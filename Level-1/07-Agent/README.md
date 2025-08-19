# Information Reguarding Agent
```bash
import os
from dotenv import load_dotenv
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel
from agents.run import RunConfig

load_dotenv()

gemini_api_key = os.getenv("GEMINI_API_KEY")

if not gemini_api_key:
    raise ValueError("GEMINI_API_KEY is not set. Please ensure it is defined in your .env file.")


external_client = AsyncOpenAI(
    api_key=gemini_api_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/",
)

model = OpenAIChatCompletionsModel(
    model="gemini-2.0-flash",
    openai_client=external_client
)

config = RunConfig(
    model=model,
    model_provider=external_client,
    tracing_disabled=True
)

agent: Agent = Agent(name="Assistant", instructions="You are a helpful assistant", model=model)

result = Runner.run_sync(agent, "Hello, how are you.", run_config=config)
print(result.final_output)
```

### Question For this Code 
#### 1. What is from dotenv import load_dotenv?
A .env file is a plain text file where you store configuration values like API keys, database URLs, or secret keys. For example:
This line is used to load environment variables from a file named .env into your Python program.The function load_dotenv() reads the .env file and loads all the variables inside it into your system environment. This allows you to access them using os.getenv().


#### 2. OpenAIChatCompletionsModel 
you can use OpenAIChatCompletionsModel to connect to third-party LLMs if.OpenAI SDK uses GPT models by default. If we want to use a third-party LLM, we can use OpenAIChatCompletionsModel to connect to it, as long as that model supports the same message format.
```bash
class OpenAIChatCompletionsModel(
    model: ChatModel | str,
    openai_client: AsyncOpenAI
)
``` 
* jab bhi hum OpenAIChatCompletionsModel ka use krty ha to humy do cheezy pass krni pharti ha base ul or api key.
lekin agr app lite llm ha use krty hato sirf api use hogi. or lite llm ka use krkr ap world ke 100 plus models access kr sakty hain.

#### 3. RunConfig
```bash
class RunConfig(
    model: str | Model | None = None,
    model_provider: ModelProvider = MultiProvider,
    model_settings: ModelSettings | None = None,
    handoff_input_filter: HandoffInputFilter | None = None,
    input_guardrails: list[InputGuardrail[Any]] | None = None,
    output_guardrails: list[OutputGuardrail[Any]] | None = None,
    tracing_disabled: bool = False,
    trace_include_sensitive_data: bool = True,
    workflow_name: str = "Agent workflow",
    trace_id: str | None = None,
    group_id: str | None = None,
    trace_metadata: dict[str, Any] | None = None
)
```

#### 4. AsyncOpenAI
AsyncOpenAI is a Python class from the OpenAI library that enables asynchronous API calls to OpenAI's services
```bash
class AsyncOpenAI(
    *,
    api_key: str | None = None,
    organization: str | None = None,
    project: str | None = None,
    webhook_secret: str | None = None,
    base_url: str | URL | None = None,
    websocket_base_url: str | URL | None = None,
    timeout: float | Timeout | NotGiven | None = NOT_GIVEN,
    max_retries: int = DEFAULT_MAX_RETRIES,
    default_headers: Mapping[str, str] | None = None,
    default_query: Mapping[str, object] | None = None,
    http_client: AsyncClient | None = None,
    _strict_response_validation: bool = False
)
```

#### 5. Agent
he Agent class creates an AI agent with specific behavior and capabilities, as defined by its parameters.
agent name: str pereamter required or all perameter optional
```bash
class Agent(
    name: str,
    instructions: str | ((RunContextWrapper[Any], Agent[Any]) -> MaybeAwaitable[str]) | None = None,
    prompt: Prompt | DynamicPromptFunction | None = None,
    handoff_description: str | None = None,
    handoffs: list[Agent[Any] | Handoff[Any]] = list,
    model: str | Model | None = None,
    model_settings: ModelSettings = ModelSettings,
    tools: list[Tool] = list,
    mcp_servers: list[MCPServer] = list,
    mcp_config: MCPConfig = lambda : MCPConfig(),
    input_guardrails: list[InputGuardrail[Any]] = list,
    output_guardrails: list[OutputGuardrail[Any]] = list,
    output_type: type[Any] | AgentOutputSchemaBase | None = None,
    hooks: AgentHooks[Any] | None = None,
    tool_use_behavior: StopAtTools | ToolsToFinalOutputFunction[Any] | Literal['run_llm_again', 'stop_on_first_tool'] = "run_llm_again",
    reset_tool_choice: bool = True
)
```

