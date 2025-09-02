## `tool_use_behavior` – The Agent's Control Knob

Your primary tool for managing workflow is the `Agent`'s `tool_use_behavior` parameter. It dictates what happens after a tool is successfully executed.

### Mode 1: `"run_llm_again"` (The Default Thinker)
This is the standard behavior. After a tool runs, its output is sent **back to the LLM**. The LLM then analyzes the result and decides what to do next.

### Mode 2: `"stop_on_first_tool"` (The Direct Responder)
This mode stops execution immediately after the **first tool call**. The raw output of that tool becomes the agent's final answer. The LLM does *not* see the tool's result.

```bash
@function_tool()
def weather_tool(input:str)-> str:
    return f"{input} weather is sunny"


agent = Agent(
    name="Assistance",
    instructions="you are a helpfull assistance if you asked the weather related question youo want to call weather_tool",    
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    tools=[weather_tool],
    tool_use_behavior="stop_on_first_tool"
)
```
* run_llm_again → Tool call ke baad, agent phir se LLM ko bulaata hai taake tool output ko process karke final response de.
* stop_on_first_tool → Pehli tool call hi final response hogi; LLM passive ho jata hai, tool ka result directly user ko return hota hai.
















<!-- # Advanced Tools MasterClass

Welcome to the next level of tool calling. If basic tools are about giving your agent *abilities*, advanced tools are about giving you *control*. This guide will teach you how to manage your agent's workflow, handle errors gracefully, and build robust, real-world applications.

> **The Big Idea:** You are a manager, and your tools are your team. Advanced features are your management playbook for telling them *when* to work, *if* they can work, and *what to do* when they run into trouble.

### What We'll Master in This Step

To give you a roadmap, here are the key questions we will answer. By the end of this guide, you'll be able to confidently control your agent's behavior in complex, real-world scenarios:

*   **Controlling Execution Flow:** How can I use `tool_use_behavior` to stop my agent after its first action (`"stop_on_first_tool"`), or only after a specific "finalizing" tool (`StopAtTools`)?
*   **Preventing Runaway Agents:** What is the `max_turns` safety net, how does it limit LLM calls, and how does it raise an exception when reached?
*   **Creating Context-Aware Tools:** How do I make tools available *only* under specific conditions, like creating an "admin-only" tool using the dynamic `is_enabled` flag?
*   **Building Resilient Agents:** How can my agent handle tool failures gracefully with `try/except` so it can recover instead of crashing?
*   **Managing Stateful Tools:** For rare cases where a tool needs to remember information, how do we build one using the `FunctionTool` class, and why is this pattern used sparingly?
*   **Applying Production Patterns:** How do these features map to real-world architectures like API Gateways, Data Pipelines, and Interactive Assistants?

## 🤔 Why Do We Need an Advanced Tools MasterClass?

Without advanced controls, agents can get stuck in loops, crash on a simple error, or try to use tools they shouldn't have access to. This costs time and money. Advanced tools solve these critical problems:
*   **Control:** Stop your agent from running forever or calling tools unnecessarily.
*   **Context:** Enable or disable tools based on the user's permissions or the situation.
*   **Resilience:** Handle failures without crashing the entire process.
*   **Precision:** Build sophisticated, multi-step workflows that execute predictably.

---



### Mode 3: `StopAtTools` (The Workflow Finisher)
This mode gives you surgical control. You provide a list of "finalizing" tool names. The agent will run its workflow but stop immediately after one of those specific tools is called.

```python
@function_tool()
def addition_tool(a:int, b:int):
    return a + b

@function_tool()
def subtraction_tool(a:int, b:int):
    return a - b

agent = Agent(
    name="Assistance",
    instructions="you are a helpfull assistance if you asked the add related question you want to call addition_tool and subtraction related question you want to call subtraction_tool",    
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    tools=[addition_tool, subtraction_tool],
    tool_use_behavior=StopAtTools(stop_at_tool_names=["addition_tool"])
)
```
* jab addition_tool tool call hoga to tool output llm ke pass nh jaeyga. direct answer ayega tool ka.
* jab subtraction_tool tool call hoga to tool output llm ke pass jaeyga or llm sy process hokr aega.


---

## Part 2: The Runner's Safety Net – `max_turns`

