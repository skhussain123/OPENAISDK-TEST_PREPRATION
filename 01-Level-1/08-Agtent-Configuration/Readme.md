
# Model Configuration
Agents SDK is setup to use OpenAI as default providers. When using other providers you can setup at different levels:

1. Agent Level
2. RUN LEVEL
3. Global Level

## 1. AGENT LEVEL
* Har Agent instance apni khud ki configuration specify kar sakta hai—jaise model, model_settings, tools, instructions, aur even custom ModelProvider.
* Yeh flexibility deta hai ke different agents use different models or providers in the same application/workflow.
* Use case: Jab ek workflow mein multiple agents ho, aur aap chahte ho ke har agent ek specific model ya provider use kare (e.g., Spanish agent uses GPT-3.5, English agent uses Gemini, etc.).

```python
import os
from agents import Agent, Runner, OpenAIChatCompletionsModel, set_tracing_disabled
from openai import AsyncOpenAI
from dotenv import load_dotenv

# Load environment variables from a .env file
load_dotenv()
gemini_api_key = os.getenv('GEMINI_API_KEY')

# Check if the API key is loaded; raise an error if not
if not gemini_api_key:
    raise ValueError("Api Key Not lodded")

# Initialize an AsyncOpenAI client with the Gemini API key and custom base URL
external_client = AsyncOpenAI(
    api_key=gemini_api_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/",  
)

# Disable tracing (likely for debugging or logging purposes)
set_tracing_disabled(True)

# Create an Agent instance with a name, instructions, and model configuration
agent: Agent = Agent(
    name="Assistant", 
    instructions="You are a helpful assistant",
    model=OpenAIChatCompletionsModel(model="gemini-2.0-flash", openai_client=external_client),
)

# Run the agent synchronously with the input "write a blog"
result = Runner.run_sync(starting_agent=agent, input="write a blog")
print(result.final_output)
```

## 2. Run LEVEL
* Runner (ya Runner.run) configuration ke through aap ek specific run ke liye model provider, model settings, tracing options etc. override kar sakte hain.
* Isme aap RunConfig object pass karte ho, jisme settings jaise model choice, modelProvider, modelSettings, tracing flags, guardrails, context, etc. set ho sakte hain.
* Use case: Jab ek specific execution ke liye different setup chahiye ho (e.g., test run, high-temperature model, tracing disabled, etc.).


```python
import os
from agents import Agent, Runner, OpenAIChatCompletionsModel,AsyncOpenAI
from agents.run import RunConfig
from dotenv import load_dotenv

load_dotenv()

gemini_key = os.getenv('GEMINI_API_KEY')

if not gemini_key:
    raise ValueError("API KEY is NOT Laoded")

external_client = AsyncOpenAI(
    api_key=gemini_key,
     base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

model = OpenAIChatCompletionsModel(
    model='gemini-2.0-pro',
    openai_client=external_client
)

config = RunConfig(
    model=model,
    model_provider=external_client,
    tracing_disabled=True    
)

agent = Agent(
    name="Assistance",
    instructions="you are a helpfull assistance",    
)

result = Runner.run_sync(starting_agent=agent, input="Hi how are you",run_config=config)
print(result.final_output)
```

## Global Level
* Global level pe aap entire application ya SDK instance ke liye defaults set kar sakte hain—jaise ke default OpenAI client, base URL, ya API key.
* Example: set_default_openai_client(...) se har agent aur run mein woh client automatically istemal ho jata hai.
* Use case: Jab aap ek consistent LLM provider, endpoint, ya auth config poore app mein use karna chahte ho.


```python
from agents import Agent, Runner, OpenAIChatCompletionsModel,AsyncOpenAI,set_default_openai_api,set_default_openai_client,set_tracing_disabled
from dotenv import load_dotenv
import os

load_dotenv()

gemini_key = os.getenv('GEMINI_API_KEY')
set_default_openai_api('chat_completions')
set_tracing_disabled(disabled=True)

if not gemini_key:
    raise ValueError("API KEY is NOT Laoded")

external_client = AsyncOpenAI(
    api_key=gemini_key,
     base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

set_default_openai_client(external_client)

agent =  Agent(
    name="assistance",
    instructions="your are a helpfull asistance",
     model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client)
)

result = Runner.run_sync(starting_agent=agent,input="hi How are you")
print(result.final_output)
```

