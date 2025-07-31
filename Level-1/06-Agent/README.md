
### Chat With GPT turbo
```bash
import os
from openai import AsyncOpenAI
from dotenv import load_dotenv
import asyncio

load_dotenv()

OPENAI_API_KEY = os.getenv("OPENAI_API_KEY")

if not OPENAI_API_KEY:
    raise ValueError("Please Set Valid OPENAI_API_KEY")

client = AsyncOpenAI(api_key=OPENAI_API_KEY)

async def main():
    response = await client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": "Write a haiku about recursion in programming."}]
    )
    print(response.choices[0].message.content)

asyncio.run(main())
```



## Prepration With gemini-2.0-flash
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