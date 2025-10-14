
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
* handoff agent ka name llm ke p-ass is tarha jata ha transfer_to_nextjs_agent

```bash
Python_agent = Agent(
   name="Python_agent",
   instructions='you are a help full Python Assistace',
   handoff_description="you are poem writer"  
)
```
* **Instructions:** Yeh batata hai ke Python_agent khud kya karega jab usay query milegi. Masalan, instructions='you are a helpful Python Assistant' ka matlab hai ke yeh agent Python-related sawalon ke jawab dega, jaise coding help ya debugging.
* **Handoff_description:** Yeh triage_agent ke liye ek hint hai jo batata hai ke Python_agent kis tarah ke queries handle kar sakta hai. Masalan, handoff_description="you are poem writer" ka matlab hai ke triage_agent query ko Python_agent ke taraf bhej sakta hai agar query poem se related lagti hai. Lekin jab query Python_agent ke pas jati hai, to woh apne instructions ke mutabiq kaam karta hai, na ke handoff_description ke.


**Out Ke Sath ye Agent Class Return hogi result.last_agent ki jasy se**
```bash
Agent(name='Python_agent', handoff_description=None, tools=[], mcp_servers=[], mcp_config={}, instructions='you are a help full Python Assistace', prompt=None, handoffs=[], model=None, model_settings=ModelSettings(temperature=None, top_p=None, frequency_penalty=None, presence_penalty=None, tool_choice=None, parallel_tool_calls=None, truncation=None, max_tokens=None, reasoning=None, verbosity=None, metadata=None, store=None, include_usage=None, response_include=None, top_logprobs=None, extra_query=None, extra_body=None, extra_headers=None, extra_args=None), input_guardrails=[], output_guardrails=[], output_type=None, hooks=None, tool_use_behavior='run_llm_again', reset_tool_choice=True)
```

Handoffs allow an agent to delegate task responsibility to another specialized agent. SDK is process ko ek tool call ke roop mein treat karta hai—e.g., agar aap Agent B ko handoff karte hain, toh LLM ko ek “transfer_to_agent_b” tool dikhega, jo handoff initiate karta hai

**Jab Hum Agent ko instructions or handoff_description dengy to Triage Agent ke pass Merge hokr is tarha jaega**
```python
Python_agent = Agent(
   name="Python_agent",
   instructions='you are a help full Python Assistace',  
   handoff_description="you a Inteligent Python Teacher " 
)
```
```python
"description": "Handoff to the Python_agent agent to handle the request. you a Inteligent Python Teacher ",
```

---

# 1. handoff make two ways
* create normal agent and pass tool perameter in triage_agent
* using handoff()

## Customizing handoffs via the handoff() function
The handoff() function lets you customize things.

* agent: This is the agent to which things will be handed off.
* tool_name_override: By default, the Handoff.default_tool_name() function is used, which resolves to transfer_to_<agent_name>. You can override this.
* tool_description_override: Override the default tool description from Handoff.default_tool_description()
* on_handoff: A callback function executed when the handoff is invoked. This is useful for things like kicking off some data fetching as soon as you know a handoff is being invoked. This function receives the agent context, and can optionally also receive LLM generated input. The input data is controlled by the input_type param.
* input_type: The type of input expected by the handoff (optional).
* input_filter: This lets you filter the input received by the next agent. See below for more.
* is_enabled: Whether the handoff is enabled. This can be a boolean or a function that returns a boolean, allowing you to dynamically enable or disable the handoff at runtime.


#### Arg
```bash
(function) def handoff(
    agent: Agent[TContext@handoff],
    *,
    tool_name_override: str | None = None,
    tool_description_override: str | None = None,
    input_filter: ((HandoffInputData) -> HandoffInputData) | None = None,
    is_enabled: bool | ((RunContextWrapper[Any], Agent[Any]) -> MaybeAwaitable[bool]) = True
) -> Handoff[TContext@handoff, Agent[TContext@handoff]]
```

##### Args Defination
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

# 2. Difference Between single agent aur handoff() agent

