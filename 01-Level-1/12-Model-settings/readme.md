
# What are Model Settings?
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
**Creativity ka matlab hai “naya sochna” aur “naye tareeke se kisi cheez ko banana ya hal karna”.**

### Temperature ke Types aur Unka Kaam

#### 1. Low Temperature (0.0 - 0.3)
* **Kya Hota Hai?:** Jab temperature kam hoti hai, jaise 0.1, toh model bohot focused aur predictable jawab deta hai. Yani, woh wahi jawab choose karta hai jo uske training ke hisaab se sabse zyada likely ya correct hai.
* **Kaam:** Is setting mein jawab bohot precise aur consistent hote hain. Randomness ya creativity bohot kam hoti hai.
* **Example:** Jaise aapka "Math Tutor" (temperature 0.1) wala example hai, yeh setting perfect hai jab aapko accurate aur clear jawab chahiye, jaise mathematical solutions ya factual information.

#### 2. Medium Temperature (0.4 - 0.6)
* **Kya Hota Hai?:** Yeh ek balanced approach hai. Model thodi creativity ke saath jawab deta hai, lekin phir bhi zyada tar predictable aur relevant rehta hai.
* 3. **Kaam:** Yeh setting tab useful hai jab aapko thodi flexibility chahiye, lekin jawab bilkul out-of-the-box nahi hone chahiye. Maslan, agar aap ek discussion ya explanation chahte hain jo thoda engaging ho lekin factual bhi rahe.
* **Example:** General knowledge questions ya discussions ke liye yeh setting kaam aati hai.

#### 3. High Temperature (0.7 - 0.9 ya usse zyada)
* **Kya Hota Hai?:** Jab temperature zyada hoti hai, jaise 0.9, toh model bohot creative aur random jawab deta hai. Yeh different aur unique ideas generate kar sakta hai, lekin kabhi kabhi jawab kam accurate ya off-topic bhi ho sakte hain.
* **Kaam:** Yeh setting tab use hoti hai jab aapko creative ya imaginative content chahiye, jaise stories, poems, ya out-of-the-box ideas
* **Example:** Jaise aapka "Story Writer" (temperature 0.9) wala example hai, yeh setting stories ya creative writing ke liye perfect hai.

#### Comparision
| Temperature | Expect karo                                                                                               |
| ----------- | --------------------------------------------------------------------------------------------------------- |
| **0.1-0.2** | Jawab bohat seedha, predictable, kam variation; similar answers baar baar milenge.                        |
| **0.5-0.7** | Thodi creativity – thode unexpected comparisons, metaphors ya ideas; phir bhi relevant.                   |
| **0.9-1.0** | Zyada alag, creative aur kabhi kabhi unusual ya imaginative jawab; kabhi topic se thoda dur ja sakta hai. |


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

##### Kaam:
* Top-k output ko control karta hai by limiting choices to a fixed number of tokens.
* Yeh creative ya predictable output ke liye use hota hai, depending on k ki value.
* Example: Technical ya factual answers ke liye chhota k (jaise k=10) better hai, jabke creative tasks ke liye bada k (jaise k=100).

#### Top-p aur Top-k Mein Difference
| Feature             | Top-p (Nucleus Sampling)                                       | Top-k Sampling                                                             |
| ------------------- | -------------------------------------------------------------- | -------------------------------------------------------------------------- |
| **Selection Basis** | Probability threshold (p) ke basis pe tokens select hote hain. | Fixed number (k) ke basis pe top tokens select hote hain.                  |
| **Flexibility**     | Dynamic hai; nucleus size har step pe change ho sakta hai.     | Static hai; har baar fixed k tokens hi liye jaate hain.                    |
| **Output Control**  | Zyada natural aur relevant output deta hai.                    | Output predictable ya diverse ho sakta hai, k ke size pe depend karta hai. |
| **Use Case**        | Creative lekin controlled content (jaise stories).             | Factual ya creative tasks, depending on k value.                           |

#### Top_p , Top_k, Temperature
| Setting | Temperature              | Top-k                | Top-p                | Output ka nature                                                 |
| ------- | ------------------------ | -------------------- | -------------------- | ---------------------------------------------------------------- |
| A       | Low (0.2)                | Low (e.g. k=5)       | Strict (p=0.3-0.5)   | Bohut predictable, safe; repeat hone wali phrases; kam surprises |
| B       | Medium (0.7)             | Moderate (k=50)      | Moderate (p=0.8-0.9) | Accha balance; thodi variety, context maintain hogi              |
| C       | High (1.0 ya us se upar) | High (k=200 ya open) | High (p≈1.0)         | Bohut creative, unpredictable; risk of off topic parts           |


#### Top_p , Top_k, Temperature Combination


# 3. Tool Choice

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


