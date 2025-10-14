


# Tracing
The Agents SDK includes built-in tracing, collecting a comprehensive record of events during an agent run: LLM generations, tool calls, handoffs, guardrails, and even custom events that occur. Using the Traces dashboard, you can debug, visualize, and monitor your workflows during development and in production.

**Tracing is enabled by default. There are different ways to disable tracing:**

1. You can globally disable tracing by setting the env var OPENAI_AGENTS_DISABLE_TRACING=1

2. You can disable tracing for a single run by setting agents.run.RunConfig.tracing_disabled to True
```bash
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel,set_tracing_disabled
set_tracing_disabled(disabled=True)

```
3. enable_verbose_stdout_logging()
enable_verbose_stdout_logging() ka use krke bhi logs ko dekh sakty hain. local tracing or dashboard tracing me ke farak ha
ke dashboard tracing me hum kisi span run hony pr ksi action ko perfrom nh krwa sakty.local tracing me customization kr sakty ha. during run tarcing or span 

### Traces and spans

* **Traces** represent a single end-to-end operation of a "workflow". They're composed of Spans. Traces have the following properties:
    * **workflow_name**: This is the logical workflow or app. For example "Code generation" or "Customer service".
    * **trace_id**: A unique ID for the trace. Automatically generated if you don't pass one. Must have the format trace_<32_alphanumeric>.
    * **group_id**: Optional group ID, to link multiple traces from the same conversation. For example, you might use a chat thread ID.
    * **disabled**: If True, the trace will not be recorded.
    * **metadata**: Optional metadata for the trace.

* **Spans** represent operations that have a start and end time. Spans have:
    * **started_at** and ended_at timestamps.
    * **trace_id**, to represent the trace they belong to
    * **pa*rent_id**, which points to the parent Span of this Span (if any)
    * **span_data**, which is information about the Span. For example, AgentSpanData contains information about the Agent, GenerationSpanData contains information about the LLM generation, etc.

### Default tracing
By default, the SDK traces the following:

* The entire Runner.{run, run_sync, run_streamed}() is wrapped in a trace().
* Each time an agent runs, it is wrapped in agent_span()
* LLM generations are wrapped in generation_span()
* Function tool calls are each wrapped in function_span()
* Guardrails are wrapped in guardrail_span()
* Handoffs are wrapped in handoff_span()
* Audio inputs (speech-to-text) are wrapped in a transcription_span()
* Audio outputs (text-to-speech) are wrapped in a speech_span()
* Related audio spans may be parented under a speech_group_span()

By default, the trace is named "Agent workflow". You can set this name if you use trace, or you can configure the name and other properties with the RunConfig.

In addition, you can set up custom trace processors to push traces to other destinations (as a replacement, or secondary destination).


### Higher level traces
Sometimes, you might want multiple calls to run() to be part of a single trace. You can do this by wrapping the entire code in a trace().

* tracing bydeafult on hoti ha (False hoti hai)
set_tracing_disabled(disabled=False)

```bash
async def main():
    
    with trace("Joke workflow"):
       result = await Runner.run(starting_agent=myagent, input=query)
       rich.print(result.final_output)
    
asyncio.run(main())
```

#### trace function arg
```bash
(function) def trace(
    workflow_name: str,
    trace_id: str | None = None,
    group_id: str | None = None,
    metadata: dict[str, Any] | None = None,
    disabled: bool = False
) -> Trace
```

##### eik he trace me multiple runner chalengy or final output last waly agent ka ayega
```bash
async def main():
    
    with trace("Joke workflow"):
       result = await Runner.run(starting_agent=myagent, input="How are you")
       result = await Runner.run(starting_agent=myagent, input="what is the prime minister of pakistan")
       result = await Runner.run(starting_agent=myagent, input="what is the weather in karachi")
       rich.print(result.final_output)
    
asyncio.run(main())
```
* Trace: ek poori journey ya workflow hai — matlab ek request ya transaction jo shayad multiple agents/services/tools se guzarti hai. 
* Span: Trace ke andar ek choti ya bada operation — jaise “database query”, “API call”, “tool execution”, ya koi aur step. Har span ka hisa hota hai us trace me.


### Local Tracing
TracingProcessor eik abstract class ha mtlb me iska is class ka koe instance nh bana sakta. mujhe TracingProcessor me mojood 
* on_trace_start
* on_trace_end
* on_span_start
* on_span_end
* shutdown
* force_flush

