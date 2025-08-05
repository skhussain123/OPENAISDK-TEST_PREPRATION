
### Tools
Tools let agents take actions: things like fetching data, running code, calling external APIs, and even using a computer. There are three classes of tools in the Agent SDK:

* Hosted tools: these run on LLM servers alongside the AI models. OpenAI offers retrieval, web search and computer use as hosted tools.
* Function calling: these allow you to use any Python function as a tool.
* Agents as tools: this allows you to use an agent as a tool, allowing Agents to call other agents without handing off to them.


### Hosted tools
1. The WebSearchTool lets an agent search the web.
2. The FileSearchTool allows retrieving information from your OpenAI Vector Stores.
3. The ComputerTool allows automating computer use tasks.
4. The CodeInterpreterTool lets the LLM execute code in a sandboxed environment.
5. The HostedMCPTool exposes a remote MCP server's tools to the model.
6. The ImageGenerationTool generates images from a prompt.
7. The LocalShellTool runs shell commands on your machine.


### Tools Class
```bash
(variable) tools: list[FunctionTool | FileSearchTool | WebSearchTool | ComputerTool | HostedMCPTool | LocalShellTool | ImageGenerationTool | CodeInterpreterTool]
```

### Function tools / Function calling
You can use any Python function as a tool. The Agents SDK will setup the tool automatically:

* The name of the tool will be the name of the Python function (or you can provide a name)
* Tool description will be taken from the docstring of the function (or you can provide a description)
* The schema for the function inputs is automatically created from the function's arguments
* Descriptions for each input are taken from the docstring of the function, unless disabled

```bash
@function_tool
def javascript(topic: str) -> str:
    "Explains a JavaScript topic in simple terms."
    return f"You asked about JavaScript topic: {topic}. Here's a basic explanation..."


agent = Agent(
    name="You are helpful assistant",
    instructions=("You are a helpful assistant for programming."),
    model=model,
    tools=[javascript],
)
```

* agr me tool me doc string nh dunga to tool me jab bhi proper work kryga.

#### async Tool
```bash
@function_tool
async def get_weather(city: str) -> str:
    return f"The weather in {city} is sunny."
```   

##### @function_tool Class
```bash
(function)
def function_tool(
    func: ToolFunction[...],
    *,
    name_override: str | None = None,
    description_override: str | None = None,
    docstring_style: DocstringStyle | None = None,
    use_docstring_info: bool = True,
    failure_error_function: ToolErrorFunction | None = None,
    strict_mode: bool = True,
    is_enabled: bool | ((RunContextWrapper[Any], Agent[Any]) -> MaybeAwaitable[bool]) = True
) -> FunctionTool: ...

def function_tool(
    *,
    name_override: str | None = None,
    description_override: str | None = None,
    docstring_style: DocstringStyle | None = None,
    use_docstring_info: bool = True,
    failure_error_function: ToolErrorFunction | None = None,
    strict_mode: bool = True,
    is_enabled: bool | ((RunContextWrapper[Any], Agent[Any]) -> MaybeAwaitable[bool]) = True
) -> ((ToolFunction[...]) -> FunctionTool): ...
```

## Agent as a Tool
```bash

# Define a support agent
poetry_agent = Agent(
    name="Poetry Writer Agent",
    instructions="Write a 3-stanza English poem on the given topic.",
    model=model
)

# Convert agents into tools
poetry_tool = poetry_agent.as_tool(
    tool_name="english_poetry_writer_tool",
    tool_description="Writes English poetry on the given topic."
)

triage_agent = Agent(
    name="Triage Agent",
    instructions="""
You are a smart assistant.
1. If the user asks for a poem or poetry, use 'english_poetry_writer_tool'.
2. Otherwise, use 'english_essay_writer_tool'.
Never write content yourself. Always call the right tool.
""",
    tools=[poetry_tool],
    model=model
)
```

### as_tools() Class
```bash
(method) def as_tool(
    tool_name: str | None,
    tool_description: str | None,
    custom_output_extractor: ((RunResult) -> Awaitable[str]) | None = None
) -> Tool
```

#### Complete Code Example Agent As a Tool
```bash
from agents import Agent, Runner

# Define individual agents
shopping_agent = Agent(
    name="Shopping Assistant",
    instructions="You assist users in finding products and making purchase decisions."
)

support_agent = Agent(
    name="Support Agent",
    instructions="You help users with post-purchase support and returns."
)

# Convert agents into tools
shopping_tool = shopping_agent.as_tool()
support_tool = support_agent.as_tool()

# Define a triage agent that delegates tasks
triage_agent = Agent(
    name="Triage Agent",
    instructions="You route user queries to the appropriate department.",
    tools=[shopping_tool, support_tool]
)

# Run the triage agent with a sample input
result = Runner.run_sync(triage_agent, "I need help with a recent purchase.")
print(result.final_output)
```