The `Runner.run` `max_turns` parameter is your ultimate safety net against infinite loops.

*   **Use Case:** A complex research task where you want to allow up to 5 web searches before stopping, no matter what.

```python
result = await Runner.run(agent, "Find articles about AI agents. You can think and act a maximum of 5 times.", max_turns=6)
```

*   **What it is:** A hard limit on the number of **calls to the LLM**.
*   **What happens when it's reached:** It **raises a `MaxTurnsExceeded` exception**. Your application code must be prepared to catch this.

> **🧠 Think About It:** What happens if `max_turns` is 1 and the agent needs to call a tool (search)? The runner will stop it after the first tool call, before taking tool response to llm. Always set `max_turns` high enough for the expected workflow.

---

## Part 3: Context is King – Making Tools Appear & Disappear

A good manager doesn't give every tool to every team member. The `is_enabled` flag on a `@function_tool` lets you make tools available only when conditions are right.

### The Static On/Off Switch

The simplest way is with a `True`/`False` value. This is great for turning off a tool for maintenance.

```python
@function_tool(is_enabled=False)
def addition_tool(a:int, b:int):
    return a + b
```
* True hone par tool hamesha LLM ke use ke liye available rahega.
* False hone par tool LLM se completely hidden ho jayega — LLM use call nahi karega.


### The Dynamic On/Off Switch (with a function)
is_enabled me function (callable) aap context-specific logic laga ke tool ko dynamically enable ya disable kar sakte hain.

*  **Use Case:** An "admin" tool that should only be visible to users with admin privileges.

```python
import os
from pydantic import BaseModel

from agents import (
    Agent,
    Runner,
    OpenAIChatCompletionsModel,
    AsyncOpenAI,
    function_tool,
    RunContextWrapper,
)
from dotenv import load_dotenv

load_dotenv()

gemini_key = os.getenv("GEMINI_API_KEY")
if not gemini_key:
    raise ValueError("API KEY is NOT Loaded")

external_client = AsyncOpenAI(
    api_key=gemini_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

class UserContext(BaseModel):
    user_role: str

def is_user_admin(wrapper: RunContextWrapper[UserContext], agent) -> bool:
    return wrapper.context.user_role == "admin"

@function_tool(is_enabled=is_user_admin)
def delete_user_database():
    """[ADMIN ONLY] Deletes the entire user database."""
    
    return "Database has been deleted."

agent = Agent[UserContext](
    name="Assistance",
    instructions="You are a helpful assistant.If user asks to delete, call the delete_user_database tool.",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash', openai_client=external_client),
    tools=[delete_user_database],
)

user_ctx = UserContext(user_role="admin")
result = Runner.run_sync(starting_agent=agent, input="please delete the user data on database?", context=user_ctx)

print(result.final_output)
```

---

## Part 4: When Things Go Wrong – Graceful Error Handling

Tools can fail. A resilient agent doesn't crash; it handles the error, and a simple `try/except` block is usually the best way.

```python
@function_tool
def divide(a: int, b: int) -> str:
    """Divides two numbers."""
    try:
        result = a / b
        return str(result)
    except ZeroDivisionError:
        return "Error: You cannot divide by zero. Please ask for a different number."
```

### The Advanced Way: Custom Error Functions

For more complex scenarios, like custom logging or routing, you can provide a `failure_error_function`. This is less common but offers maximum control.

#### failure_error_function kya hota hai?

failure_error_function ek optional parameter hai jo aap @function_tool decorator ke saath define kar sakte hain.

* Jab koi tool function error (jaise exception ya failure) throw karta hai, to agar aap ne failure_error_function specify kiya hai, to wo function run hoga aur uska return value LLM ko final message ke roop mein diye jaata hai.
* Agar aap failure_error_function specify nahi karte, to SDK by default default_tool_error_function use karta hai, jo ek generic error message return karta hai:
* Agar aap failure_error_function=None set karte hain, to errors re-raised hongi (tool crash karega aur fallback message nahi banega).

---

## Part 5: The Specialist – Stateful Tools (Use with Caution)

While `@function_tool` is best for 99% of cases, you can build a tool from the `FunctionTool` class to manage internal state (memory between calls).

> **⚠️ Recommendation:** This pattern is complex and can make agent behavior harder to predict. Always prefer a simple `@function_tool` if possible.

