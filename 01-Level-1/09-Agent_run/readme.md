

# 1. runner.run(prompt)
* Async Requirement: Runner.run ko await karna zaroori hai kyunki yeh async method hai. Iske liye code ko asyncio.run ya event loop mein chalana padta hai.Run ko async function me use krty hain or sath await ka use bhi krty hain.asyncio ki library async function ko run 
krny ke liye use hoti hain.

* Purpose: Query bhejna aur complete response aik baar mein lena.
* Nature: Asynchronous (await karna parta hai).
* Use-case: Jab aapko full result aik hi baar mein chahiye ho.

```python
agent = Agent(name="Assistant", instructions="You are a helpful assistant", model=model)

async def main():
    result = await Runner.run(agent, "Hello, how are you.", run_config=config)
    print(result.final_output)
    print(result.last_agent)
    
asyncio.run(main())  
```
* result.last_agent ye humy Agent ki Class return krygi is tarha

**Return Agent Class**
```python
Agent(name='Assistance', handoff_description=None, tools=[], mcp_servers=[], mcp_config={}, instructions='you are a help full Assistance', prompt=None, handoffs=[], model=<agents.models.openai_chatcompletions.OpenAIChatCompletionsModel object at 0x000002C02750EAD0>, model_settings=ModelSettings(temperature=None, top_p=None, frequency_penalty=None, presence_penalty=None, tool_choice=None, parallel_tool_calls=None, truncation=None, max_tokens=None, reasoning=None, verbosity=None, metadata=None, store=None, include_usage=None, response_include=None, top_logprobs=None, extra_query=None, extra_body=None, extra_headers=None, extra_args=None), input_guardrails=[], output_guardrails=[], output_type=None, hooks=None, tool_use_behavior='run_llm_again', reset_tool_choice=True)
```

#### run method ye peramters leta ha 
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
Run a workflow starting at the given agent. The agent will run in a loop until a final output is generated. The loop runs like so:

1. The agent is invoked with the given input.
2. If there is a final output (i.e. the agent produces something of type agent.output_type, the loop terminates.
3. If there's a handoff, we run the loop again, with the new agent.
4. Else, we run tool calls (if any), and re-run the loop. In two cases, the agent may raise an exception:
5. If the max_turns is exceeded, a MaxTurnsExceeded exception is raised.
6. If a guardrail tripwire is triggered, a GuardrailTripwireTriggered exception is raised. Note that only the first agent's input guardrails are run.


##### Args
1. starting_agent
The starting agent to run.

2. input
The initial input to the agent. You can pass a single string for a user message, or a list of input items.

3. context
The context to run the agent with.

4. max_turns
The maximum number of turns to run the agent for. A turn is defined as one AI invocation (including any tool calls that might occur).

5. hooks
An object that receives callbacks on various lifecycle events.

6. run_config
Global settings for the entire agent run.

7. previous_response_id
The ID of the previous response, if using OpenAI models via the Responses API, this allows you to skip passing in input from the previous turn.

**Returns**
out :
A run result containing all the inputs, guardrail results and the output of the last agent. Agents may perform handoffs, so we don't know the specific type of the output.


# 2. runner.run_sync(prompt)

* Purpose: Same as run(), but sync code ke liye.
* Nature: Synchronous (without async/await).
* Use-case: Jab aap ka code async nahi hai (like simple scripts or CLI).

```python
result =  Runner.run_sync(agent, "Write kids Poetry funy?", run_config=config)
print(result.final_output)
print(result.last_agent)
```
* run_sync ka fucntion async function me work nh kryga qk ye Synchronous work krta hain. normal python me under run_sync chal jayega 
lekin async function me nh chlyga..

**Return Agent**
```python
Agent(name='Assistance', handoff_description=None, tools=[], mcp_servers=[], mcp_config={}, instructions='you are a help full Assistance', prompt=None, handoffs=[], model=<agents.models.openai_chatcompletions.OpenAIChatCompletionsModel object at 0x000001695DD82890>, model_settings=ModelSettings(temperature=None, top_p=None, frequency_penalty=None, presence_penalty=None, tool_choice=None, parallel_tool_calls=None, truncation=None, max_tokens=None, reasoning=None, verbosity=None, metadata=None, store=None, include_usage=None, response_include=None, top_logprobs=None, extra_query=None, extra_body=None, extra_headers=None, extra_args=None), input_guardrails=[], output_guardrails=[], output_type=None, hooks=None, tool_use_behavior='run_llm_again', reset_tool_choice=True)
```

#### run_sync method ye peramters leta ha 
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

Run a workflow synchronously, starting at the given agent. Note that this just wraps the run method, so it will not work if there's already an event loop (e.g. inside an async function, or in a Jupyter notebook or async context like FastAPI). For those cases, use the run method instead. The agent will run in a loop until a final output is generated. The loop runs like so:

1. The agent is invoked with the given input.
2. If there is a final output (i.e. the agent produces something of type agent.output_type, the loop terminates.
3. If there's a handoff, we run the loop again, with the new agent.
4. Else, we run tool calls (if any), and re-run the loop. In two cases, the agent may raise an exception:
5. If the max_turns is exceeded, a MaxTurnsExceeded exception is raised.
6. If a guardrail tripwire is triggered, a GuardrailTripwireTriggered exception is raised. Note that only the first agent's input guardrails are run.

##### Args
1. starting_agent
The starting agent to run.

2. input
The initial input to the agent. You can pass a single string for a user message, or a list of input items.

3. context
The context to run the agent with.

4. max_turns
The maximum number of turns to run the agent for. A turn is defined as one AI invocation (including any tool calls that might occur)

5. hooks
An object that receives callbacks on various lifecycle events.

6. run_config
Global settings for the entire agent run.

7. previous_response_id
The ID of the previous response, if using OpenAI models via the Responses API, this allows you to skip passing in input from the previous turn.

**Returns**
out :
A run result containing all the inputs, guardrail results and the output of the last agent. Agents may perform handoffs, so we don't know the specific type of the output.


# 3.  runner.stream(prompt)
* Purpose: Prompt bhejna aur real-time streaming mein response lena.
* Nature: Asynchronous stream (token/token ya chunk/chunk mein response aata hai). 
* Use-case: Chat apps, terminals, jahan user ko live output chahiye hota hai.

### what is streaming in openai sdk
In the OpenAI SDK, streaming refers to the ability to receive the response from the model token-by-token (or chunk-by-chunk) as it's generated, instead of waiting for the entire response to complete before you get any output.

#### Why Use Streaming?
* Faster feedback: You see results instantly as they are generated.
* Better user experience: Useful in chat apps, terminals, or any interactive UI.
* Ideal for long responses: Reduces perceived latency for long outputs.

### Synchronous
Synchronous mode mein jab user koi query karta hai, to poori request server tak bheji jati hai aur server usay process karta hai. Lekin jab tak poora jawab tayar nahi ho jata, tab tak user ko kuch bhi response nahi milta. Server jab apna kaam mukammal kar leta hai, tabhi ek baar mein poora output wapas bhejta hai. Is tarah ka system tab theek hota hai jab response chhota ho ya real-time feedback ki zarurat na ho.

Iske muqable mein asynchronous ya streaming mode mein data tukdon (chunks) mein wapas aata hai. Jaise hi server kuch output generate karta hai, wo foran user ko bhejna shuru kar deta hai. Poore response ka intezar nahi hota. Yeh approach un situations mein bohot faida mand hoti hai jahan response lamba ho ya user ko turant feedback dikhana ho – jaise AI chat apps ya terminal-based tools mein. Streaming se user ko lagta hai ke system fast aur responsive hai, kyunke output foran dikhna shuru ho jata hai.

### Asynchronous
Asynchronous (ya async) mode mein jab user koi query bhejta hai, to server usay process karna start karta hai lekin poore response ka intezar nahi karta. Jaise hi model kuch output generate karta hai, wo usay chunks (tukdon) mein turant wapas bhejna shuru kar deta hai. Iska matlab hai ke user ko pehla hissa foran mil jata hai, phir agla, phir uske baad wala — jab tak poora jawab complete nahi ho jata. Is process ko streaming kehte hain. Async mode ka faida ye hai ke user ko real-time feedback milta hai, aur response jaldi aur smooth lagta hai. Ye approach un apps ke liye ideal hoti hai jahan AI se lambi conversation hoti hai, jaise chatbots, assistants, ya terminal tools, jahan har second kaafi important hota hai.

Jab humara agent loop mein continuously tool calls ya LLM calls kar raha hota hai, to wo asynchronous tareeqay se kaam karta hai — khas kar jab hum streaming ka use karte hain.

#### Kaise hota hai async behavior agent loop mein?
1. Agent runner ya loop continuously input le raha hota hai aur usko process karne ke liye LLM ya tools ko forward kar raha hota hai.
2. Jab agent ko koi tool call karni hoti hai (e.g. weather tool, calculator, DB lookup), wo non-blocking tareeqay se async call karta hai.
3. Isi tarah, jab LLM (OpenAI ya koi aur) ko call karta hai with streaming, to response chunks mein wapas aata hai, real-time mein.


| Method              | Async / Sync | Streaming | Output Type     | Use When                             |
| ------------------- | ------------ | --------- | --------------- | ------------------------------------ |
| `runner.run()`      | Async        | ❌         | Full message    | Full output after processing         |
| `runner.stream()`   | Async        | ✅         | Streamed chunks | Real-time / token-by-token output    |
| `runner.run_sync()` | Sync         | ❌         | Full message    | When not using async (basic scripts) |


#### Key Points
* await ko humesha async funciton ke under use kia jata hain
* async function ko call krwany ke liye await lagana pharta hain.
* async.io ki library async function ko run krny ke liye use hoti hain.

### run_streamed
run_streamed() is a higher-level helper in the OpenAI Agents SDK that gives you real-time streaming (like stream()), but with the final assembled response object at the end.


```python
async def main():
    result = Runner.run_streamed(starting_agent=agent,input='hello how are you')
    
    async for event in result.stream_events():
        rich.print(event)

asyncio.run(main())
```

**OUTPUT**
```python
AgentUpdatedStreamEvent(
    new_agent=Agent(
        name='Assistance',
        handoff_description=None,
        tools=[],
        mcp_servers=[],
        mcp_config={},
        instructions='you are a helpfull assistance',
        prompt=None,
        handoffs=[],
        model=<agents.models.openai_chatcompletions.OpenAIChatCompletionsModel object at 0x00000286F3524B90>,
        model_settings=ModelSettings(
            temperature=None,
            top_p=None,
            frequency_penalty=None,
            presence_penalty=None,
            tool_choice=None,
            parallel_tool_calls=None,
            truncation=None,
            max_tokens=None,
            reasoning=None,
            verbosity=None,
            metadata=None,
            store=None,
            include_usage=None,
            response_include=None,
            top_logprobs=None,
            extra_query=None,
            extra_body=None,
            extra_headers=None,
            extra_args=None
        ),
        input_guardrails=[],
        output_guardrails=[],
        output_type=None,
        hooks=None,
        tool_use_behavior='run_llm_again',
        reset_tool_choice=True
    ),
    type='agent_updated_stream_event'
)
RawResponsesStreamEvent(
    data=ResponseCreatedEvent(
        response=Response(
            id='__fake_id__',
            created_at=1755934635.5354772,
            error=None,
            incomplete_details=None,
            instructions=None,
            metadata=None,
            model='gemini-2.0-flash',
            object='response',
            output=[],
            parallel_tool_calls=False,
            temperature=None,
            tool_choice='auto',
            tools=[],
            top_p=None,
            background=None,
            max_output_tokens=None,
            max_tool_calls=None,
            previous_response_id=None,
            prompt=None,
            prompt_cache_key=None,
            reasoning=None,
            safety_identifier=None,
            service_tier=None,
            status=None,
            text=None,
            top_logprobs=None,
            truncation=None,
            usage=None,
            user=None
        ),
        sequence_number=0,
        type='response.created'
    ),
    type='raw_response_event'
)
RawResponsesStreamEvent(
    data=ResponseOutputItemAddedEvent(
        item=ResponseOutputMessage(
            id='__fake_id__',
            content=[],
            role='assistant',
            status='in_progress',
            type='message'
        ),
        output_index=0,
        sequence_number=1,
        type='response.output_item.added'
    ),
    type='raw_response_event'
)
RawResponsesStreamEvent(
    data=ResponseContentPartAddedEvent(
        content_index=0,
        item_id='__fake_id__',
        output_index=0,
        part=ResponseOutputText(annotations=[], text='', type='output_text', logprobs=None),
        sequence_number=2,
        type='response.content_part.added'
    ),
    type='raw_response_event'
)
RawResponsesStreamEvent(
    data=ResponseTextDeltaEvent(
        content_index=0,
        delta='I',
        item_id='__fake_id__',
        logprobs=[],
        output_index=0,
        sequence_number=3,
        type='response.output_text.delta'
    ),
    type='raw_response_event'
)
RawResponsesStreamEvent(
    data=ResponseTextDeltaEvent(
        content_index=0,
        delta=' am doing well',
        item_id='__fake_id__',
        logprobs=[],
        output_index=0,
        sequence_number=4,
        type='response.output_text.delta'
    ),
    type='raw_response_event'
)
RawResponsesStreamEvent(
    data=ResponseTextDeltaEvent(
        content_index=0,
        delta=', thank you for asking! How can I help you today?\n',
        item_id='__fake_id__',
        logprobs=[],
        output_index=0,
        sequence_number=5,
        type='response.output_text.delta'
    ),
    type='raw_response_event'
)
RawResponsesStreamEvent(
    data=ResponseContentPartDoneEvent(
        content_index=0,
        item_id='__fake_id__',
        output_index=0,
        part=ResponseOutputText(
            annotations=[],
            text='I am doing well, thank you for asking! How can I help you today?\n',
            type='output_text',
            logprobs=None
        ),
        sequence_number=6,
        type='response.content_part.done'
    ),
    type='raw_response_event'
)
RawResponsesStreamEvent(
    data=ResponseOutputItemDoneEvent(
        item=ResponseOutputMessage(
            id='__fake_id__',
            content=[
                ResponseOutputText(
                    annotations=[],
                    text='I am doing well, thank you for asking! How can I help you today?\n',
                    type='output_text',
                    logprobs=None
                )
            ],
            role='assistant',
            status='completed',
            type='message'
        ),
        output_index=0,
        sequence_number=7,
        type='response.output_item.done'
    ),
    type='raw_response_event'
)
RawResponsesStreamEvent(
    data=ResponseCompletedEvent(
        response=Response(
            id='__fake_id__',
            created_at=1755934635.5354772,
            error=None,
            incomplete_details=None,
            instructions=None,
            metadata=None,
            model='gemini-2.0-flash',
            object='response',
            output=[
                ResponseOutputMessage(
                    id='__fake_id__',
                    content=[
                        ResponseOutputText(
                            annotations=[],
                            text='I am doing well, thank you for asking! How can I help you today?\n',
                            type='output_text',
                            logprobs=None
                        )
                    ],
                    role='assistant',
                    status='completed',
                    type='message'
                )
            ],
            parallel_tool_calls=False,
            temperature=None,
            tool_choice='auto',
            tools=[],
            top_p=None,
            background=None,
            max_output_tokens=None,
            max_tool_calls=None,
            previous_response_id=None,
            prompt=None,
            prompt_cache_key=None,
            reasoning=None,
            safety_identifier=None,
            service_tier=None,
            status=None,
            text=None,
            top_logprobs=None,
            truncation=None,
            usage=None,
            user=None
        ),
        sequence_number=8,
        type='response.completed'
    ),
    type='raw_response_event'
)
RunItemStreamEvent(
    name='message_output_created',
    item=MessageOutputItem(
        agent=Agent(
            name='Assistance',
            handoff_description=None,
            tools=[],
            mcp_servers=[],
            mcp_config={},
            instructions='you are a helpfull assistance',
            prompt=None,
            handoffs=[],
            model=<agents.models.openai_chatcompletions.OpenAIChatCompletionsModel object at 0x00000286F3524B90>,       
            model_settings=ModelSettings(
                temperature=None,
                top_p=None,
                frequency_penalty=None,
                presence_penalty=None,
                tool_choice=None,
                parallel_tool_calls=None,
                truncation=None,
                max_tokens=None,
                reasoning=None,
                verbosity=None,
                metadata=None,
                store=None,
                include_usage=None,
                response_include=None,
                top_logprobs=None,
                extra_query=None,
                extra_body=None,
                extra_headers=None,
                extra_args=None
            ),
            input_guardrails=[],
            output_guardrails=[],
            output_type=None,
            hooks=None,
            tool_use_behavior='run_llm_again',
            reset_tool_choice=True
        ),
        raw_item=ResponseOutputMessage(
            id='__fake_id__',
            content=[
                ResponseOutputText(
                    annotations=[],
                    text='I am doing well, thank you for asking! How can I help you today?\n',    
                    type='output_text',
                    logprobs=None
                )
            ],
            role='assistant',
            status='completed',
            type='message'
        ),
        type='message_output_item'
    ),
    type='run_item_stream_event'
)
```

1.  AgentUpdatedStreamEvent Class return Two properties 
    *  new_agent
    *  type='agent_updated_stream_event'

2. RawResponsesStreamEvent Class return Two properties 
    * data
    * type='raw_response_event'

3.  RunItemStreamEvent Class return three  properties
    * name
    * item
    * run_item_stream_event



#### Under this code
* Humy is Class sy data nikalna ha 
```python
RawResponsesStreamEvent(
    data=ResponseTextDeltaEvent(
        content_index=0,
        delta=', thank you for asking! How can I help you today?\n',
        item_id='__fake_id__',
        logprobs=[],
        output_index=0,
        sequence_number=5,
        type='response.output_text.delta'
    ),
    type='raw_response_event'
)
```
* sirf unhi ka data nikalo jiski event type run_item_stream_event ho and isinstance ye check krta ha ke event.type ResponseTextDeltaEvent ka he instance hena.

```python
async for event in result.stream_events():
     if event.type == "raw_response_event" and isinstance(event.type, ResponseTextDeltaEvent):
            print(event.data.delta)
```

#### isinstance(event.type, ResponseTextDeltaEvent) --> under this Code With pyton Code
```python
class Userinfo:
    def __init__(self, name):
        self.name = name
        
class Personinfo:
    def __init__(self, name,age):
        self.name = name 
        self.age  = age     
        
user = Userinfo("hussain")
person = Personinfo("faheem",25)

print(isinstance(user,Userinfo))  # output True
print(isinstance(person,Userinfo))   # output False     
```

#### Complete Example
```bash
set_tracing_disabled(disabled=True)

agent = Agent(
    name="Assistance",
    instructions="you are a helpfull assistance", 
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),   
)

async def main():
    
    result = Runner.run_streamed(agent, input="Please tell me 5 jokes.")
    async for event in result.stream_events():
        if event.type == "raw_response_event" and isinstance(event.data, ResponseTextDeltaEvent):
            print(event.data.delta, end="", flush=True)
            
        
asyncio.run(main())
```

##### end="" ka matlab kya hai?
By default, Python ka print() har cheez ke baad ek newline (\n) laga deta hai.
Magar agar aap end="" specify karein, to kuch bhi add nahi hota—output ek hi line mein rehta hai.

```python
print("Hello", end=" ")
print("World!")   # output / Hello World
```

##### flush=True ka kya kaam hai?
Python default tor pe output ko buffered mode mein rakhta hai — matlab, writing console ya file par turant nahi hota.

**Agar aap flush=True use karte ho, to:**
* Buffer mein jitna bhi data hai (chahe line complete na hua ho) — turant likh diya jata hai.
* Ye real-time output ya progress indicators ke liye bohot zyada useful hai.

       
---
### Complete Example
```python
from agents import Agent, Runner, OpenAIChatCompletionsModel,AsyncOpenAI,set_tracing_disabled
from dotenv import load_dotenv
import os
import asyncio
from openai.types.responses import ResponseTextDeltaEvent

load_dotenv()
set_tracing_disabled(False)

gemini_key = os.getenv("GEMINI_API_KEY")
if not gemini_key:
    raise ValueError("API KEY is NOT Loaded")


external_client = AsyncOpenAI(
    api_key=gemini_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

agent = Agent(
    name="Assistance",
    instructions="you are a helpfull assistance.",
    model=OpenAIChatCompletionsModel(model="gemini-2.0-flash", openai_client=external_client),
)

async def main():
  
  result = Runner.run_streamed(starting_agent=agent,input="write a blog")
  async for event in result.stream_events():
      if(event.type == "raw_response_event" and isinstance(event.data,ResponseTextDeltaEvent)):
          print(event.data.delta)


asyncio.run(main())
```

---

# Other Stream Events
* agent_updated_stream_event
* run_item_stream_event
  * tool_call_item
  * tool_call_output_item
  * message_output_item

```python
from agents import Agent, Runner, OpenAIChatCompletionsModel,AsyncOpenAI,set_tracing_disabled,ItemHelpers,function_tool
from dotenv import load_dotenv
import os
import asyncio
import random

load_dotenv()
set_tracing_disabled(False)

gemini_key = os.getenv("GEMINI_API_KEY")
if not gemini_key:
    raise ValueError("API KEY is NOT Loaded")


external_client = AsyncOpenAI(
    api_key=gemini_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

@function_tool
def how_many_jokes() -> int:
    return random.randint(1, 10)


agent = Agent(
    name="Joker",
    instructions="First call the `how_many_jokes` tool, then tell that many jokes..",
    model=OpenAIChatCompletionsModel(model="gemini-2.0-flash", openai_client=external_client),
    tools=[how_many_jokes]
)

async def main():
  
 result = Runner.run_streamed(starting_agent=agent,input="Hello")
 async for event in result.stream_events():
      if(event.type == "raw_response_event"):
          continue
      elif(event.type == "agent_updated_stream_event"):
          print(f"Agent updated: {event.new_agent.name}")
      
      elif event.type == "run_item_stream_event":
          if event.item.type == "tool_call_item":
                print("-- Tool was called")
          elif event.item.type == "tool_call_output_item":
                print(f"-- Tool output: {event.item.output}")
          elif event.item.type == "message_output_item":
                print(f"-- Message output:\n {ItemHelpers.text_message_output(event.item)}")
          else:
                pass      
              
asyncio.run(main())
```
#### Output
```bash
Agent updated: Joker
-- Tool was called
-- Tool output: 2
-- Message output:
 I am programmed to tell two jokes.
Why don't scientists trust atoms?
Because they make up everything!
What do you call a lazy kangaroo?
Pouch potato!
```

#### 1. raw_response_event
* Yeh LLM ka raw chunk hota hai (token by token / partial JSON).
* Matlab jo model backend se stream me bhej raha hai, woh as-is tumhe milta hai.
* Normally, isse skip karte hain (tum bhi continue kar rahe ho), kyunki woh "low level" hota hai.

#### 2. agent_updated_stream_event
* Jab agent ki state update hoti hai, yeh event aata hai.
* Example: agent ne apna name, instructions, ya context update kiya.
* Tum use print kar rahe ho:
```python
print(f"Agent updated: {event.new_agent.name}")
```

#### 3. run_item_stream_event
##### a) tool_call_item
  * Jab agent kisi tool ko call karta hai.

##### b) tool_call_output_item
  * Jab tool se output return hota hai.

##### c) message_output_item
  * Jab agent message output (final ya intermediate reply) generate karta hai.

##### d) other item types
* Jaise function_call_item, function_output_item, log_item, etc.


---