#### Customizing tool-agents
```bash
from agents import Agent, Runner, function_tool

@function_tool
async def run_my_agent(input: str) -> str:
    """Runs a sub-agent with custom config and input."""

    agent = Agent(
        name="My Agent",
        instructions="You help users by translating text to French."
    )

    result = await Runner.run(
        agent,
        input=input,
        max_turns=5 # max_turns = 5 ka matlab hai ke agent sirf 5 dafa LLM call karega ya tools use karega jab tak final output produce ho.
    )

    return str(result.final_output)
```

```bash
triage_agent = Agent(
    name="Assistance",
     instructions=("You are helpfull Assistance"),
    model=model,
    tools=[add],
    tool_use_behavior="stop_on_first_tool"
)
```
* Agent me eik argument tool_use_behavior ka hota ha or ismy two perameter hoty ha  run_llm_again, or stop_on_first_tool  defauly run_llm_again set hoga ha

1. tool_use_behavior="stop_on_first_tool" ka matlab kya hai?
Ye setting Agent ko ye batata hai ke jab koi tool (function) use kiya jaye, to uske baad LLM (language model) ko dobara run na karna — yani usi waqt ruk jana.

2. (run_llm_again):
Tool run karne ke baad agent LLM ko dobara run karta hai, takay output ko explain kare ya aage steps kare.

| Behavior                  | Kya hota hai                        | Example Output                       |
| ------------------------- | ----------------------------------- | ------------------------------------ |
| `stop_on_first_tool`      | Tool chalate hi agent ruk jata hai  | `8`                                  |
| default (`run_llm_again`) | Tool ke baad LLM phir se chalta hai | `The result of adding 5 and 3 is 8.` |


```bash
from agents.agent import StopAtTools

@function_tool
def add(a: int, b: int):
    """Add two numbers"""
    return a + b


@function_tool
def human_review():
    """human in the loop inetrface"""
    return "human review Tool Calling"


# Orchestrator agent
triage_agent = Agent(
    name="Assistance",
     instructions=("You are helpfull Assistance"),
    model=model,
    tools=[add,human_review],
    tool_use_behavior=StopAtTools(stop_at_tool_names=["human_review"])
)

result = Runner.run_sync(triage_agent, "What is 2 plus 2. after result ask human to review", run_config=config)
print(result.final_output)
```
##### StopAtTools(stop_at_tool_names=["human_review"]) Kya Karta Hai?

Agent 4 to calculate karega, magar kyunki human_review() last mein call hua, aur StopAtTools ne bola ke us tool ke baad rukna hai — to final_output wahi hoga jo human_review() return karega.
Jab Agent human_review tool ko call kare, to uske baad LLM ko dobara run NAHI karna, agent wahi ruk jaye.

**Yani agar model ne decide kiya ke human_review() tool chalana hai, to:**
1. Woh tool run karega.
2. Uske baad model ko dobara run nahi karega.
3. Final output wahi hoga jo tool ne return kiya.

**Agar tum human_review tool call karo, to uske baad kuch aur mat karna. Bas us tool ka result return kar dena aur ruk jana**

1. Message mein pehle add(2, 2) karega → result 4.
2. Phir dekhega ke user ne bola hai "ask human to review" → to human_review() call karega.
3. Aur human_review() ke baad agent ruk jayega, LLM dobara nahi chalega.

| Behavior                                           | Rukne ka rule                  | Example: add(2,2)    | Example: human\_review() |
| -------------------------------------------------- | ------------------------------ | -------------------- | ------------------------ |
| `"stop_on_first_tool"`                             | Pehla tool chale to hi ruk jao | ✅ Ruk jaata hai      | ✅ Ruk jaata hai          |
| `StopAtTools(stop_at_tool_names=["human_review"])` | Sirf listed tool pe rukna      | ❌ Continue karta hai | ✅ Ruk jaata hai          |

#### Model Settings
**ModelSettings Perameter**
```bash
class ModelSettings(
    temperature: float | None = None,
    top_p: float | None = None,
    frequency_penalty: float | None = None,
    presence_penalty: float | None = None,
    tool_choice: str | None = None,
    parallel_tool_calls: bool | None = None,
    truncation: Literal['auto', 'disabled'] | None = None,
    max_tokens: int | None = None,
    reasoning: Reasoning | None = None,
    metadata: dict[str, str] | None = None,
    store: bool | None = None,
    include_usage: bool | None = None,
    response_include: list[ResponseIncludable] | None = None,
    extra_query: Query | None = None,
    extra_body: Body | None = None,
    extra_headers: Headers | None = None,
    extra_args: dict[str, Any] | None = None
)
```
```bash
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel, function_tool,ModelSettings

triage_agent = Agent(
    name="Assistance",
     instructions=("You are helpfull Assistance"),
    model=model,
    tools=[add,human_review],
    model_settings = ModelSettings(tool_choice="required"),
    reset_tool_choice=False # ye by default True hota. 
)
```
**model_settings = ModelSettings(tool_choice=("auto"))**
* LLM automatic tool call nahi karega.
* Lekin agar explicitly aap ne agent ya runner ko kaha ke tool call karo → to phir chalega.

