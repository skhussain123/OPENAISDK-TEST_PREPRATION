



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


#### Run Agent 
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


# 2 . LiteLLM Agent
**uv add opanai-agents[litellm]**
```bash

```


# 3.  What are Model Settings?
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

### Temperature ke Types aur Unka Kaam

#### 1. Low Temperature (0.0 - 0.3)
* **Kya Hota Hai?:** Jab temperature kam hoti hai, jaise 0.1, toh model bohot focused aur predictable jawab deta hai. Yani, woh wahi jawab choose karta hai jo uske training ke hisaab se sabse zyada likely ya correct hai.
* **Kaam:** Is setting mein jawab bohot precise aur consistent hote hain. Randomness ya creativity bohot kam hoti hai.
* **Example:** Jaise aapka "Math Tutor" (temperature 0.1) wala example hai, yeh setting perfect hai jab aapko accurate aur clear jawab chahiye, jaise mathematical solutions ya factual information.

#### 2. Medium Temperature (0.4 - 0.7)
* **Kya Hota Hai?:** Yeh ek balanced approach hai. Model thodi creativity ke saath jawab deta hai, lekin phir bhi zyada tar predictable aur relevant rehta hai.
* 3. **Kaam:** Yeh setting tab useful hai jab aapko thodi flexibility chahiye, lekin jawab bilkul out-of-the-box nahi hone chahiye. Maslan, agar aap ek discussion ya explanation chahte hain jo thoda engaging ho lekin factual bhi rahe.
* **Example:** General knowledge questions ya discussions ke liye yeh setting kaam aati hai.

#### 3. High Temperature (0.8 - 1.0 ya usse zyada)

* **Kya Hota Hai?:** Jab temperature zyada hoti hai, jaise 0.9, toh model bohot creative aur random jawab deta hai. Yeh different aur unique ideas generate kar sakta hai, lekin kabhi kabhi jawab kam accurate ya off-topic bhi ho sakte hain.
* **Kaam:** Yeh setting tab use hoti hai jab aapko creative ya imaginative content chahiye, jaise stories, poems, ya out-of-the-box ideas
* **Example:** Jaise aapka "Story Writer" (temperature 0.9) wala example hai, yeh setting stories ya creative writing ke liye perfect hai.



### Example 1: Math Tutor with Low Temperature
```bash
from agents import Agent, ModelSettings, Runner

# Create a precise math tutor
math_tutor = Agent(
    name="Math Tutor",
    instructions="You are a precise math tutor. Always show your work step by step.",
    model_settings=ModelSettings(
        temperature=0.1,  # Very focused
        max_tokens=500    # Enough for detailed steps
    )
)

result = Runner.run_sync(math_tutor, "Solve: 2x + 5 = 13")
print(result.final_output)
```

#### Max Tokens Kya Hai?
* **Max_tokens** ek parameter hai jo AI model ke har response ke liye maximum kitne "tokens" generate ho sakte hain, yeh control karta hai.
* **Token Kya Hai?:** Token ek chhoti unit hoti hai jo text ko represent karti hai. Ek token ek word, punctuation, ya space bhi ho sakta hai. Average taur par:
   * 1 word ≈ 1-2 tokens (English mein).
   * Example: "Hello, world!" yeh 3 words aur ~5 tokens hai (Hello + comma + space + world + exclamation).
* Max_tokens ka Kaam: Yeh limit set karta hai ke model ek baar mein kitna lamba jawab de sakta hai. Agar max_tokens=400, toh model ka response 400 tokens se zyada nahi hoga.

---

### Example 2: Creative Writer with High Temperature
```bash
creative_writer = Agent(
    name="Creative Writer",
    instructions="You are a creative storyteller. Write engaging, imaginative stories.",
    model_settings=ModelSettings(
        temperature=0.8,  # Very creative
        max_tokens=300    # Short but creative
    )
)

result = Runner.run_sync(creative_writer, "Write a short story about a robot learning to paint")
print(result.final_output)
```
---

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

## 1. Top-p Sampling Kya Hai?
Definition: Top-p (nucleus sampling) ek method hai jisme model apne possible outputs (tokens) mein se sirf un tokens ko select karta hai jo ek specific probability threshold (p) ke andar aate hain. Yani, model woh tokens choose karta hai jo combined probability mein ek particular percentage (p) cover karte hain.

