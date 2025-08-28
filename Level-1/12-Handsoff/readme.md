
## Handoffs
Handoffs allow an agent to delegate tasks to another agent. This is particularly useful in scenarios where different agents specialize in distinct areas. For example, a customer support app might have agents that each specifically handle tasks like order status, refunds, FAQs, etc.

Handoffs are represented as tools to the LLM. So if there's a handoff to an agent named Refund Agent, the tool would be called transfer_to_refund_agent.

### Creating a handoff
All agents have a handoffs param, which can either take an Agent directly, or a Handoff object that customizes the Handoff.

You can create a handoff using the handoff() function provided by the Agents SDK. This function allows you to specify the agent to hand off to, along with optional overrides and input filters.

```bash
import os
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel
from agents.run import RunConfig
from dotenv import load_dotenv


load_dotenv()
gemini_api_key = os.getenv('GEMINI_API_KEY')

if not gemini_api_key:
    raise ValueError("Api key is not loadded")

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

Nextjs_agent = Agent(
   name="Nextjs_agent",
   instructions='you are a help full NextJS Assistace',  
)

Python_agent = Agent(
   name="Python_agent",
   instructions='you are a help full Python Assistace',  
)

triage_agent = Agent(
    name="Assistance",
    instructions='you are a help full assistance.if your asked the Nextjs related question you want handoff the Nextjs_agent and any python question you want to handoff Python_agent',
    model=model,
    handoffs=[Nextjs_agent,Python_agent]
)

result = Runner.run_sync(starting_agent=triage_agent,input='i have some isses the Python opps',run_config=config)
print(result.final_output)
print(result.last_agent) # <--- this is property
```
*handoff agent ka name llm ke p-ass is tarha jata ha transfer_to_nextjs_agent


**Out Ke Sath ye Agent Class Return hogi result.last_agent ki jasy se**
```bash
Agent(name='Python_agent', handoff_description=None, tools=[], mcp_servers=[], mcp_config={}, instructions='you are a help full Python Assistace', prompt=None, handoffs=[], model=None, model_settings=ModelSettings(temperature=None, top_p=None, frequency_penalty=None, presence_penalty=None, tool_choice=None, parallel_tool_calls=None, truncation=None, max_tokens=None, reasoning=None, verbosity=None, metadata=None, store=None, include_usage=None, response_include=None, top_logprobs=None, extra_query=None, extra_body=None, extra_headers=None, extra_args=None), input_guardrails=[], output_guardrails=[], output_type=None, hooks=None, tool_use_behavior='run_llm_again', reset_tool_choice=True)
```

Handoffs allow an agent to delegate task responsibility to another specialized agent. SDK is process ko ek tool call ke roop mein treat karta hai—e.g., agar aap Agent B ko handoff karte hain, toh LLM ko ek “transfer_to_agent_b” tool dikhega, jo handoff initiate karta hai


## Customizing handoffs via the handoff() function
The handoff() function lets you customize things.

* agent: This is the agent to which things will be handed off.
* tool_name_override: By default, the Handoff.default_tool_name() function is used, which resolves to transfer_to_<agent_name>. You can override this.
* tool_description_override: Override the default tool description from Handoff.default_tool_description()
* on_handoff: A callback function executed when the handoff is invoked. This is useful for things like kicking off some data fetching as soon as you know a handoff is being invoked. This function receives the agent context, and can optionally also receive LLM generated input. The input data is controlled by the input_type param.
* input_type: The type of input expected by the handoff (optional).
* input_filter: This lets you filter the input received by the next agent. See below for more.
* is_enabled: Whether the handoff is enabled. This can be a boolean or a function that returns a boolean, allowing you to dynamically enable or disable the handoff at runtime.


**if you want to customize the agent you want to import**
```bash
from agents import (
    Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel,handoff
)
```