#### 6. Agent Basic configuration
* name: A required string that identifies your agent.
* instructions: also known as a developer message or system prompt.
* model: which LLM to use, and optional model_settings to configure model tuning parameters like temperature, top_p, etc.
* tools: Tools that the agent can use to achieve its tasks.


#### 7. Runner
Runner class ek utility ya controller class hai jo AI agents ke execution ko handle karta hai. Yeh agents (jaise aapka Agent class) aur unke associated models (jaise OpenAIChatCompletionsModel) ke saath kaam karta hai, taki user prompts ko process karke responses generate kiye ja sakein. Aapke code mein, Runner.run_sync(agent, "Hello, how are you.", run_config=config) ka use dikhta hai, jo indicate karta hai ke Runner ek interface provide karta hai jo synchronous ya asynchronous tarike se agent ke operations ko execute karta hai.

dir(Runner)
```bash
['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getstate__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'run', 'run_streamed', 'run_sync']
```

##### 1. runner.run(prompt)
* Async Requirement: Runner.run ko await karna zaroori hai kyunki yeh async method hai. Iske liye code ko asyncio.run ya event loop mein chalana padta hai.Run ko async function me use krty hain or sath await ka use bhi krty hain.asyncio ki library async function ko run 
krny ke liye use hoti hain.

* Purpose: Query bhejna aur complete response aik baar mein lena.
* Nature: Asynchronous (await karna parta hai).
* Use-case: Jab aapko full result aik hi baar mein chahiye ho.

```bash
agent = Agent(name="Assistant", instructions="You are a helpful assistant", model=model)

async def main():
    result = await Runner.Run(agent, "Hello, how are you.", run_config=config)
    print(result.final_output)
      print(result.last_agent)
    
asyncio.run(main())  
```
* result.last_agent ye humy Agent ki Class return krygi is tarha
```bash
Agent(name='Assistant', instructions='You are a helpful assistant.', prompt=None, handoff_description=None, handoffs=[], model=<agents.models.openai_chatcompletions.OpenAIChatCompletionsModel object at 0x0000028F049E5C90>, model_settings=ModelSettings(temperature=None, top_p=None, frequency_penalty=None, presence_penalty=None, tool_choice=None, parallel_tool_calls=None, truncation=None, max_tokens=None, reasoning=None, metadata=None, store=None, include_usage=None, response_include=None, extra_query=None, extra_body=None, extra_headers=None, extra_args=None), tools=[FunctionTool(name='english_poetry_writer_tool', description='Writes English poetry on the given topic.', params_json_schema={'properties': {'input': {'title': 'Input', 'type': 'string'}}, 'required': ['input'], 'title': 'english_poetry_writer_tool_args', 'type': 'object', 'additionalProperties': False}, on_invoke_tool=<function function_tool.<locals>._create_function_tool.<locals>._on_invoke_tool at 0x0000028F09A08860>, strict_json_schema=True, is_enabled=True)], mcp_servers=[], mcp_config={}, input_guardrails=[], output_guardrails=[], output_type=None, hooks=None, tool_use_behavior='run_llm_again', reset_tool_choice=True)
```

##### 2. runner.run_sync(prompt)

* Purpose: Same as run(), but sync code ke liye.
* Nature: Synchronous (without async/await).
* Use-case: Jab aap ka code async nahi hai (like simple scripts or CLI).