### Kaise Kaam Karta Hai?:
* Model har possible token ko probability ke hisaab se rank karta hai.
* Phir woh chhote se chhota set (nucleus) banata hai jisme tokens ki total probability p (jaise 0.9) tak hoti hai.
* Sirf is nucleus ke tokens mein se randomly select karta hai.

### Example:
* Agar top-p=0.9, toh model woh tokens select karega jo 90% probability cover karte hain. Baaki 10% low-probability tokens ignore ho jaate hain.
* Yeh output ko creative banata hai, lekin bilkul random nahi, kyunki low-probability wale tokens nahi liye jaate.

### Kaam:
* Top-p output ko balanced rakhta hai—na bohot predictable, na bohot random.
* Agar aap creative lekin relevant jawab chahte hain, toh top-p acha hai.
* Example: Story writing ya engaging content ke liye top-p=0.9 acha hota hai.

## 2. Top-k Sampling Kya Hai?
Definition: Top-k sampling mein model har step pe sabse zyada probability wale "k" tokens ko select karta hai aur unme se randomly ek choose karta hai.
##### Kaise Kaam Karta Hai?:
  * Model sab tokens ko probability ke hisaab se sort karta hai.
  * Top-k tokens (jaise k=50) select karta hai aur unme se randomly ek pick karta hai.
  * Baaki tokens ignore kar diya jaate hain.
##### Example:
  * Agar top-k=50, toh model har baar top 50 high-probability tokens mein se choose karega.
  * Chhota k (jaise k=10) zyada predictable output deta hai, jabke bada k (jaise k=100) zyada diverse output deta hai.






















# Tool Choice

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

##### tool_use_behavior

```bash
triage_agent = Agent(
    name="Assistance",
     instructions=("You are helpfull Assistance"),
    model=model,
    tools=[add],
    tool_use_behavior="stop_on_first_tool"
)
```
* Agent me eik argument tool_use_behavior ka hota ha or ismy two perameter hoty ha run_llm_again, or stop_on_first_tool  default run_llm_again set hoga ha

1. tool_use_behavior="stop_on_first_tool" ka matlab kya hai?
Ye setting Agent ko ye batata hai ke jab koi tool (function) use kiya jaye, to uske baad LLM (language model) ko dobara run na karna — yani usi waqt ruk jana.

2. (run_llm_again):
Tool run karne ke baad agent LLM ko dobara run karta hai, takay output ko explain kare ya aage steps kare.

| Behavior                  | Kya hota hai                        | Example Output                       |
| ------------------------- | ----------------------------------- | ------------------------------------ |
| `stop_on_first_tool`      | Tool chalate hi agent ruk jata hai  | `8`                                  |
| default (`run_llm_again`) | Tool ke baad LLM phir se chalta hai | `The result of adding 5 and 3 is 8.` |

--- 

##### StopAtTools
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


#### Parallel Tool Calls
```bash
# Agent can use multiple tools at once
parallel_agent = Agent(
    name="Multi-Tasker",
    tools=[weather_tool, calculator, translator],
    model_settings=ModelSettings(
        tool_choice="auto",
        parallel_tool_calls=True  # Use multiple tools simultaneously
    )
)

# Agent uses tools one at a time
sequential_agent = Agent(
    name="One-at-a-Time",
    tools=[weather_tool, calculator, translator],
    model_settings=ModelSettings(
        tool_choice="auto",
        parallel_tool_calls=False  # Use tools one by one
    )
)
```

#### Top-P and Penalties
```bash
# More focused vocabulary
focused_agent = Agent(
    name="Focused",
    model_settings=ModelSettings(
        top_p=0.3,              # Use only top 30% of vocabulary
        frequency_penalty=0.5,   # Avoid repeating words
        presence_penalty=0.3     # Encourage new topics
    )
)
```

## 🎯 When to Use Each Setting

| Setting | Use When | Example |
|---------|----------|---------|
| **Low Temperature** | Need precise, consistent answers | Math problems, fact-checking |
| **High Temperature** | Want creative, varied responses | Story writing, brainstorming |
| **Tool Choice: Required** | Want to force tool usage | Data analysis, calculations |
| **Tool Choice: None** | Want chat-only responses | Casual conversation |
| **Low Max Tokens** | Need brief responses | Quick answers, summaries |
| **High Max Tokens** | Need detailed explanations | Tutorials, documentation |


