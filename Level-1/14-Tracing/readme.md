


# Tracing
The Agents SDK includes built-in tracing, collecting a comprehensive record of events during an agent run: LLM generations, tool calls, handoffs, guardrails, and even custom events that occur. Using the Traces dashboard, you can debug, visualize, and monitor your workflows during development and in production.

**Tracing is enabled by default. There are different ways to disable tracing:**

1. You can globally disable tracing by setting the env var OPENAI_AGENTS_DISABLE_TRACING=1

2. You can disable tracing for a single run by setting agents.run.RunConfig.tracing_disabled to True
```bash
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel,set_tracing_disabled
set_tracing_disabled(disabled=True)

```

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