#### Agent ko Customize krny ka method
```bash
import os
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel, handoff
from agents.run import RunConfig
from dotenv import load_dotenv

# Load API key
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

# Define specialized agent
Nextjs_agent = Agent(
    name="Nextjs_agent",
    instructions="You are a helpful Next.js assistant."
)

# jab Nextjs_agent handoff sy call hoga to ye function call hokr customize agent ke details bateyga
def on_handoff_debug(ctx):
    print("[DEBUG] Handoff triggered!")
    print("Tool name:", nextjs_handoff.tool_name)
    print("Tool description:", nextjs_handoff.tool_description)
    return Nextjs_agent


# Create Handoff object, then manually assign .name
nextjs_handoff = handoff(
    agent=Nextjs_agent,
    tool_name_override="specialized_nextjs_agent",
    tool_description_override="Transfer to specialized Next.js agent for routing issues.",
    on_handoff=on_handoff_debug  # <--- jab ap chahty ha Nextjs_agent call hoto koe dusra function call ho jaye to on_handoff attribute use kro
)

triage_agent = Agent(
    name="Assistance",
    instructions="You are a helpful assistant. If the query is about Next.js, hand off to the Next.js agent.",
    model=model,
    handoffs=[nextjs_handoff]
)

result = Runner.run_sync(
    starting_agent=triage_agent,
    input="I have some issues with Next.js routing",
    run_config=config
)

print("Last agent to respond:", result.last_agent)
```

**Output**
```bash
[DEBUG] Handoff triggered!
Tool name: specialized_nextjs_agent
Tool description: Transfer to specialized Next.js agent for routing issues.
Last agent to respond: Agent(name='Nextjs_agent', handoff_description=None, tools=[], mcp_servers=[], mcp_config={}, instructions='You are a helpful Next.js assistant.', prompt=None, handoffs=[], model=None, model_settings=ModelSettings(temperature=None, top_p=None, frequency_penalty=None, presence_penalty=None, tool_choice=None, parallel_tool_calls=None, truncation=None, max_tokens=None, reasoning=None, verbosity=None, metadata=None, store=None, include_usage=None, response_include=None, top_logprobs=None, extra_query=None, extra_body=None, extra_headers=None, extra_args=None), input_guardrails=[], output_guardrails=[], output_type=None, hooks=None, tool_use_behavior='run_llm_again', reset_tool_choice=True)
```

#### handoff ye Peramters Lega
```bash
(function) def handoff(
    agent: Agent[TContext@handoff],
    *,
    on_handoff: OnHandoffWithoutInput,
    tool_description_override: str | None = None,
    tool_name_override: str | None = None,
    input_filter: ((HandoffInputData) -> HandoffInputData) | None = None,
    is_enabled: bool | ((RunContextWrapper[Any], Agent[Any]) -> MaybeAwaitable[bool]) = True
) -> Handoff[TContext@handoff, Agent[TContext@handoff]]
```

##### Args
1. agent
The agent to handoff to, or a function that returns an agent.
2. tool_name_override
Optional override for the name of the tool that represents the handoff.
3. tool_description_override
Optional override for the description of the tool that represents the handoff
4. on_handoff
A function that runs when the handoff is invoked.
5. input_type
the type of the input to the handoff. If provided, the input will be validated against this type. Only relevant if you pass a function that takes an input.
6. input_filter
a function that filters the inputs that are passed to the next agent.
7. is_enabled
Whether the handoff is enabled. Can be a bool or a callable that takes the run context and agent and returns whether the handoff is enabled. Disabled handoffs are hidden from the LLM at runtime.


## Handoff inputs
Handoff Inputs ek mechanism hai jisme, jab ek agent dusre agent ko “handoff” (delegate) kar raha ho, to aap LLM (Large Language Model) se kuch structured data expect kar sakte ho—jaise reason, ticket number, task details—aur wo data naya agent receive kare.

Ye aap define karte ho using the input_type parameter, jo Pydantic model ki tarah hota hai. SDK is input ko JSON schema ke through validate karta hai aur aap us data ko on_handoff callback me conveniently use kar sakte ho.

