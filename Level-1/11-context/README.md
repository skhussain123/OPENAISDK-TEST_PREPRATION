

[OpenAi to Study Context management](https://openai.github.io/openai-agents-python/context/)

# Context Management
Context management in the OpenAI Agents SDK refers to handling additional data that your code can use during an agent’s execution. This “context” comes in two main forms:

## 1. Local Context
What It Is:
Local context is any data or dependencies you pass to your agent's run that your code (tools, lifecycle hooks, etc.) can use. It’s entirely internal and never sent to the LLM.

### How It Works:

#### Creating Context:
You create a Python object—often using a dataclass or a Pydantic model—to encapsulate data like a username, user ID, logger, or helper functions.

#### Passing Context:
You pass this object to the run method (e.g., Runner.run(..., context=your_context)). The SDK wraps your object in a RunContextWrapper, making it available to every tool function, lifecycle hook, or callback during that run via wrapper.context.

#### Key Point:
All parts of a single agent run must share the same type of context, ensuring consistency.


### Example Use Cases:

* Storing user details (e.g., a username or ID) that your tools might need.
* Injecting dependencies such as loggers or data fetchers.
* Providing helper functions accessible throughout the run.

Note: This local context is not exposed to the LLM. It’s solely for your backend logic and operations.

## 2. Agent/LLM Context
What It Is:
Agent/LLM context refers to the information the LLM sees when it generates responses. This is essentially the conversation history or messages (like system prompts, instructions, and user inputs) that guide its output.

### How to Use It:
#### Embedding in Instructions:
Include important context (like the user’s name, current date, or specific guidelines) directly in the agent’s instructions or system prompts.

#### Passing in Inputs:
You can also add context to the input message when calling Runner.run(), ensuring that this data is part of the conversation that the LLM processes.

#### Function Tools:
The LLM may also invoke function tools to fetch on-demand data that wasn’t initially part of its conversation history.

#### Retrieval/Web Search:
Use specialized tools to pull in relevant external data, thereby grounding the LLM’s responses in up-to-date or detailed information.

### Key Difference:
While the local context is internal and never sent to the LLM, the agent/LLM context is deliberately exposed as part of the conversation to influence and guide the LLM’s response generation.