# 4. Parallel Tool Calls (default None)
* Jab parallel_tool_calls = true hota hai, to model ek hi step mein multiple tools ko ek saath call kar sakta hai (parallel execution).
* Jab parallel_tool_calls = false hota hai, to model ek waqt pe sirf ek tool call karta hai (sequential execution).
* Gemini API ka OpenAI-compatible wrapper abhi sirf sequential tool calls allow karta hai (parallel nahi).

#### Example
##### parallel_tool_calls = true
  * Model ek hi turn mein ek saath web.search() aur python dono chala sakta hai.
  * Fayda: Speed zyada hoti hai, tasks ek hi waqt process hote hain.

##### parallel_tool_calls = false
  * Model pehle web.search() karega → uska result lega → phir python chalaye ga.
  * Fayda: Order maintained rehta hai, debugging easy hoti hai.

```bash
# Agent can use multiple tools at once
parallel_agent = Agent(
    name="Multi-Tasker",
    tools=[weather_tool, calculator, translator],
    model_settings=ModelSettings(
        tool_choice="auto",
        parallel_tool_calls=True  # Use multiple tools simultaneously (parallel tool calling not support for gemini chat compatible)
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

# 5. frequency_penalty
* Jab frequency_penalty low (0 ya near 0) hota hai → model zyadatar tokens repeat karne ki aadat rakhta hai (words/phrases dobara use kar sakta hai).
* Jab frequency_penalty high hota hai → model repeated words ko avoid karta hai, aur nayi variety ke words choose karta hai.

#### Formula-wise idea:
Ye penalty model ke logit scores (jo token choose karte hain) par lagti hai.
* Har token jo pehle output mein aa chuka hai, uska score penalize ho jaata hai jitni dafa wo repeat hua hai.
* Matlab jitni dafa ek word repeat hoga, uske dobara choose hone ka chance kam hota jaata hai.

#### Example

**Prompt: "Write a poem about the moon."**
##### frequency_penalty = 0
* Output ho sakta hai:
* "The moon is bright, the moon is light, the moon is night..." (zyada repetition)

##### frequency_penalty = 2
* Output ho sakta hai:
* "The moon glows softly, guiding dreams across the sky..." (kam repetition, zyada variety)


```bash
# More focused vocabulary
focused_agent = Agent(
    name="Focused",
    model_settings=ModelSettings(
        top_p=0.3,              # Use only top 30% of vocabulary
        frequency_penalty=0.5,   # Avoid repeating words
    )
)
```

# 6. presence_penalty
* frequency_penalty → Ek token jitni dafa repeat hota hai, utni hi zyada penalty lagti hai (repetition count based).
* presence_penalty → Bas ek hi dafa agar token aa gaya, to uske dobara aane ke chance kam ho jaate hain (presence based, count se farq nahi).

#### Simple Explanation
* Low presence_penalty (0) → Model easily same words/ideas dobara use karega.
* High presence_penalty → Model naya vocabulary aur nayi directions explore karega (repeat avoid karega aur naye topics introduce karega).


#### Example
**Prompt: "Talk about cats."**
##### presence_penalty = 0
* Output ho sakta hai:
* "Cats are cute. Cats are playful. Cats love to sleep." (zyada “cats” repeat)

##### presence_penalty = 2
* Output ho sakta hai:
* "Cats are cute. They are playful animals that enjoy sleeping and hunting." (naye words aate hain, “cats” dobara kam repeat hota hai)

## 🎯 When to Use Each Setting

| Setting | Use When | Example |
|---------|----------|---------|
| **Low Temperature** | Need precise, consistent answers | Math problems, fact-checking |
| **High Temperature** | Want creative, varied responses | Story writing, brainstorming |
| **Tool Choice: Required** | Want to force tool usage | Data analysis, calculations |
| **Tool Choice: None** | Want chat-only responses | Casual conversation |
| **Low Max Tokens** | Need brief responses | Quick answers, summaries |
| **High Max Tokens** | Need detailed explanations | Tutorials, documentation |

---

### resolve() Methods
Jab humare paas ek base setting ho (jaise temperature = 0.5, max_tokens = 100), aur hum chahte hain ke kuch runs mein kuch cheezein change ho jaayen (jaise temperature = 0.8) — to resolve() method use karke hum ek naya settings object bana sakte hain jisme base settings + override settings merge ho.

```python
base_settings = ModelSettings(
    temperature=0.5,
    max_tokens=100,
)

# Override settings at runtime
override_settings = ModelSettings(
    temperature=0.9,
)

# Resolve merged settings
final_settings = base_settings.resolve(override_settings)

myagent =  Agent(
    name="assistance",
    instructions='you are a helpfull assistant',
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    model_settings=final_settings
)

result = Runner.run_sync(starting_agent=myagent, input='what is the age of hussain')
print(result.last_agent)
```