#### 1. Normal Agent ko Direct Pass Karna
```bash
Nextjs_agent = Agent(
    name="Nextjs_agent",
    instructions="You are a helpful Next.js assistant."
)

triage_agent = Agent(
    name="Assistance",
    instructions="You are a helpful assistant. If the query is about Next.js, hand off to the Next.js agent.",
    model=model,
    handoffs=[Nextjs_agent]
)
```
##### Yeh Kya Karta Hai?:
* Nextjs_agent ko direct handoffs list mein pass kiya gaya hai.
* triage_agent query ko analyze karta hai aur Nextjs_agent ke instructions ("You are a helpful Next.js assistant") ke basis par decide karta hai ke query Next.js se related hai ya nahi.
* Handoff ka faisla Nextjs_agent ke name aur instructions par depend karta hai. Yani, triage_agent LLM ke zariye samajhta hai ke query "Next.js" se related hai to Nextjs_agent ko bhej dega.

##### Kab Use Karna?:
* Jab aap chahte hain ke handoff ka logic simple ho aur triage_agent khud agent ke instructions ya name se faisla kare.
* Yeh tab kaam karta hai jab handoff ke liye zyada customization ki zarurat nahi hoti.


### 2. handoff() Function ka Use Karna
* nextjs_handoff ka name or desc llm pass tool_name_override or tool_description_override wala jaeyga.

```bash
Nextjs_agent = Agent(
    name="Nextjs_agent",
    instructions="You are a helpful Next.js assistant."
)

nextjs_handoff = handoff(
    agent=Nextjs_agent,
    tool_name_override="specialized_nextjs_agent",
    tool_description_override="Transfer to specialized Next.js agent for routing issues."
)

triage_agent = Agent(
    name="Assistance",
    instructions="You are a helpful assistant. If the query is about Next.js, hand off to the Next.js agent.",
    model=model,
    handoffs=[nextjs_handoff]
)
```
##### Yeh Kya Karta Hai?:
1. handoff() function ke zariye aap Nextjs_agent ko ek custom wrapper mein pass karte hain, jisme aap tool_name_override aur tool_description_override define kar sakte hain.
2. tool_name_override ek custom naam deta hai jo triage_agent ke liye handoff ke tool ko identify karta hai.
3. tool_description_override ek specific description deta hai jo triage_agent ko batata hai ke yeh handoff kis tarah ke queries ke liye suitable hai (masalan, "routing issues" ke liye).
4. triage_agent ab tool_description_override ("Transfer to specialized Next.js agent for routing issues") ko dekhega query ko handoff karne ke liye, na ke sirf Nextjs_agent ke instructions ko.

##### Kab Use Karna?:
* Jab aap handoff ke logic ko zyada precise aur controlled banana chahte hain.
* Masalan, agar aap chahte hain ke Nextjs_agent sirf Next.js ke "routing issues" ke liye handoff ho, to tool_description_override mein yeh specific likh sakte hain.
* Yeh tab useful hai jab aap ke paas multiple agents hain aur aap chaahte hain ke triage_agent specific scenarios ke liye sahi agent select kare.


#### Dono mein Farq

#### Control aur Specificity:
Normal Agent: Handoff ka faisla Nextjs_agent ke name aur instructions par depend karta hai. Yeh zyada generic hota hai aur triage_agent ke LLM par chhod deta hai ke query kaun se agent ke liye hai.
handoff() Function: tool_description_override ke zariye aap handoff ke logic ko zyada specific bana sakte hain. Masalan, aap keh sakte hain ke sirf "routing issues" ke liye Nextjs_agent ko handoff kiya jaye, chahe query mein "Next.js" ka zikr ho.

#### Customization:
Normal Agent: Customization sirf instructions tak seemit hai. triage_agent ko khud hi decide karna hota hai ke query kisko bhejna hai.
handoff() Function: tool_name_override aur tool_description_override ke zariye aap handoff ke behavior ko fine-tune kar sakte hain, jaise specific query types ke liye agent select karna.


## 1. is_enabled=True bydefault True
* is_enabled=True hone ka matlab hai ki handoff option hamesha available hai.
* is_enabled=false hony pr ab specialized_nextjs_agent llm ke pass nh jayega.