ko copy krke apni Custom MyTraceClass me use krna hoga.
* Abstract Class ko method ko use krny ke liye ussy create krna hoga 

```bash
import asyncio
import os
from agents import (
    Agent, Runner,TracingProcessor, AsyncOpenAI, OpenAIChatCompletionsModel,
    set_default_openai_api,
    set_default_openai_client,
    set_trace_processors,
    trace
)
from dotenv import load_dotenv
import rich

# Load API key
load_dotenv()

gemini_api_key = os.getenv('GEMINI_API_KEY')
if not gemini_api_key:
    raise ValueError("API key is not loaded")

external_client = AsyncOpenAI(
    api_key=gemini_api_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)


myagent =  Agent(
    name="assistance",
    instructions='you are a helpfull Assistance',
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
)

class LocalTraceProcessor(TracingProcessor):
    
    # consider this constructor store all traces and spans in database but here we store in list
    def __init__(self):
        self.traces = []
        self.spans = []
    
    def on_trace_start(self, trace):
        self.traces.append(trace) # jasi trace start hoga traces tarce array store ho jayega
        print(f"Trace Starting{trace.trace_id}")
    
    
    def on_trace_end(self, trace):
        print(f"Trace End{trace.export()}")
        
        
    def on_span_start(self, span):
        self.spans.append(span)
        print(f"Span start{span.span_id}")
        print(f"Span Details")
        rich.print(f"Span Details: {span.export()}")

    
    
    def on_span_end(self, span):
        print(f"Span start{span.span_id}")
        print(f"Span Details")
        rich.print(f"Span Details: {span.export()}")
    
    
    def force_flush(self):
        print(f"Forcing Flush to Tracing Data")
    
    
    def shutdown(self):
        print("=======Shutting down trace processor========")
        # Print all collected trace and span data
        print("Collected Traces:")
        for trace in self.traces:
            print(trace.export())
        print("Collected Spans:")
        for span in self.spans:
            print(span.export())    
        
    
# Configure the client
set_default_openai_client(client=external_client, use_for_tracing=True)
set_default_openai_api("chat_completions")

# Set up the custom trace processor
local_processor = LocalTraceProcessor()
set_trace_processors([local_processor])

    
async def main():
    
    with trace("Hussain workflow"):
       result = await Runner.run(starting_agent=myagent, input="How are you")
    

asyncio.run(main())
```

| Method                      | Kab/Consition par Trigger hota hai                                                                                                                                                  |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **on\_trace\_start(trace)** | Jab ek *naya trace* shuru hota hai. For example jab tum `with trace("workflow name"):` use karo, ya Runner.run() start ho jaye aur tracing enabled ho. ([OpenAI GitHub][1])         |
| **on\_trace\_end(trace)**   | Jab woh trace khatam hota hai. Yani jitna task ya workflow trace karna tha, finish ho gaya ho. ([OpenAI GitHub][2])                                                                 |
| **on\_span\_start(span)**   | Span ka individual operation ya step start hone par. Jaise agent span, generation span, tool call span, handoff span etc. ([OpenAI GitHub][1])                                      |
| **on\_span\_end(span)**     | Jab woh span poori tarah finish ho jaye — matlab us operation ka kaam ho gaya ho. ([OpenAI GitHub][2])                                                                              |
| **force\_flush()**          | Jab tum chahtay ho ke **queued (pending) traces/spans** turant backend ya jo bhi exporter hai, usko bhej do/batch export karo — bina wait ki usual schedule ya buffer full hone ka. |

#### force_flush() ka matlab
1. force_flush() ek method hai jo queued (matlab abhi export ya process hone ke intezar me) traces ya spans ko turant process/export karne ke liye use hoti hai. 
2. Yani agar tumhare paas kuch trace/span events pending hain (buffer ya queue me), aur tum chahte ho ke abhi un sab ka data export ho jaye ya delete/clear ho jaye abhi, toh force_flush() call karte ho.


### External tracing processors list
1. Weights & Biases
2. Arize-Phoenix
3. Future AGI
4. MLflow (self-hosted/OSS
5. MLflow (Databricks hosted
6. Braintrust
7. Pydantic Logfire
8. AgentOps
9. Scorecard
10. Keywords AI
11. LangSmith
12. Maxim AI
13. Comet Opik
14. Langfuse
15. Langtrace
16. Okahu-Monocle
17. Galileo
18. Portkey AI
19. LangDB AI
20. Agenta