```bash
result =  Runner.run_sync(agent, "Write kids Poetry funy?", run_config=config)
print(result.final_output)
print(result.last_agent)
```
* run_sync ka fucntion async function me work nh kryga qk ye Synchronous work krta hain. normal python me under run_sync chal jayega 
lekin async function me nh chlyga..

##### 3.  runner.stream(prompt)
* Purpose: Prompt bhejna aur real-time streaming mein response lena.
* Nature: Asynchronous stream (token/token ya chunk/chunk mein response aata hai). 
* Use-case: Chat apps, terminals, jahan user ko live output chahiye hota hai.


##### runner.run_sync vs runner.run
1. runner.run() ek asynchronous function ko run karta hai runner ke context ke andar. Isse await ke saath call kiya jata hai, aur yeh async code ke liye hota hai.
2. Same as run(), but sync code ke liye. Nature: Synchronous (without async/await).

##### Key points
* await ko humesha async funciton ke under use kia jata hain
* async function ko call krwany ke liye await lagana pharta hain.
* async.io ki library async function ko run krny ke liye use hoti hain.

##### idf you print result
* print(result)
```bash
- Last agent: Agent(name="Assistant", ...)
- Final output (str):
- Last agent: Agent(name="Assistant", ...)
- Final output (str):
- Final output (str):
    I am doing well, thank you for asking! How can I help you today?
    I am doing well, thank you for asking! How can I help you today?
- 1 new item(s)
- 1 raw response(s)
- 0 input guardrail result(s)
- 0 output guardrail result(s)
(See `RunResult` for more details)
```

### How to configure LLM Providers at different levels (Global, Run and Agent)?
#### 8 Agents SDK is setup to use OpenAI as default providers. When using other providers you can setup at different levels:
1. Agent Level
2. RUN LEVEL
3. Global Level


##### 1. Agent Level
You assign a specific model or model provider directly to the agent.
```bash
agent = Agent(
        name="Assistant",
        instructions="You only respond in haikus.",
        model=OpenAIChatCompletionsModel(model="gemini-2.0-flash", openai_client=client),
    )
```


##### 2. Run Level Configuration
You provide the model or model provider during the specific run execution, using RunConfig.
```bash
config = RunConfig(
    model=my_custom_model,
    model_provider=my_custom_client
)

Runner.run_sync(agent, "Hello", run_config=config)
```

##### 3. Global Level Configuration
You set a default model/provider globally, which is used by all agents and runs unless overridden.
```bash
from agents import Agent, Runner, AsyncOpenAI, set_default_openai_client, set_tracing_disabled, set_default_openai_api

gemini_api_key = ""
set_tracing_disabled(True)
set_default_openai_api("chat_completions")

external_client = AsyncOpenAI(
    api_key=gemini_api_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/",
)
set_default_openai_client(external_client)

agent: Agent = Agent(name="Assistant", instructions="You are a helpful assistant", model="gemini-2.0-flash")

result = Runner.run_sync(agent, "Hello")

print(result.final_output)
```


##### Context
Agents are generic on their context type. Context is a dependency-injection tool: it's an object you create and pass to Runner.run(), that is passed to every agent, tool, handoff etc, and it serves as a grab bag of dependencies and state for the agent run. You can provide any Python object as the context.
```bash
@dataclass
class UserContext:
    name: str
    uid: str
    is_pro_user: bool

    async def fetch_purchases() -> list[Purchase]:
        return ...

agent = Agent[UserContext](
    ...,
)
```

##### Output types
By default, agents produce plain text (i.e. str) outputs. If you want the agent to produce a particular type of output, you can use the output_type parameter. A common choice is to use Pydantic objects, but we support any type that can be wrapped in a Pydantic TypeAdapter - dataclasses, lists, TypedDict, etc.
```bash
from pydantic import BaseModel
from agents import Agent


class CalendarEvent(BaseModel):
    name: str
    date: str
    participants: list[str]

agent = Agent(
    name="Calendar extractor",
    instructions="Extract calendar events from text",
    output_type=CalendarEvent,
)
```