```bash
Nextjs_agent = Agent(
    name="Nextjs_agent",
    instructions="You are a helpful Next.js assistant."
)

nextjs_handoff = handoff(
    agent=Nextjs_agent,
    tool_name_override="specialized_nextjs_agent",
    tool_description_override="Transfer to specialized Next.js agent for routing issues.",
    is_enabled=False
)

triage_agent = Agent(
    name="Assistance",
    instructions="You are a helpful assistant. If the query is about Next.js, hand off to the Next.js agent.",
    model=model,
    handoffs=[nextjs_handoff]
)
```

## 2. input_filter 
input_filter ek function hai jo OpenAI Agents SDK mein query ya input ko process ya modify karta hai pehle ke woh agent ya LLM ke paas jaye. Yeh query ko validate, clean, ya transform karta hai (jaise capital letters mein convert karna) taake agent ke liye sahi aur safe input bheja jaye.

```bash
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel, handoff, enable_verbose_stdout_logging,HandoffInputData

# Input Filter Function
def Convert_capital_letter(handoff_input: 'HandoffInputData') -> 'HandoffInputData':
    """Query ko capital letters mein convert karta hai aur HandoffInputData return karta hai."""
    # Query string ko extract karna
    query = handoff_input.input_history
    print("DEBUG: Original query:", query)
    
    # Query ko capital (uppercase) mein convert karna
    query = query.upper()
    print("DEBUG: Capitalized query:", query)
    
    # Agar Next.js related query hai, to prefix add karna
    if "NEXT.JS" in query:
        query = f"NEXT.JS-RELATED QUERY: {query}"
    
    # Modified HandoffInputData object banakar return karna
    modified_handoff_input = HandoffInputData(
        input_history=query,
        pre_handoff_items=handoff_input.pre_handoff_items,
        new_items=handoff_input.new_items,
        run_context=handoff_input.run_context
    )
    return modified_handoff_input

nextjs_handoff = handoff(
    agent=Nextjs_agent,
    tool_name_override="specialized_nextjs_agent",
    tool_description_override="Transfer to specialized Next.js agent for routing issues.",
    input_filter=Convert_capital_letter  # Input filter apply kiya
)

triage_agent = Agent(
    name="Assistance",
    instructions="You are a helpful assistant. If the query is about Next.js, hand off to the Next.js agent.",
    model=model,
    handoffs=[nextjs_handoff]
)
```
* input_filter sy query pehly Convert_capital_letter function ke pass jayegi or capital letter me convert hokr llm ke pass jayegi


## 3. on_handoff parameter 
on_handoff ek callback function hota hai jo handoff() mein pass kiya jaata hai.
* Ye function tab chalta hai jab handoff invoke kiya jaata hai — yani jab ek agent control transfer kar ke doosre agent ko delegate karta hai.
* Is function ko RunContextWrapper milta hai (aur agar input_type specified hai to structured input bhi), aur ye ek agent ko return karta hai, jise execution continue karna hota hai.

```python
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel,handoff,RunContextWrapper
from typing import Any


Nextjs_agent = Agent(
    name="Nextjs Agent",
    instructions="You are a helpful NextJS assistant."
)
   # on_handoff callback define karo
def on_handoff_callback(ctx: RunContextWrapper[Any]):
    print("Handoff trigger hua — context:", ctx)
    return Nextjs_agent

   # Handoff object create karo, customizing behavior
nextjs_handoff = handoff(
    agent=Nextjs_agent,
    on_handoff=on_handoff_callback
)

triage_agent = Agent(
    name="Triage Assistance Agent",
    instructions=(
        "You are a helpful assistant.\n"
        "If the user asks a Next.js related question, hand off to the Nextjs agent."
    ),
    model=model,
    handoffs=[nextjs_handoff]
)

result = Runner.run_sync(
    starting_agent=triage_agent,
    input="I have some issues with Next.js ops",
    run_config=config
)
```

## 4. input_type parameter 
Definition: input_type ek optional parameter hai jo handoff() function mein diya ja sakta hai, taake aap specify kar saken ke handoff ke waqt LLM se jo input milta hai uska expected structure ya type kya hoga—jaise ek Pydantic model (structured data), string, ya dict.

