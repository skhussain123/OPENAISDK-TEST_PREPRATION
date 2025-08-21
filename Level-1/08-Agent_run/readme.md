

# 1. runner.run(prompt)
* Async Requirement: Runner.run ko await karna zaroori hai kyunki yeh async method hai. Iske liye code ko asyncio.run ya event loop mein chalana padta hai.Run ko async function me use krty hain or sath await ka use bhi krty hain.asyncio ki library async function ko run 
krny ke liye use hoti hain.

* Purpose: Query bhejna aur complete response aik baar mein lena.
* Nature: Asynchronous (await karna parta hai).
* Use-case: Jab aapko full result aik hi baar mein chahiye ho.

```bash
agent = Agent(name="Assistant", instructions="You are a helpful assistant", model=model)

async def main():
    result = await Runner.Run(agent, "Hello, how are you.", run_config=config)
    print(result.final_output)
    print(result.last_agent)
    
asyncio.run(main())  
```
* result.last_agent ye humy Agent ki Class return krygi is tarha

**Return Agent Class**
```bash
Agent(name='Assistance', handoff_description=None, tools=[], mcp_servers=[], mcp_config={}, instructions='you are a help full Assistance', prompt=None, handoffs=[], model=<agents.models.openai_chatcompletions.OpenAIChatCompletionsModel object at 0x000002C02750EAD0>, model_settings=ModelSettings(temperature=None, top_p=None, frequency_penalty=None, presence_penalty=None, tool_choice=None, parallel_tool_calls=None, truncation=None, max_tokens=None, reasoning=None, verbosity=None, metadata=None, store=None, include_usage=None, response_include=None, top_logprobs=None, extra_query=None, extra_body=None, extra_headers=None, extra_args=None), input_guardrails=[], output_guardrails=[], output_type=None, hooks=None, tool_use_behavior='run_llm_again', reset_tool_choice=True)
```

#### run method ye peramters leta ha 
```bash
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

```bash
result =  Runner.run_sync(agent, "Write kids Poetry funy?", run_config=config)
print(result.final_output)
print(result.last_agent)
```
* run_sync ka fucntion async function me work nh kryga qk ye Synchronous work krta hain. normal python me under run_sync chal jayega 
lekin async function me nh chlyga..

**Return Agent**
```bash
Agent(name='Assistance', handoff_description=None, tools=[], mcp_servers=[], mcp_config={}, instructions='you are a help full Assistance', prompt=None, handoffs=[], model=<agents.models.openai_chatcompletions.OpenAIChatCompletionsModel object at 0x000001695DD82890>, model_settings=ModelSettings(temperature=None, top_p=None, frequency_penalty=None, presence_penalty=None, tool_choice=None, parallel_tool_calls=None, truncation=None, max_tokens=None, reasoning=None, verbosity=None, metadata=None, store=None, include_usage=None, response_include=None, top_logprobs=None, extra_query=None, extra_body=None, extra_headers=None, extra_args=None), input_guardrails=[], output_guardrails=[], output_type=None, hooks=None, tool_use_behavior='run_llm_again', reset_tool_choice=True)
```

#### run_sync method ye peramters leta ha 
```bash
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

##### 1. runner.run(prompt)
* 🔹 Purpose: Query bhejna aur complete response aik baar mein lena. 
* 🔹 Nature: Asynchronous (await karna parta hai). 
* 🔹 Use-case: Jab aapko full result aik hi baar mein chahiye ho.

##### 2. runner.run_sync(prompt)
* 🔹 Purpose: Same as run(), but sync code ke liye. 
* 🔹 Nature: Synchronous (without async/await). 
* 🔹 Use-case: Jab aap ka code async nahi hai (like simple scripts or CLI).

##### 3. runner.stream(prompt)
* 🔹 Purpose: Prompt bhejna aur real-time streaming mein response lena. 
* 🔹 Nature: Asynchronous stream (token/token ya chunk/chunk mein response aata hai). 
* 🔹 Use-case: Chat apps, terminals, jahan user ko live output chahiye hota hai.

| Method              | Async / Sync | Streaming | Output Type     | Use When                             |
| ------------------- | ------------ | --------- | --------------- | ------------------------------------ |
| `runner.run()`      | Async        | ❌         | Full message    | Full output after processing         |
| `runner.stream()`   | Async        | ✅         | Streamed chunks | Real-time / token-by-token output    |
| `runner.run_sync()` | Sync         | ❌         | Full message    | When not using async (basic scripts) |


#### runner.run_sync vs runner.run
1. runner.run() ek asynchronous function ko run karta hai runner ke context ke andar.
Isse await ke saath call kiya jata hai, aur yeh async code ke liye hota hai.
2. Same as run(), but sync code ke liye. Nature: Synchronous (without async/await).

#### Key Points
* await ko humesha async funciton ke under use kia jata hain
* async function ko call krwany ke liye await lagana pharta hain.
* async.io ki library async function ko run krny ke liye use hoti hain.

### run_streamed
run_streamed() is a higher-level helper in the OpenAI Agents SDK that gives you real-time streaming (like stream()), but with the final assembled response object at the end.










---
### Errors Info
##### if you Run
```bash
import asyncio

result = Runner.run(starting_agent=myagent,input='write a 3 poem in list',run_config=config)
print(result.final_output)
print(result.last_agent)
```

**You Will See this Error** 
```bash
Traceback (most recent call last):
  File "C:\Users\user\Pictures\example-app\main.py", line 40, in <module>
    print(result.final_output)
          ^^^^^^^^^^^^^^^^^^^
AttributeError: 'coroutine' object has no attribute 'final_output'
sys:1: RuntimeWarning: coroutine 'Runner.run' was never awaited
```

##### if you Run
```bash
import asyncio

async def main():
    result = Runner.run_sync(starting_agent=myagent,input='write a 3 poem in list',run_config=config)
    print(result.final_output)
    print(result.last_agent)
asyncio.run(main()) 
```

**You Will See**
```bash
RuntimeError: This event loop is already running
sys:1: RuntimeWarning: coroutine 'AgentRunner.run' was never awaited
(example-app) PS C:\Users\user\Pictures\example-app>
```

##### if you Run
```bash
result = Runner.run_streamed(starting_agent=myagent,input='write a 3 poem in list',run_config=config)
print(result.final_output)
print(result.last_agent)
```

**You Will See this Error**
```bash
File "C:\Users\user\Pictures\example-app\.venv\Lib\site-packages\agents\run.py", line 341, in run_streamed 
    return runner.run_streamed(
           ^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\user\Pictures\example-app\.venv\Lib\site-packages\agents\run.py", line 612, in run_streamed 
    streamed_result._run_impl_task = asyncio.create_task(
                                     ^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\user\AppData\Local\Programs\Python\Python311\Lib\asyncio\tasks.py", line 381, in create_task
    loop = events.get_running_loop()
           ^^^^^^^^^^^^^^^^^^^^^^^^^
RuntimeError: no running event loop
sys:1: RuntimeWarning: coroutine 'AgentRunner._start_streaming' was never awaited
```

##### runner.run_sync vs runner.run
1. runner.run() ek asynchronous function ko run karta hai runner ke context ke andar. Isse await ke saath call kiya jata hai, aur yeh async code ke liye hota hai.
2. Same as run(), but sync code ke liye. Nature: Synchronous (without async/await).

##### Key points
* await ko humesha async funciton ke under use kia jata hain
* async function ko call krwany ke liye await lagana pharta hain.
* async.io ki library async function ko run krny ke liye use hoti hain.
