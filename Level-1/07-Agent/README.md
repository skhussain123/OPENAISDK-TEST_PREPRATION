



# Agent
The OpenAI Agents SDK enables you to build agentic AI apps in a lightweight, easy-to-use package with very few abstractions. It's a production-ready upgrade of our previous experimentation for agents, Swarm. The Agents SDK has a very small set of primitives:

* Agents, which are LLMs equipped with instructions and tools
* Handoffs, which allow agents to delegate to other agents for specific tasks
* Guardrails, which enable validation of agent inputs and outputs
* Sessions, which automatically maintains conversation history across agent runs

In combination with Python, these primitives are powerful enough to express complex relationships between tools and agents, and allow you to build real-world applications without a steep learning curve. In addition, the SDK comes with built-in tracing that lets you visualize and debug your agentic flows, as well as evaluate them and even fine-tune models for your application.

## Why use the Agents SDK
1. Enough features to be worth using, but few enough primitives to make it quick to learn.
2. Works great out of the box, but you can customize exactly what happens.

**Here are the main features of the SDK:**
* Agent loop: Built-in agent loop that handles calling tools, sending results to the LLM, and looping until the LLM is done.
* Python-first: Use built-in language features to orchestrate and chain agents, rather than needing to learn new abstractions.
* Handoffs: A powerful feature to coordinate and delegate between multiple agents.
* Guardrails: Run input validations and checks in parallel to your agents, breaking early if the checks fail.
* Sessions: Automatic conversation history management across agent runs, eliminating manual state handling.
* Function tools: Turn any Python function into a tool, with automatic schema generation and Pydantic-powered validation.
* Tracing: Built-in tracing that lets you visualize, debug and monitor your workflows, as well as use the OpenAI suite of evaluation, fine-tuning and distillation tools.

```bash
from agents import Agent, Runner
agent: Agent = Agent(name="Assistant", instructions="You are a helpful assistant")
```

#### what is from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel
* Python agents module (ya package) ke andar jao
* aur sirf Agent aur Runner ko le aao

* agent perameter me first perameter agent name
* second perameter instructions ha jissmy sysytem prompt bhi kethy hain(agent persona / Role)
* agent ko minium name perameter required ha

* Agent ek blueprint (class) hai.
* Agent(...) us class ka object (instance) banata hai.
* agent: Agent matlab "main keh raha hoon ke ye variable ek Agent type ka hoga."


#### Run Agent (RUN LEVEL)
```bash
import os
from agents import Agent, Runner,OpenAIChatCompletionsModel,set_tracing_disabled
from openai import AsyncOpenAI
from dotenv import load_dotenv

load_dotenv()
gemini_api_key = os.getenv('GEMINI_API_KEY')

if not gemini_api_key:
    raise ValueError("Api Key Not lodded")

external_client = AsyncOpenAI(
    api_key=gemini_api_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/",  
)

model = OpenAIChatCompletionsModel(
    model="gemini-2.0-flash",
    openai_client=external_client
)

set_tracing_disabled(True)

agent: Agent = Agent(name="Assistant", instructions="You are a helpful assistant",model=model)
result = Runner.run_sync(starting_agent=agent, input = "write a blog")

print(result.final_output)
```

##### 1. Agent
Ye class OpenAI Agents SDK mein hoti hai, jo ek intelligent AI actor ko represent karti hai. Ye ek AI assistant hota hai jo:
* Aapko name, instructions, aur model deta hai.
* Agar zarurat ho, to ek agent dosre agent ko handoff bhi kar sakta hai.
* Zyada complex workflows mein, agent tools aur guardrails use karke tasks perform kar sakta hai.

#### 2. Runner
Ye bhi ek class hai jo ek agent ko execute/run karti hai. Key points:
* Runner.run, Runner.run_sync, ya Runner.run_streamed methods ke through agent ko input pass karke output liya jaata hai.
* Ye agent ke thinking loop ko manage karti hai — input receive karna, model ke through response generate karna, tools ya handoffs perform karna, aur final output deliver karna.

#### 3. OpenAIChatCompletionsModel
Ye model wrapper class hai. Iska kaam hai:
* OpenAI (Chat Completions API) ya kisi OpenAI-compatible LLM ke saath easily interface provide karna.
* model="gpt-4" ya model="gemini-2.0-flash" specify karne par, ye us model ka object banata hai jise agent use karega.
* Isko AsyncOpenAI client ke saath integrate karna hota hai.

#### 4. set_tracing_disabled
Ye helper function hai (class nahi), jo SDK ke tracing mechanism ko enable ya disable karta hai. Jab aap LLM models external providers se integrate karte hain (like Gemini via OpenAI-compatible API), to default tracing (OpenAI dashboard tracing) fail ho sakti hai. Us case mein, tracing ko disable karna useful hota hai.

#### 5. AsyncOpenAI
Ye client class hai jo asynchronously OpenAI-compatible API se connect karta hai. Iska purpose:
* Aapke .env file se API key aur base URL ke zariye external model endpoints (jaise Gemini) se safely connect karna.
* OpenAI ya OpenAI-compatible endpoints ke saath async requests manage karta hai.

