



# 1. Agent
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
* OpenAI (Chat Completions API) ya kisi OpenAI-compatible third party LLM ke saath easily interface provide karna.
* model="gpt-4" ya model="gemini-2.0-flash" specify karne par, ye us model ka object banata hai jise agent use karega.
* Isko AsyncOpenAI client ke saath integrate karna hota hai.
* by default openai sdk responses api use krta ha.

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

* agr ap agent me model pass nh krty ho by default 4O use hoga ha gpt api ke sath

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


# 2.  What are Model Settings?
Think of Model Settings like the knobs and dials on a professional camera. Just as a photographer adjusts focus, exposure, and shutter speed to get the perfect shot, you can adjust your AI agent's brain behavior to get exactly the response you want.

Imagine you're cooking:
* Temperature = How creative vs. focused your agent is
* Tool Choice = Whether your agent can use calculators, weather apps, etc.
* Max Tokens = How long the response can be
* Parallel Tools = Whether your agent can use multiple tools at once

```bash
# Low temperature (0.1) = Very focused, consistent answers
agent_focused = Agent(
    name="Math Tutor",
    instructions="You are a precise math tutor.",
    model_settings=ModelSettings(temperature=0.1)
)

# High temperature (0.9) = More creative, varied responses
agent_creative = Agent(
    name="Story Writer",
    instructions="You are a creative storyteller.",
    model_settings=ModelSettings(temperature=0.9)
)
```
**When to use:**
* Low (0.1-0.3): Math, facts, precise instructions
* Medium (0.4-0.6): General conversation, explanations
* High (0.7-0.9): Creative writing, brainstorming

Note: For gemini temprature range extends to 2.

#### Full code Example
```bash
import os
from agents import Agent, AsyncOpenAI, Runner, OpenAIChatCompletionsModel,ModelSettings
from agents.run import RunConfig
from dotenv import load_dotenv

load_dotenv()
gemini_api_key = os.getenv('GEMINI_API_KEY')
if not gemini_api_key:
    raise ValueError("API key is not loaded")


external_client = AsyncOpenAI(
    api_key=gemini_api_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
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

triage_agent = Agent(
    name="Helpfull Assistance",
    instructions="You are a help Full Assistance.",
    model=model,
    model_settings=ModelSettings(temperature=1) # // bydefault 0.7
)

result = Runner.run_sync(
    starting_agent=triage_agent,
    input="hi how are you.",
    run_config=config
)
print("Last agent to respond:", result.final_output)
```

### ModelSetting Arg
```bash
class ModelSettings(
    temperature: float | None = None,
    top_p: float | None = None,
    frequency_penalty: float | None = None,
    presence_penalty: float | None = None,
    tool_choice: ToolChoice = None,
    parallel_tool_calls: bool | None = None,
    truncation: Literal['auto', 'disabled'] | None = None,
    max_tokens: int | None = None,
    reasoning: Reasoning | None = None,
    verbosity: Literal['low', 'medium', 'high'] | None = None,
    metadata: dict[str, str] | None = None,
    store: bool | None = None,
    include_usage: bool | None = None,
    response_include: list[ResponseIncludable] | None = None,
    top_logprobs: int | None = None,
    extra_query: Query | None = None,
    extra_body: Body | None = None,
    extra_headers: Headers | None = None,
    extra_args: dict[str, Any] | None = None
)
```

* if use blank model_settings=ModelSettings() to agent chal jaeyga qk ModelSettings ke all arg by default none ha
* agent ki class me agent name required ha baki perameters ke bagir bhi agent run ho jayeg.

# 2. Max Tokens - The Response Length Limit
* input or output me milna kr jo token banty hain ussy max_tokens kehty hain.

```bash
triage_agent = Agent(
    name="Helpfull Assistance",
    instructions="You are a help Full Assistance.",
    model=model,
    model_settings=ModelSettings(temperature=1,max_tokens=40)
)

result = Runner.run_sync(
    starting_agent=triage_agent,
    input="write a blog in 100 word",
    run_config=config
)
print("Last agent to respond:", result.final_output)
```