1. Structured definition: Pehle, aap ek Pydantic model define karte hain, jisme aap specify karte hain ke input ka format kya hoga (jaise fields aur types).
2. handoff() call mein input_type parameter use karte hain taake SDK is model ke basis par LLM se aane wale input ko validate kar sake.
3. Agar validation successful hoti hai, to structured input aapke on_handoff callback ya next agent tak bheja jaata hai, strongly typed.
4. Agar input mismatch ho, to SDK error throw karta hai—type safety aur reliability ensure hoti hai.

```python
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel,handoff,RunContextWrapper
from pydantic import BaseModel

# Step 1: Structured input type define karein
class EscalationData(BaseModel):
    reason: str


specialist = Agent(
    name="Escalation Agent",
    instructions="You are a Escalation Agent"
)

# on_handoff callback define karein (structured input receive karega)
def on_handoff_callback(ctx: RunContextWrapper, input_data: EscalationData):
    print("Handoff ho gaya! Reason:", input_data.reason)
    return specialist


handoff_obj = handoff(
    agent=specialist,
    input_type=EscalationData,
    on_handoff=on_handoff_callback
)

triage_agent = Agent(
    name="Triage Agent",
    instructions="Agar user escalation ka reason bataye, to escalate karo.",
    handoffs=[handoff_obj]
)

result = Runner.run_sync(starting_agent=triage_agent, input="I have some issues with Next.js ops", run_config=config )
print("Final Output:", result.final_output)
```
* iska matlab hai ke handoff hone ke waqt jo data next agent ko pass hoga, woh EscalationData type ka hoga.
Yani specialist agent sirf tab trigger hoga jab usay EscalationData type ka input milega.


### Callbacks in Handoffs
```python
from datetime import datetime
from pydantic import BaseModel
from typing import Optional
from agents import handoff, RunContextWrapper

class EscalationData(BaseModel):
    reason: str
    priority: Optional[str] = "medium"

async def safety_callback(ctx: RunContextWrapper, input_data: Optional[EscalationData] = None):
    timestamp = datetime.now()
    print(f"[HANDOFF {timestamp}] Escalating: {input_data.reason if input_data else 'Unknown'}")
    # Parallel data fetch (non-blocking)
    # await fetch_user_history(ctx.user_id)
    # Or notify: send_slack_alert(f"Safety handoff: {input_data.priority}")

safety_agent = Agent(name="Safety Expert", instructions="Handle safety concerns.")

custom_handoff = handoff(
    safety_agent,
    name="escalate_to_safety",
    input_type=EscalationData,
    on_handoff=safety_callback,
)

# In your main agent
main_agent = Agent(handoffs=[custom_handoff], ...)
```

### Handoff perameters
| Parameter                   | Purpose / Use                                                                            | Detail                                                                                                                         |
| --------------------------- | ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `agent`                     | Woh agent jisko handoff karna hai.                                                       | Required. ([OpenAI Github][1])                                                                                                 |
| `tool_name_override`        | Default tool name override karna.                                                        | Default hota hai `transfer_to_<agent_name>`. ([OpenAI Github][1])                                                              |
| `tool_description_override` | Tool ka description change karna.                                                        | ([OpenAI Github][1])                                                                                                           |
| `on_handoff`                | Callback jab handoff execute ho jaaye.                                                   | Yahan aap custom logic daal sakte hain jaise logging, data fetch karna etc. ([OpenAI Github][1])                               |
| `input_type`                | Agar aap chahte hain ke LLM kuch additional structured data bhi de jab handoff ho.       | Yeh schema define karta hai, jaise “EscalationData” with `reason` field etc. ([OpenAI Github][2])                              |
| `input_filter`              | History ya conversation ka woh hissa control karne ke liye jo next agent ko dikhai dega. | By default poora conversation history chala jata hai; filter se unwanted parts remove kiye ja sakte hain. ([OpenAI Github][1]) |
| `is_enabled`                | Decide karna ke handoff available ho ya nahi, dynamically.                               | Boolean ya callback to enable/disable based on context. ([OpenAI Github][2])                                                   |