* set_default_openai_api function use bydeafult openai api and default value set on None
* set_tracing_disabled default return None



| Level      | Configure What                            | Override Scope                   | Example Use Case                                         |
| ---------- | ----------------------------------------- | -------------------------------- | -------------------------------------------------------- |
| **Global** | Default client/provider, API key, routing | Entire SDK / Application         | Use a single OpenAI client across all agents and runs    |
| **Run**    | Model, settings, tracing, guardrails      | One specific `Runner.run()` call | Temporary override: high-temperature or tracing-only run |
| **Agent**  | Model, tools, instructions                | Individual `Agent`               | Mix-and-match models: e.g., specialized agents per task  |


### Question For this Code 

* agr ap agent me model pass nh krty ho by default 4O use hoga ha gpt api ke sath

#### 1. What is from dotenv import load_dotenv?
A .env file is a plain text file where you store configuration values like API keys, database URLs, or secret keys. For example:
This line is used to load environment variables from a file named .env into your Python program.The function load_dotenv() reads the .env file and loads all the variables inside it into your system environment. This allows you to access them using os.getenv().


#### 2. OpenAIChatCompletionsModel 
you can use OpenAIChatCompletionsModel to connect to third-party LLMs if.OpenAI SDK uses GPT models by default. If we want to use a third-party LLM, we can use OpenAIChatCompletionsModel to connect to it, as long as that model supports the same message format.
```python
class OpenAIChatCompletionsModel(
    model: ChatModel | str,
    openai_client: AsyncOpenAI
)
``` 
* jab bhi hum OpenAIChatCompletionsModel ka use krty ha to humy do cheezy pass krni pharti ha base ul or api key.
lekin agr app lite llm ha use krty hato sirf api use hogi. or lite llm ka use krkr ap world ke 100 plus models access kr sakty hain.

#### 3. RunConfig (@dataclass)
```python
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

#### 4. AsyncOpenAI (@dataclass)
AsyncOpenAI is a Python class from the OpenAI library that enables asynchronous API calls to OpenAI's services
```python
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

#### 5. Agent (@dataclass)
he Agent class creates an AI agent with specific behavior and capabilities, as defined by its parameters.
agent name: str pereamter required or all perameter optional
```python
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


#### 7. Runner (@classmethod)
Runner class ek utility ya controller class hai jo AI agents ke execution ko handle karta hai. Yeh agents (jaise aapka Agent class) aur unke associated models (jaise OpenAIChatCompletionsModel) ke saath kaam karta hai, taki user prompts ko process karke responses generate kiye ja sakein. Aapke code mein, Runner.run_sync(agent, "Hello, how are you.", run_config=config) ka use dikhta hai, jo indicate karta hai ke Runner ek interface provide karta hai jo synchronous ya asynchronous tarike se agent ke operations ko execute karta hai.

dir(Runner)
```python
['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getstate__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'run', 'run_streamed', 'run_sync']
```

### Normal agent ke sath ye ye cheeezy hoti ha 
```python
Agent(name='Assistance', handoff_description=None, tools=[], mcp_servers=[], mcp_config={}, instructions='you are a help full assistance.if your asked the Nextjs related question you want handoff the Nextjs_agent and any python question you want to handoff Python_agent', prompt=None, handoffs=[], model=<agents.models.openai_chatcompletions.OpenAIChatCompletionsModel object at 0x000002139ECEFB50>, model_settings=ModelSettings(temperature=None, top_p=None, frequency_penalty=None, presence_penalty=None, tool_choice=None, parallel_tool_calls=None, truncation=None, max_tokens=None, reasoning=None, verbosity=None, metadata=None, store=None, include_usage=None, response_include=None, top_logprobs=None, extra_query=None, extra_body=None, extra_headers=None, extra_args=None), input_guardrails=[], output_guardrails=[], output_type=None, hooks=None, tool_use_behavior='run_llm_again', reset_tool_choice=True)
```