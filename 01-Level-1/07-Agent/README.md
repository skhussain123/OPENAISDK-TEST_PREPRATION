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

```python
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


#### Run Agent 
```python
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
config = RunConfig(
    model=model,
    model_provider=external_client,
    tracing_disabled=True    
)

model = OpenAIChatCompletionsModel(
    model="gemini-2.0-flash",
    openai_client=external_client
)

set_tracing_disabled(True)

agent: Agent = Agent(name="Assistant", instructions="You are a helpful assistant")
result = Runner.run_sync(starting_agent=agent, input = "write a blog",run_config = config)

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
```python
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

#### run() vs run_sync() vs run_streamed()
| Method           | Execution Type  | Return Type          | Use Case                             |
| ---------------- | --------------- | -------------------- | ------------------------------------ |
| `run()`          | Async           | `RunResult`          | Async environments, concurrent tasks |
| `run_sync()`     | Sync (blocking) | `RunResult`          | Simple scripts, CLI tools            |
| `run_streamed()` | Async + Stream  | `RunResultStreaming` | Real-time feedback (e.g., live UIs)  |


#### Agent Basic configuration
```python
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


# 2 . LiteLLM Agent
**uv add opanai-agents[litellm]**
```python
from litellm import completion
import os
from dotenv import load_dotenv

load_dotenv()

gemini_api_key = os.getenv("GEMINI_API_KEY")
open_api_key = os.getenv("OPENAI_API_KEY")

if not gemini_api_key:
    raise ValueError("GEMINI_API_KEY is not set. Please ensure it is defined in your .env file.")

if not open_api_key:
    raise ValueError("open_api_key is not set. Please ensure it is defined in your .env file.")


def gemini():
    response = completion(
        model="gemini/gemini-1.5-flash",
        messages=[{"role": "user", "content": "Hello, how are you?"}],
        api_key=gemini_api_key
    )
    print(response.choices[0].message["content"])


def gemini2():
    response = completion(
        model="gemini/gemini-2.0-flash-exp",
        messages=[{ "content": "Hello, how are you?","role": "user"}],
        api_key=gemini_api_key
    )
    print(response.choices[0].message["content"])   
        
    
def openai():
    response = completion(
        model="openai/gpt-4o",
        messages=[{"role": "user", "content": "Hello, how are you?"}],
        api_key=open_api_key
    )
    print(response.choices[0].message["content"])   
    
     

# Run the function
gemini()
# openai()
# gemini2()
```


### AsyncOpenAI Class Perameters
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


### RunConfig Class Perameters
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

### OpenAIChatCompletionsModel Class Perameters
```python
class OpenAIChatCompletionsModel(
    model: ChatModel | str,
    openai_client: AsyncOpenAI
)
```

#### Agent Class Perameters
```python
class Agent(
    name: str,
    handoff_description: str | None = None,
    tools: list[Tool] = list,
    mcp_servers: list[MCPServer] = list,
    mcp_config: MCPConfig = lambda : MCPConfig(),
    instructions: str | ((RunContextWrapper[Any], Agent[Any]) -> MaybeAwaitable[str]) | None = None,
    prompt: Prompt | DynamicPromptFunction | None = None,
    handoffs: list[Agent[Any] | Handoff[Any, Any]] = list,
    model: str | Model | None = None,
    model_settings: ModelSettings = ModelSettings,
    input_guardrails: list[InputGuardrail[Any]] = list,
    output_guardrails: list[OutputGuardrail[Any]] = list,
    output_type: type[Any] | AgentOutputSchemaBase | None = None,
    hooks: AgentHooks[Any] | None = None,
    tool_use_behavior: StopAtTools | ToolsToFinalOutputFunction[Any] | Literal['run_llm_again', 'stop_on_first_tool'] = "run_llm_again",
    reset_tool_choice: bool = True
)
```

#### run_sync Method Perameters
```python
(method) def run_sync(
    starting_agent: Agent[TContext@run_sync],
    input: str | list[TResponseInputItem],
    *,
    context: TContext@run_sync | None = None,
    max_turns: int = DEFAULT_MAX_TURNS,
    hooks: RunHooks[TContext@run_sync] | None = None,
    run_config: RunConfig | None = None,
    previous_response_id: str | None = None,
    session: Session | None = None
) -> RunResult
```

#### run Method Perameters
```python
(method) def run(
    starting_agent: Agent[TContext@run],
    input: str | list[TResponseInputItem],
    *,
    context: TContext@run | None = None,
    max_turns: int = DEFAULT_MAX_TURNS,
    hooks: RunHooks[TContext@run] | None = None,
    run_config: RunConfig | None = None,
    previous_response_id: str | None = None,
    session: Session | None = None
) -> CoroutineType[Any, Any, RunResult]
```

#### run_streamed method Perameters
```python
(method) def run_streamed(
    starting_agent: Agent[TContext@run_streamed],
    input: str | list[TResponseInputItem],
    context: TContext@run_streamed | None = None,
    max_turns: int = DEFAULT_MAX_TURNS,
    hooks: RunHooks[TContext@run_streamed] | None = None,
    run_config: RunConfig | None = None,
    previous_response_id: str | None = None,
    session: Session | None = None
) -> RunResultStreaming
```

### Default Perameters Set
* tracing bydfault openai ki taraf sy enabled hoti ha (False hoti ha)
* DEFAULT_MAX_TURNS = 10



## Experiments
```python
agent = Agent(
    name=""
)
result = Runner.run_sync(starting_agent=agent,input="Hi ahow are you", run_config=config)
print(result.last_agent)
```
* blank name bhi rakh kr agent chal jayega..

```python
agent = Agent(
    name=None
)
```
* none use krengy to Error ayega.