**model_settings = ModelSettings(tool_choice=("none"))**
* Tool Call nhi hoga.Llm jawab dega.

**tool_choice="required" ka matlab:**
Model ko tool use karna hi padega.
Agar prompt ka response banana hai, to model function/tool call ke through hi kare, direct text reply allowed nahi.
* Model sirf tool ke zariye response dega.
* Agar tool call ka koi reason nahi milta, to error bhi aa sakta hai.

**reset_tool_choice=False ka matlab:**
Ek dafa koi tool select ho gaya, to wahi bar bar use hota rahega, jab tak explicitly change na ho.10 time chal kr last me error aeyga

```bash
result = Runner.run_sync(triage_agent, "What is 2 plus 2. after result ask human to review", run_config=config,max_turns=1)
```
* max_turns 1 sy eik bar loop agent loop chalyga

#### strict_mode=True
* strict_mode=True matlab ke aap sakhti kar rahe ho ke tool sirf wahi parameters le jo function define karta hai.
* Agar model se kuch galt, kama, ya ziyadah mile — toh aapka application vo tool use hone se pehle hi rok deta hai.
* Ye aapka tool zyada mazboot aur safe banata hai.

#### strict_mode=False
* strict_mode=False → “maryaada mein soft rehna”
* Optional parameters ka hona imaandaari se maangna bhi nahi zaroori hota.
* Agar model koi “bekarar” ya extra cheez pass kar deta hai (undefined field), phir bhi error nahi deta.
* Ye setup zara flexible hai, lekin sawaal ka jawab less predictable ho sakta hai compare to strict mode.


### Custom function tools
Sometimes, you don't want to use a Python function as a tool. You can directly create a FunctionTool if you prefer. You'll need to provide:
* name
* description
* params_json_schema, which is the JSON schema for the arguments
* on_invoke_tool, which is an async function that receives a ToolContext and the arguments as a JSON string, and must return the tool output as a string.


#### 1. Handoff vs As Tool
The key difference here revolves around what context is passed to the new agent and how control of the conversation flows between agents. Let’s break down each point:

* Handoffs:
When an agent uses a handoff, the new (receiving) agent is given the entire conversation history. This means that it gets every message—user input, previous responses, tool calls, and any context that has been built up so far. This comprehensive context allows the new agent to fully understand the background, nuances, and prior decisions of the conversation. It’s as if the conversation “moves” entirely over to the new agent, which can then generate responses based on all of the earlier dialogue.

* Tool-based Calls (using as_tool):
In contrast, when an agent is invoked as a tool (using the as_tool method), it does not receive the whole conversation history. Instead, it gets a piece of generated input from the original agent—often a specific string or a data payload that was produced during the conversation. The new agent (now acting as a tool) only processes this discrete input. This design is useful when the new agent’s functionality is meant to handle a specific task or computation without needing the full background, thereby keeping the interface simpler and more focused.

#### 2. . Flow of Conversation Control
* Handoffs:
In a handoff, the new agent “takes over” the conversation. Because it receives the full history, it continues the interaction as if it were the main agent, making decisions, asking follow-up questions, or generating responses based solely on the transferred dialogue. Essentially, the conversational control is completely passed to the new agent, which now becomes responsible for driving the dialogue forward.

* Tool-based Calls (using as_tool):
When an agent is used as a tool, it is invoked by the original agent to perform a specific function (for example, processing data or executing a sub-task). After the tool (the new agent) completes its job and returns its output, the original agent resumes the conversation. The original agent integrates the tool’s result into the ongoing dialogue, which means it maintains overall control of the conversation flow. This approach allows for modularity—different agents can be “plugged in” to perform functions without completely transferring the conversational context or control.


#### 3. Why This Distinction Matters
* Modularity and Reusability:
Using the tool method (via as_tool) is ideal for building systems where you want to keep the conversation centralized. The original agent can call upon various specialized sub-agents (tools) for tasks like calculations, look-ups, or processing requests, then stitch their outputs back into a coherent conversation. This leads to a highly modular design where each agent can be developed and maintained independently while still contributing to a unified interaction.

* Context-Rich Delegation:
Handoffs, on the other hand, are best suited for scenarios where the new agent must have a complete understanding of the conversation to address complex or nuanced issues. This might be important in customer support or when the conversation’s history carries essential details that affect subsequent responses.


#### An Analogy
Imagine you’re at a restaurant:

* Handoff: If you ask the host to call the chef over because your dish needs a complete rework, the chef comes over with full knowledge of everything that’s happened (the conversation history, complaints, previous interactions) and takes over your service.
* Tool Call: Instead, if you ask the waiter to bring a side dish, the waiter simply takes your specific request (the generated input) and returns with the dish. You, as the diner, still engage directly with the waiter, who integrates that dish into your meal.