#### 6. 6. load_dotenv (from dotenv library)
Ye utility function hota hai jo .env file se environment variables (jaise API keys) load karta hai. Iska purpose:
* Sensitive information code me hard-code na karna.
8 Securely secrets ko environment me laana, jisse os.getenv("GEMINI_API_KEY") jaise calls use karke easily access ho sake.


#### When You Want ro Customize Agent Configration 
```bash
config = RunConfig(
    model=model,
    model_provider=external_client,
    tracing_disabled=True
)

result = Runner.run_sync(agent, "Hello!", run_config=config)
```
* Runner ke paas koi extra configuration nahi hoti.
* Sirf wahi chalega jo agent banate waqt set kiya tha (model, client, tracing waghera).
* Agar tumhe run ki settings change karni ho (jaise ek run me tracing on, dusre me off), to agent dobara banana padega ya manual changes karne padenge.


#### Agent Basic configuration
```bash
agent = Agent(
    name="Haiku agent",
    instructions="Always respond in haiku form",
    model="o3-mini",
    tools=[get_weather],
)
```
* name: A required string that identifies your agent.
* instructions: also known as a developer message or system prompt.
* model: which LLM to use, and optional model_settings to configure model tuning parameters like temperature, top_p, etc.
* tools: Tools that the agent can use to achieve its tasks.


# Model Configuration
Agents SDK is setup to use OpenAI as default providers. When using other providers you can setup at different levels:

1. Agent Level
2. RUN LEVEL
3. Global Level

## 1. AGENT LEVEL
```bash
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
```bash
import os
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel, RunConfig
from dotenv import load_dotenv
from agents.run import RunConfig

# Load environment variables
load_dotenv()
gemini_api_key = os.getenv('GEMINI_API_KEY')

# Check if the API key is loaded
if not gemini_api_key:
    raise ValueError("Api is not lodded")

# Initialize the AsyncOpenAI client
external_client = AsyncOpenAI(
    api_key=gemini_api_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/", 
)

# Create a model instance
external_model = OpenAIChatCompletionsModel(
    model="gemini-2.0-flash",
    openai_client=external_client
)

# Create a RunConfig instance for custom configuration
config = RunConfig(
    model=external_model,
    model_provider=external_client,
    tracing_disabled=True
)

# Create an Agent instance
myagent = Agent(
    name='Assistance',
    instructions='you are a help full Assistance',
    model=external_model
)

# Run the agent with the custom configuration
result = Runner.run_sync(starting_agent=myagent, input='write a 3 poem in list', run_config=config)
print(result.final_output)
```

## Global Level
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

| Level      | Configure What                            | Override Scope                   | Example Use Case                                         |
| ---------- | ----------------------------------------- | -------------------------------- | -------------------------------------------------------- |
| **Global** | Default client/provider, API key, routing | Entire SDK / Application         | Use a single OpenAI client across all agents and runs    |
| **Run**    | Model, settings, tracing, guardrails      | One specific `Runner.run()` call | Temporary override: high-temperature or tracing-only run |
| **Agent**  | Model, tools, instructions                | Individual `Agent`               | Mix-and-match models: e.g., specialized agents per task  |


#### 1. Global Level
* Global level pe aap entire application ya SDK instance ke liye defaults set kar sakte hain—jaise ke default OpenAI client, base URL, ya API key.
* Example: set_default_openai_client(...) se har agent aur run mein woh client automatically istemal ho jata hai.
* Use case: Jab aap ek consistent LLM provider, endpoint, ya auth config poore app mein use karna chahte ho.

#### 2. Run Level
* Runner (ya Runner.run) configuration ke through aap ek specific run ke liye model provider, model settings, tracing options etc. override kar sakte hain.
* Isme aap RunConfig object pass karte ho, jisme settings jaise model choice, modelProvider, modelSettings, tracing flags, guardrails, context, etc. set ho sakte hain.
* Use case: Jab ek specific execution ke liye different setup chahiye ho (e.g., test run, high-temperature model, tracing disabled, etc.).

#### 3. Agent Level
* Har Agent instance apni khud ki configuration specify kar sakta hai—jaise model, model_settings, tools, instructions, aur even custom ModelProvider.
* Yeh flexibility deta hai ke different agents use different models or providers in the same application/workflow.
* Use case: Jab ek workflow mein multiple agents ho, aur aap chahte ho ke har agent ek specific model ya provider use kare (e.g., Spanish agent uses GPT-3.5, English agent uses Gemini, etc.).


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

#### 3. RunConfig (@dataclass)
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

#### 4. AsyncOpenAI (@dataclass)
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

#### 5. Agent (@dataclass)
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


#### 7. Runner (@classmethod)
Runner class ek utility ya controller class hai jo AI agents ke execution ko handle karta hai. Yeh agents (jaise aapka Agent class) aur unke associated models (jaise OpenAIChatCompletionsModel) ke saath kaam karta hai, taki user prompts ko process karke responses generate kiye ja sakein. Aapke code mein, Runner.run_sync(agent, "Hello, how are you.", run_config=config) ka use dikhta hai, jo indicate karta hai ke Runner ek interface provide karta hai jo synchronous ya asynchronous tarike se agent ke operations ko execute karta hai.

dir(Runner)
```bash
['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getstate__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'run', 'run_streamed', 'run_sync']
```


















<!-- ##### Context
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
``` -->
