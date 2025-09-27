## 1. `tool_use_behavior` – Direct Tool Output 

Your primary tool for managing workflow is the `Agent`'s `tool_use_behavior` parameter. It dictates what happens after a tool is successfully executed.

### Mode 1: `"run_llm_again"` (Default )
This is the standard behavior. After a tool runs, its output is sent **back to the LLM**. The LLM then analyzes the result and decides what to do next.

### Mode 2: `"stop_on_first_tool"`
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
* Example agr mery pass 2 tool ha or meny user input me dono tool call ka promt diya howa ha or Agent me ye use ho raha ha 
```python
  tool_use_behavior="stop_on_first_tool"
```
to sirf first tool ka output ayega direct function sy.. 
* reset_tool_choice=True (default True)



## 2. `StopAtTools` – Agr ap Specific tool ka output finaloutput banana cahaty ha..
StopAtTools ek TypedDict hai jo ek list accept karta hai: stop_at_tool_names. Yeh list un tools ke names rakhti hai jinhe agar agent call kare, to agent apna execution rok dega aur us tool ka output directly final response ke roop mein istemal karega. Matlab, agent LLM ko dobara se process nahi karega.

```python
from agents.agent import StopAtTools

@function_tool
def get_weather(city: str) -> str:
    """Returns weather info for the specified city."""
    return f"The weather in {city} is sunny"

@function_tool
def finance_query_resolver(query: str) -> str:
    """Resolves the user's finance query."""
    return f"Finance query resolved for: {query}"

agent = Agent(
    name="Assistant",
    instructions=(
        "You are a helpful assistant. "
        "If asked weather-related questions, call get_weather tool. "
        "If asked finance-related questions, call finance_query_resolver tool."
    ),
    tools=[get_weather, finance_query_resolver],
    tool_use_behavior=StopAtTools(stop_at_tool_names=["get_weather", "finance_query_resolver"])
)

result = Runner.run_sync(agent, "What's the weather in Karachi?", run_config=config)
print(result.final_output)
```
* Is configuration mein, agar user get_weather ya finance_query_resolver tool se related koi query karta hai, toh agent us tool ko call karega aur uska output directly final response ke roop mein dega.
* agr me dono tool call krwa do input dekr. to out sirf first tool ka ayega.


## 3. Making Tools Appear & Disappear (is_enabled  Default True)
```python
@function_tool(is_enabled=True)
def get_weather(city: str) -> str:
    """Returns weather info for the specified city."""
    return f"The weather in {city} is sunny"


agent = Agent(
    name="Assistant",
    instructions=(
        "You are a helpful assistant. "
        "If asked weather-related questions, call get_weather tool. "
    ),
    tools=[get_weather],
)
```
* True hone par tool hamesha Agent or LLM ke use ke liye available rahega.
* False hone par tool Agent or LLM se completely hidden ho jayega — LLM use call nahi karega.

### 3.1 is_enabled Dynamic On/Off Switch  
is_enabled me function (callable) aap context-specific logic laga ke tool ko dynamically enable ya disable kar sakte hain.

```python
from agents import Agent, Runner, function_tool, OpenAIChatCompletionsModel,RunContextWrapper
from pydantic import BaseModel


class UserData(BaseModel):
    user_role : str
    

def is_user_admin(ctx:RunContextWrapper[UserData], agent: Agent)->bool:
    return ctx.context.user_role == "admin"    
    

@function_tool(is_enabled=is_user_admin)
def delete_user_database():
    """[ADMIN ONLY] Deletes the entire user database."""
    
    return "Database has been deleted."


agent = Agent(
    name="Assistance",
    instructions="You are a helpful assistant.If user asks to delete, call the delete_user_database tool.",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash', openai_client=external_client),
    tools=[delete_user_database],
)

user_ctx = UserData(user_role='admin')
result = Runner.run_sync(starting_agent=agent, input="please delete the user data on database?", context=user_ctx)
print(result.final_output)
```

## 4. Graceful Error Handling
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

## 5. Custom Error With failure_error_function
Agar aap chahte hain ke jab aapka tool call fail ho, to ek specific error message LLM ko bheja jaye, to aap apni custom error function define kar sakte hain.

### failure_error_function kya hota hai?
failure_error_function ek optional parameter hai jo aap @function_tool decorator ke saath define kar sakte hain.
* Jab koi tool function error (jaise exception ya failure) throw karta hai, to agar aap ne failure_error_function specify kiya hai, to wo function run hoga aur uska return value LLM ko final message ke roop mein diye jaata hai.
* Agar aap failure_error_function specify nahi karte, to SDK by default default_tool_error_function use karta hai, jo ek generic error message return karta hai:
* Agar aap failure_error_function=None set karte hain, to errors re-raised hongi (tool crash karega aur fallback message nahi banega).

```python
from agents import RunContextWrapper


# Custom error handler
def custom_error_handler(ctx: RunContextWrapper[Any], error: Exception) -> str:
    return f"Oops! Something went wrong: {str(error)}"

@function_tool(failure_error_function=custom_error_handler)
def broken_tool(x: int) -> int:
    """Always raises an error."""
    return 1 / 0 

# Simple agent setup
assistant_agent = Agent(
    name="ErrorTester",
    instructions="If asked to use broken_tool, call that tool.",
    model=model,
    tools=[broken_tool],
)

result = Runner.run_sync(assistant_agent, "Use broken_tool with x=10", run_config=config)
print(result.final_output)
```

### 6. Custom Function Tool kya hai?
Custom Function Tool ek aisa tool hai jo aap directly FunctionTool class ko initialize karke create karte ho, na ke kisi Python function ko decorator ke through convert karke. Aapko apni taraf se:

* name
* description
* params_json_schema — jo arguments ka JSON schema hota hai
* on_invoke_tool — ek async function jo context aur arguments (JSON string) receive karta hai, aur return karta hai ek output string
```python
```

---

### 7. The Runner's Safety Net – max_turns
```python
result = await Runner.run(agent, "Find articles about AI agents. You can think and act a maximum of 5 times.", max_turns=6)
```
* What it is: A hard limit on the number of calls to the LLM.
* What happens when it's reached: It raises a MaxTurnsExceeded exception. Your application code must be prepared to catch this.

* Agar max_turns = 1 ho aur agent ko koi tool call karna ho (jaise search), to kya hoga?
Tool call to ho jayega, lekin uska response LLM tak wapas nahi pohanchayega, kyunke runner pehle hi stop kar dega.
* Is liye hamesha max_turns itna zyada set karo jitna workflow ke liye zaroori hai, warna agent apna kaam pura nahi kar paayega.