##### Kya hoga agar max_tokens=5 hota hai?
* Response bohat chhota hoga: Model sirf 5 tokens tak hi answer generate karega—kuch shabdon ya short sentence se zyada nahi.
* Input ki tokens bhi count hoti hain: Agar aapka prompt kaafi lamba hai, aur usme already bahut tokens use ho chuke hain, to model ka total context window exceed ho sakta hai ya result aur chhota ho jaayega. 
* Output limit hoti hai: max_tokens sirf output tokens lol limit karta hai—input (prompt) tokens isme include nahin hote.

**Ek aam approximation ke mutabiq:**
* 1 token ≈ 4 characters (English mein)
* 1 token ≈ 0.75 words — yaani lagbhag ¾ word per token
* Iska matlab, 100 tokens ≈ 75 words

---

## Tool Choice

1. auto bydefault (llm khud choice kryga konsa tool call krna ha)
2. none   (tool call nh kr paega llm)
3. required (tool call krna paryga llm ko)

**Auto**
```bash
from agents import function_tool

@function_tool
def calculate_area(length: float, width: float) -> str:
    """Calculate the area of a rectangle."""
    area = length * width
    return f"Area = {length} × {width} = {area} square units"


triage_agent = Agent(
    name="Helpfull Assistance",
    instructions="You are a help Full Assistance.",
    model=model,
    tools=[calculate_area],
    model_settings=ModelSettings(tool_choice="auto")
)
```
* Bydefault tool choice Auto hoti hain.

**Required**
```bash
import os
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel,enable_verbose_stdout_logging,ModelSettings, function_tool
from dotenv import load_dotenv
from agents.run import RunConfig
import rich

load_dotenv()

gemini_api_key = os.getenv('GEMINI_API_KEY')

if not gemini_api_key:
    raise ValueError("Api key is not lodded")

enable_verbose_stdout_logging()

external_client = AsyncOpenAI(
    api_key=gemini_api_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

@function_tool
def get_weather(input: str)-> str:    
    return f"{input} is sunny 1C"


myagent = Agent(
    name="Assistance",
    instructions="You are a hekpfull Assistance if your asked weather related quesiton you want to use get_weather Tool",
    model= OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    tools=[get_weather],
    model_settings=ModelSettings(temperature=1,tool_choice="required")
    
    )

result = Runner.run_sync(starting_agent=myagent, input='what is the weather in karachi')
print(result.final_output)
```
* agr ap tool choice required krty hato tool must call hoga agr apny tool sy related koe question kia ho na nhi kiya ho.