```python
from agents import FunctionTool

class CounterTool(FunctionTool):
    def __init__(self):
        self._count = 0
        super().__init__(
            name="incrementing_counter",
            description="Counts up by one each time it is called.",
            params_json_schema={"type": "object", "properties": {}},
            on_invoke_tool=self.on_invoke_tool
        )

    async def on_invoke_tool(self, context, args_json_str) -> str:
        self._count += 1
        return f"The current count is: {self._count}"


agent_tools = [CounterTool()]

print(agent_tools)
```
---
#### Expected Output :

```python
[CounterTool(name='incrementing_counter', description='Counts up by one each time it is called.', params_json_schema={'type': 'object', 'properties': {}, 'additionalProperties': False, 'required': []}, on_invoke_tool=<bound method CounterTool.on_invoke_tool of ...>, strict_json_schema=True, is_enabled=True)]
```
---

## Part 6: Production Patterns

These features map directly to common, real-world agent architectures:

*   **🌐 The API Gateway:** Fast, direct, single-action. Use `tool_use_behavior="stop_on_first_tool"`.
*   **🔄 The Data Pipeline:** A sequence with a clear end. Use `tool_use_behavior=StopAtTools(...)`.
*   **💬 The Interactive Assistant:** Needs to think about results. Use the default `tool_use_behavior="run_llm_again"`.
---

## Your Turn: A Mini-Lab

Let's build an agent that uses these advanced controls.

```python
from agents import (
    Agent,
    OpenAIChatCompletionsModel,
    Runner,
    function_tool,
    StopAtTools,
    AsyncOpenAI,
    set_tracing_disabled,
)
from dotenv import find_dotenv, load_dotenv
import asyncio
import os

_ = load_dotenv(find_dotenv())

gemini_api_key = os.getenv("GEMINI_API_KEY")

# Reference: https://ai.google.dev/gemini-api/docs/openai
client = AsyncOpenAI(
    api_key=gemini_api_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/",
)

set_tracing_disabled(disabled=True)


@function_tool
def get_user_data(user_id: str) -> str:
    """Looks up user data."""
    return f"Data for {user_id}: Name - Alex, Role - user"


# TODO 1: Make this an admin-only tool using `is_enabled`.
@function_tool
def delete_user(user_id: str) -> str:
    """Deletes a user. This is a final action."""
    return f"User {user_id} has been deleted."


admin_agent = Agent(
    name="Admin Agent",
    instructions="Help manage users. First get data, then delete if asked.",
    tools=[get_user_data, delete_user],
    model=OpenAIChatCompletionsModel(model="gemini-2.0-flash", openai_client=client),
    # TODO 2: Make the agent stop immediately after a user is deleted
    # using `tool_use_behavior` and `StopAtTools`.
    tool_use_behavior=StopAtTools(stop_at_tool_names=["delete_user"]),
)


async def main():
    print("--- Running as a regular user ---")
    result_user = await Runner.run(
        admin_agent, "Please delete user client_456.", context={"role": "user"}
    )
    print(f"Final Output: {result_user.final_output}")

    print("\n--- Running as an admin ---")
    # TODO 3: Set max_turns to 3 for this run as a safety limit.
    result_admin = await Runner.run(
        admin_agent,
        "Get data for user_123 and then delete them.",
        context={"role": "admin"},
        max_turns=3,
    )
    print(f"Final Output: {result_admin.final_output}")


asyncio.run(main())
```

#### ✅ Expected Outcome
```
--- Running as a regular user ---
Final Output: User client_456 has been deleted.

--- Running as an admin ---
Final Output: User user_123 has been deleted.
---
```

## 🏁 Wrap-Up

*   **What it is:** A set of precise controls for managing how and when your agent uses tools.
*   **Key Controls:** Use `tool_use_behavior` to manage the workflow, `Runner.max_turns` as a safety limit, and `is_enabled` for context-aware tools.
*   **Best Practices:** Handle errors inside your tools with `try/except` and match the agent's configuration to its real-world pattern (Gateway, Pipeline, or Assistant).

- https://openai.github.io/openai-agents-python/tools/
- https://github.com/openai/openai-agents-python/tree/main/examples/tools
- https://github.com/mjunaidca/agents-sdk-decoded/blob/main/01_agent/09_tool_behavior.py -->