**output**
```bash
Creating trace Agent workflow with id trace_6913d99575ce46c4a66b8978539525eb
Setting current trace: trace_6913d99575ce46c4a66b8978539525eb
Creating span <agents.tracing.span_data.AgentSpanData object at 0x000002054AD3E330> with id None
Running agent Assistance (turn 1)
Creating span <agents.tracing.span_data.GenerationSpanData object at 0x000002054AD3E510> with id None       
[
  {
    "content": "You are a hekpfull Assistance if your asked weather related quesiton you want to use get_weather Tool",
    "role": "system"
  },
  {
    "role": "user",
    "content": "what is the weather in karachi"
  }
]
Tools:
[
  {
    "type": "function",
    "function": {
      "name": "get_weather",
      "description": "",
      "parameters": {
        "properties": {
          "input": {
            "title": "Input",
            "type": "string"
          }
        },
        "required": [
          "input"
        ],
        "title": "get_weather_args",
        "type": "object",
        "additionalProperties": false
      }
    }
  }
]
Stream: False
Tool choice: required
Response format: NOT_GIVEN

LLM resp:
{
  "content": null,
  "refusal": null,
  "role": "assistant",
  "annotations": null,
  "audio": null,
  "function_call": null,
  "tool_calls": [
    {
      "id": "",
      "function": {
        "arguments": "{\"input\":\"karachi\"}",
        "name": "get_weather"
      },
      "type": "function"
    }
  ]
}

Creating span <agents.tracing.span_data.FunctionSpanData object at 0x000002054B2100B0> with id None
Invoking tool get_weather with input {"input":"karachi"}
Tool call args: ['karachi'], kwargs: {}
Tool get_weather returned karachi is sunny 1C
Running agent Assistance (turn 2)
Creating span <agents.tracing.span_data.GenerationSpanData object at 0x000002054B210770> with id None       
[
  {
    "content": "You are a hekpfull Assistance if your asked weather related quesiton you want to use get_weather Tool",
    "role": "system"
  },
  {
    "role": "user",
    "content": "what is the weather in karachi"
  },
  {
    "role": "assistant",
    "tool_calls": [
      {
        "id": "",
        "type": "function",
        "function": {
          "name": "get_weather",
          "arguments": "{\"input\":\"karachi\"}"
        }
      }
    ]
  },
  {
    "role": "tool",
    "tool_call_id": "",
    "content": "karachi is sunny 1C"
  }
]
Tools:
[
  {
    "type": "function",
    "function": {
      "name": "get_weather",
      "description": "",
      "parameters": {
        "properties": {
          "input": {
            "title": "Input",
            "type": "string"
          }
        },
        "required": [
          "input"
        ],
        "title": "get_weather_args",
        "type": "object",
        "additionalProperties": false
      }
    }
  }
]
Stream: False
Tool choice: NOT_GIVEN
Response format: NOT_GIVEN

LLM resp:
{
  "content": "The weather in Karachi is sunny and 1C.\n",
  "refusal": null,
  "role": "assistant",
  "annotations": null,
  "audio": null,
  "function_call": null,
  "tool_calls": null
}

Resetting current trace
The weather in Karachi is sunny and 1C.

Shutting down trace provider
Shutting down trace processor <agents.tracing.processors.BatchTraceProcessor object at 0x00000205492BEB90>
```

Agent jab llm ko pora data dega bhajyga to usny tool choice required hogi llm agent ko bolega ke tool must call krna. agent tool call kryga or tool ka response jab wapis lakr llm ko dega to ab tool choice reset ho jaye auto ho jayegi.
agr reset na hoti to agent loop me phas jata or bar bar llm tool call krwata

* by default reset_tool_choice True hoti ha jissy agent loop me nh phas pata.

**Like This**
```bash
myagent = Agent(
    name="Assistance",
    instructions="You are a hekpfull Assistance if your asked weather related quesiton you want to use get_weather Tool",
    model= OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    tools=[get_weather],
    model_settings=ModelSettings(temperature=1,tool_choice="required"),
    reset_tool_choice=False
    )
```  
* Agent loop 10 time chal kr ye Error ayega
```bash
 File "C:\Users\user\Pictures\example-app\.venv\Lib\site-packages\agents\run.py", line 436, in run
    raise MaxTurnsExceeded(f"Max turns ({max_turns}) exceeded")
agents.exceptions.MaxTurnsExceeded: Max turns (10) exceeded
```










---

```bash
triage_agent = Agent(
    name="Assistance",
     instructions=("You are helpfull Assistance"),
    model=model,
    tools=[add],
    tool_use_behavior="stop_on_first_tool"
)
```
* Agent me eik argument tool_use_behavior ka hota ha or ismy two perameter hoty ha run_llm_again, or stop_on_first_tool  defauly run_llm_again set hoga ha

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
| `StopAtTools(stop_at_tool_names=["human_review"])` | Sirf listed tool pe rukna      | ❌ Continue karta hai | ✅ Ruk jaata hai  








<!-- 
#### tool_use_behavior
```bash
triage_agent = Agent(
    name="Assistance",
     instructions=("You are helpfull Assistance"),
    model=model,
    tools=[add],
    tool_use_behavior="stop_on_first_tool"
)
```
* Agent me eik argument tool_use_behavior ka hota ha or ismy two perameter hoty ha run_llm_again, or stop_on_first_tool  defauly run_llm_again set hoga ha

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
| `StopAtTools(stop_at_tool_names=["human_review"])` | Sirf listed tool pe rukna      | ❌ Continue karta hai | ✅ Ruk jaata hai  



<!-- #### Tools Settings
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
* Ye setup zara flexible hai, lekin sawaal ka jawab less predictable ho sakta hai compare to strict mode. -->




