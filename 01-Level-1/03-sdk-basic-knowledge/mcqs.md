## Section 1: Core Concepts (Questions 1-15)

### Q00. LLMs (Large Language Models) by default kis type ke hote hain?**

A) Stateful – apna pura conversation history yaad rakhte hain  
B) Stateless – har request independent hoti hai (correct)  
C) Semi-stateful – thoda context yaad rakhte hain  
D) Immutable – ek baar train hone ke baad change nahi ho sakte

---

### Q1. What is the primary purpose of the OpenAI Agents SDK?
A) To deploy pre-trained models  
B) To create standalone AI models  
C) To perform only natural language processing tasks  
D) To build multi-agent AI applications for complex tasks  

**Explanation**: The OpenAI Agents SDK is a lightweight framework designed to orchestrate multiple AI agents to perform complex, multi-step tasks autonomously.  
**Answer**: D

---

### Q2. Which of the following are core primitives of the OpenAI Agents SDK?
A) APIs, Databases, Models, Tools  
B) Servers, Clients, Networks, Interfaces  
C) Prompts, Loops, Tasks, Outputs  
D) Agents, Handoffs, Guardrails, Sessions  

**Explanation**: The SDK is built around four core primitives: Agents (LLMs with instructions and tools), Handoffs (task delegation), Guardrails (input validation), and Sessions (conversation history management).  
**Answer**: D

---

### Q3. Why is the Agent class defined as a dataclass in the OpenAI Agents SDK?
A) To integrate with databases  
B) To reduce boilerplate code and improve readability  
C) To implement complex logic  
D) To slow down performance  

**Explanation**: Using a dataclass minimizes boilerplate code (e.g., `__init__`, `__repr__`) and provides type hints, making the Agent class cleaner and more readable.  
**Answer**: B

---

### Q4. What is the role of the `instructions` field in the Agent class?
A) Stores the list of tool calls  
B) Configures guardrails  
C) Specifies the system prompt or callable function to guide agent behavior  
D) Defines the output type of the agent  

**Explanation**: The `instructions` field defines how the agent behaves, either through a static system prompt or a callable function for dynamic prompts.  
**Answer**: C

---

### Q5. Why can the `instructions` field in the Agent class be set as a callable?
A) To restrict prompts to static strings  
B) To disable tool calls  
C) To bypass guardrails  
D) To generate dynamic prompts based on runtime context  

**Explanation**: A callable `instructions` field allows prompts to be dynamically generated based on context, user input, or external conditions.  
**Answer**: D

---

### Q6. What is the purpose of Handoffs in the OpenAI Agents SDK?
A) To execute tool calls  
B) To delegate tasks from one agent to another  
C) To validate inputs  
D) To format outputs  

**Explanation**: Handoffs enable an agent to transfer a task to another specialized agent when the task is outside its domain.  
**Answer**: B

---

### Q7. What is the primary role of Guardrails in the SDK?
A) To define agent tools  
B) To validate inputs and outputs for safety and compliance  
C) To modify agent outputs  
D) To store session history  

**Explanation**: Guardrails are safety checks that validate inputs and outputs to ensure agents operate within defined parameters.  
**Answer**: B

---

### Q8. What is the benefit of the Tracing & Observability feature in the SDK?
A) Generates input prompts automatically  
B) Visualizes and debugs agent workflows  
C) Defines agent tools  
D) Stores session data  

**Explanation**: Tracing allows developers to monitor, visualize, and debug agent actions, which is crucial for optimizing complex workflows.  
**Answer**: B

---

### Q9. What does the Sessions primitive do in the OpenAI Agents SDK?
A) Generates dynamic prompts  
B) Automatically manages conversation history across agent runs  
C) Executes tool calls  
D) Validates input data  

**Explanation**: Sessions eliminate manual state handling by automatically maintaining conversation history across multiple agent runs.  
**Answer**: B

---

### Q10. What makes the OpenAI Agents SDK a Python-first framework?
A) It is written in multiple languages  
B) It avoids Python type hints  
C) It requires no Python knowledge  
D) It leverages Python’s built-in features for agent orchestration  

**Explanation**: The SDK uses Python’s native features like dataclasses and type hints, reducing the need for new abstractions and making it intuitive for Python developers.  
**Answer**: D

---

### Q11. What is the significance of the `name` field in the Agent class?
A) Defines the output type  
B) Stores tool calls  
C) Configures guardrails  
D) Identifies the agent for debugging and tracing  

**Explanation**: The `name` field helps identify the agent in logs and tracing outputs, aiding debugging.  
**Answer**: D

---

### Q12. What is the role of the `output_type` field in the Agent class?
A) Defines the input format  
B) Stores tool calls  
C) Configures guardrails  
D) Specifies the expected type of the agent’s final output  

**Explanation**: The `output_type` field determines when the Agent Loop terminates by matching the output type.  
**Answer**: D

---

### Q13. What is the benefit of the SDK’s minimalist design?
A) Increases complexity  
B) Restricts flexibility  
C) Reduces the learning curve for developers  
D) Disables Python integration  

**Explanation**: The minimalist design with few primitives makes the SDK easy to learn and use.  
**Answer**: C

---

### Q14. What is a key feature of the Agent class?
A) It restricts tool usage  
B) It disables dynamic prompts  
C) It requires manual state management  
D) It supports instructions, tools, and output types  

**Explanation**: The Agent class is a container for instructions, tools, and output types, enabling flexible agent configuration.  
**Answer**: D

---

### Q15. How does the SDK support complex task coordination?
A) By restricting tasks to single agents  
B) By disabling tool calls  
C) By clearing session history  
D) Through handoffs and multi-agent workflows  

**Explanation**: Handoffs and multi-agent workflows enable the SDK to coordinate complex tasks efficiently.  
**Answer**: D

---

## Section 2: Key Features (Questions 16-30)

### Q16. What does the built-in Agent Loop in the SDK handle?
A) Database connections  
B) User authentication  
C) Model training  
D) Tool calls, result handling, and looping until final output  

**Explanation**: The Agent Loop automates sending prompts to the LLM, invoking tools, handling handoffs, and looping until a final output is produced.  
**Answer**: D

---

### Q17. How does the SDK support function tools?
A) By restricting tools to predefined APIs  
B) By requiring manual schema definitions  
C) By disabling tool usage  
D) By converting any Python function into a tool with automatic schema generation  

**Explanation**: The SDK uses Pydantic-powered validation to turn Python functions into tools with automatically generated schemas.  
**Answer**: D

---

### Q18. What is the benefit of the SDK’s interoperability feature?
A) It restricts usage to OpenAI models only  
B) It disables third-party model integration  
C) It requires custom APIs for each model  
D) It supports any model provider with Chat Completions API format  

**Explanation**: The SDK’s interoperability allows it to work with any model provider supporting the Chat Completions API.  
**Answer**: D

---

### Q19. What happens if a guardrail check fails during an agent run?
A) The agent continues running  
B) The output is reformatted  
C) The session history is cleared  
D) The workflow stops early with a GuardrailTripwireTriggered exception  

**Explanation**: Guardrails validate inputs, and if a check fails, a GuardrailTripwireTriggered exception halts the workflow.  
**Answer**: D

---

### Q20. What is the purpose of the `max_turns` parameter in the SDK?
A) To define the output type  
B) To configure session storage  
C) To limit the number of tool calls  
D) To set the maximum number of AI invocations in a workflow  

**Explanation**: `max_turns` limits the number of turns (AI invocations, including tool calls) to prevent infinite loops.  
**Answer**: D

---

### Q21. What does the `hooks` parameter do in the SDK’s run methods?
A) Defines agent tools  
B) Stores session history  
C) Generates input prompts  
D) Provides callbacks for lifecycle events  

**Explanation**: Hooks allow developers to receive callbacks for events like agent start, action, or completion for monitoring and debugging.  
**Answer**: D

---

### Q22. What is the role of the `previous_response_id` parameter?
A) To define the starting agent  
B) To validate guardrails  
C) To set the output type  
D) To skip passing previous turn input when using OpenAI Responses API  

**Explanation**: `previous_response_id` references prior responses, avoiding redundant input in the Responses API.  
**Answer**: D

---

### Q23. How does the SDK simplify multi-agent workflows?
A) By restricting workflows to single agents  
B) By requiring manual state management  
C) By disabling handoffs  
D) By enabling task delegation and coordination between multiple agents  

**Explanation**: Handoffs allow agents to delegate tasks, enabling complex, collaborative workflows.  
**Answer**: D

---

### Q24. What is the benefit of the Python-first design in the SDK?
A) It requires learning new abstractions  
B) It restricts usage to non-Python environments  
C) It avoids Python type hints  
D) It integrates seamlessly with Python’s native features  

**Explanation**: The Python-first design leverages Python’s built-in features, reducing the learning curve for developers.  
**Answer**: D

---

### Q25. What does the built-in tracing feature allow developers to do?
A) Train new models  
B) Define guardrails  
C) Store session data  
D) Visualize, debug, and monitor workflows  

**Explanation**: Tracing provides tools to visualize agent actions, debug issues, and monitor performance.  
**Answer**: D

---

### Q26. What is the benefit of automatic schema generation for tools?
A) It requires manual schema creation  
B) It disables tool usage  
C) It restricts tool flexibility  
D) It simplifies tool integration with Pydantic validation  

**Explanation**: Pydantic enables automatic schema generation and validation for tools created from Python functions.  
**Answer**: D

---

### Q27. How does the SDK handle conversation history?
A) By requiring manual state management  
B) By disabling history tracking  
C) By restricting session usage  
D) Through automatic session management  

**Explanation**: The Sessions primitive automatically manages conversation history across agent runs.  
**Answer**: D

---

### Q28. What is a turn in the context of the Agent Loop?
A) A single tool call  
B) A session update  
C) A guardrail check  
D) One AI invocation, including any tool calls  

**Explanation**: A turn is one AI invocation, which may include tool calls, in the Agent Loop.  
**Answer**: D

---

### Q29. How does the SDK reduce manual prompt engineering?
A) By requiring manual prompt creation  
B) By disabling prompts  
C) By restricting dynamic prompts  
D) By automating prompt handling in the Agent Loop  

**Explanation**: The Agent Loop automates prompt sending and result handling, reducing manual prompt engineering.  
**Answer**: D

---

### Q30. What is an example of a tool an agent might use in the SDK?
A) A database connection  
B) A user authentication module  
C) A model training script  
D) A web search function  

**Explanation**: Agents can use tools like web search or file retrieval, integrated via Python functions.  
**Answer**: D

---

## Section 3: Runner Methods (Questions 31-45)

### Q31. What is the primary difference between `run_sync` and `run_streamed` methods?
A) `run_sync` streams events, while `run_streamed` waits for final output  
B) Both methods are identical  
C) `run_streamed` disables tool calls  
D) `run_sync` waits for final output, while `run_streamed` streams events as they occur  

**Explanation**: `run_sync` blocks until the final output is ready, while `run_streamed` provides real-time event streaming.  
**Answer**: D

---

### Q32. In which scenario will `run_sync` NOT work?
A) When using OpenAI models  
B) When guardrails are disabled  
C) In a synchronous Python script  
D) In an async environment like FastAPI or Jupyter notebook  

**Explanation**: `run_sync` is a blocking call and cannot run in environments with an existing event loop.  
**Answer**: D

---

### Q33. What happens in the Agent Loop when a final output is produced?
A) The loop continues indefinitely  
B) The loop triggers a handoff  
C) The loop raises an exception  
D) The loop terminates  

**Explanation**: When an agent produces a final output of type `agent.output_type`, the Agent Loop stops.  
**Answer**: D

---

### Q34. What exception is raised if `max_turns` is exceeded in a workflow?
A) GuardrailTripwireTriggered  
B) OutputParserException  
C) TypeError  
D) MaxTurnsExceeded  

**Explanation**: If the number of turns exceeds `max_turns`, a `MaxTurnsExceeded` exception is raised.  
**Answer**: D

---

### Q35. When are guardrails applied in the Agent Loop?
A) For every agent’s input  
B) For the final output only  
C) For tool calls only  
D) Only for the first agent’s input  

**Explanation**: Guardrails are applied only to the initial agent’s input to validate it before processing.  
**Answer**: D

---

### Q36. What does the `run` method return in the OpenAI Agents SDK?
A) A list of tool calls  
B) A new agent instance  
C) A session object  
D) A RunResult containing inputs, guardrail results, and final output  

**Explanation**: The `run` method returns a `RunResult` with all inputs, guardrail results, and the final output.  
**Answer**: D

---

### Q37. What is the role of the `context` parameter in the `run_sync` method?
A) Defines the output format  
B) Specifies tool calls  
C) Stores previous responses  
D) Provides execution context for the agent  

**Explanation**: The `context` parameter supplies optional data or state for the agent during execution.  
**Answer**: D

---

### Q38. What does the `run_streamed` method return?
A) A RunResult with final output only  
B) A list of guardrail results  
C) A session history  
D) A RunResultStreaming object with a method to stream events  

**Explanation**: `run_streamed` returns a `RunResultStreaming` object for streaming events like tokens and tool calls.  
**Answer**: D

---

### Q39. What happens if a handoff occurs in the Agent Loop?
A) The loop terminates  
B) The loop raises an exception  
C) The loop skips tool calls  
D) The loop continues with a new agent  

**Explanation**: A handoff transfers control to a new agent, and the loop continues with that agent.  
**Answer**: D

---

### Q40. Which method should be used in an async environment like FastAPI?
A) `run_sync`  
B) Both `run` and `run_streamed`  
C) `run`  
D) `run_streamed`  

**Explanation**: `run` (async) and `run_streamed` are suitable for async environments, while `run_sync` is not.  
**Answer**: B

---

### Q41. Why is the `run` method defined as a classmethod?
A) To restrict access to instances  
B) To disable async functionality  
C) To limit tool calls  
D) To allow invocation without creating a Runner instance  

**Explanation**: As a classmethod, `run` can be called directly on the Runner class, simplifying usage.  
**Answer**: D

---

### Q42. What is the role of the `run_config` parameter?
A) Defines the agent’s output type  
B) Stores session history  
C) Triggers handoffs  
D) Specifies global settings for the agent run  

**Explanation**: `run_config` provides global configuration settings for the entire agent workflow.  
**Answer**: D

---

### Q43. What is the purpose of the `session` parameter in the run methods?
A) Defines tool calls  
B) Validates inputs  
C) Generates dynamic prompts  
D) Manages conversation history across runs  

**Explanation**: The `session` parameter enables automatic management of conversation history.  
**Answer**: D

---

### Q44. What is a common use case for the `run_streamed` method?
A) Batch processing of inputs  
B) Disabling tool calls  
C) Clearing session history  
D) Real-time applications needing event streaming  

**Explanation**: `run_streamed` is ideal for applications requiring real-time feedback, like live chat.  
**Answer**: D

---

### Q45. What happens if no final output is produced within `max_turns`?
A) The loop continues indefinitely  
B) A GuardrailTripwireTriggered exception is raised  
C) The session is cleared  
D) A MaxTurnsExceeded exception is raised  

**Explanation**: If `max_turns Streptomyces is exceeded without a final output, a `MaxTurnsExceeded` exception is raised.  
**Answer**: D

---

## Section 4: Exceptions and Error Handling (Questions 46-55)

### Q46. What exception is raised if a guardrail tripwire is triggered?
A) MaxTurnsExceeded  
B) OutputParserException  
C) TypeError  
D) GuardrailTripwireTriggered  

**Explanation**: A `GuardrailTripwireTriggered` exception is raised when a guardrail check fails, halting the workflow.  
**Answer**: D

---

### Q47. What causes a `MaxTurnsExceeded` exception?
A) Invalid input format  
B) Failed tool call  
C) Missing session object  
D) Exceeding the maximum number of allowed turns  

**Explanation**: This exception occurs when the workflow exceeds the `max_turns` limit.  
**Answer**: D

---

### Q48. What happens if an LLM output fails the declared `output_type` schema?
A) GuardrailTripwireTriggered  
B) MaxTurnsExceeded  
C) TypeError  
D) OutputParserException  

**Explanation**: An `OutputParserException` is raised when the LLM output does not match the expected `output_type` schema.  
**Answer**: D

---

### Q49. What happens if a tool call fails during an agent run?
A) The loop terminates with a final output  
B) A MaxTurnsExceeded exception is raised  
C) The session is cleared  
D) The loop continues after handling the failure  

**Explanation**: The Agent Loop handles tool call failures and continues unless a final output or exception occurs.  
**Answer**: D

---

### Q50. What happens if a tool call is not defined in the agent?
A) The loop terminates  
B) The loop skips the tool call  
C) The session is cleared  
D) An error is raised during execution  

**Explanation**: An invalid or undefined tool call raises an error (e.g., `ToolExecutionError`) during execution.  
**Answer**: D

---

### Q51. How does the SDK ensure safety in multi-agent systems?
A) By disabling handoffs  
B) By restricting tool usage  
C) By clearing session history  
D) Through guardrails that validate inputs  

**Explanation**: Guardrails validate inputs to ensure safe and compliant operation in multi-agent systems.  
**Answer**: D

---

### Q52. What is the significance of the `on_agent_action` hook?
A) It is called after tool invocation  
B) It terminates the agent loop  
C) It validates inputs  
D) It is called after agent reasoning but before tool invocation  

**Explanation**: The `on_agent_action` hook is triggered when the agent decides to take an action, before tool execution.  
**Answer**: D

---

### Q53. What is the role of the `on_agent_start` hook?
A) Called after tool invocation  
B) Called after the final output  
C) Called during guardrail validation  
D) Called when the agent begins processing  

**Explanation**: The `on_agent_start` hook is triggered when the agent starts its execution.  
**Answer**: D

---

### Q54. What is a common use case for the `on_agent_end` hook?
A) To validate inputs  
B) To trigger a handoff  
C) To define tool calls  
D) To log the final output of an agent  

**Explanation**: The `on_agent_end` hook is triggered when an agent completes, useful for logging or processing the output.  
**Answer**: D

---

### Q55. How does the SDK handle tool call results?
A) By ignoring them  
B) By terminating the loop  
C) By clearing the session  
D) By sending them back to the LLM in the Agent Loop  

**Explanation**: Tool call results are sent back to the LLM for further processing within the Agent Loop.  
**Answer**: D

---

## Section 5: APIs and Integration (Questions 56-65)

### Q56. What is the primary difference between the Chat Completions API and Responses API?
A) Chat Completions API supports tool calls, Responses API does not  
B) Chat Completions API is newer than Responses API  
C) Responses API is restricted to OpenAI models  
D) Responses API is more flexible, handling text completions, chat, and tool calls  

**Explanation**: The Responses API supports multiple tasks, making it more versatile than the Chat Completions API.  
**Answer**: D

---

### Q57. Which API does the OpenAI Agents SDK primarily integrate with?
A) Chat Completions API  
B) Embedding API  
C) Fine-Tuning API  
D) Responses API  

**Explanation**: The SDK is designed to work seamlessly with the Responses API for newer OpenAI models.  
**Answer**: D

---

### Q58. What does the Responses API support that the Chat Completions API does not?
A) Only chat messages  
B) Only text completions  
C) Only image generation  
D) Structured outputs and tool calls  

**Explanation**: The Responses API supports text completions, chat, structured outputs, and tool calls.  
**Answer**: D

---

### Q59. Which models are compatible with the OpenAI Agents SDK?
A) Only OpenAI models  
B) Only GPT-4.1  
C) Only Gemini models  
D) Any model supporting the Chat Completions API format  

**Explanation**: The SDK’s interoperability supports any model provider with the Chat Completions API format.  
**Answer**: D

---

### Q60. What is the benefit of using the `previous_response_id` with the Responses API?
A) It defines the agent’s instructions  
B) It disables guardrails  
C) It triggers a handoff  
D) It avoids redundant input from previous turns  

**Explanation**: `previous_response_id` references prior responses, reducing redundant input data.  
**Answer**: D

---

### Q61. What is a key feature of the Responses API compared to the Chat Completions API?
A) It only supports chat messages  
B) It is less flexible  
C) It restricts model usage  
D) It supports structured outputs and tool calls  

**Explanation**: The Responses API’s versatility enhances the SDK’s functionality for complex tasks.  
**Answer**: D

---

### Q62. How does the SDK support non-OpenAI models?
A) By restricting model usage  
B) By disabling third-party models  
C) By requiring custom integrations  
D) Through compatibility with the Chat Completions API format  

**Explanation**: The SDK supports any model provider with the Chat Completions API format.  
**Answer**: D

---

### Q63. What is a benefit of the SDK’s integration with the Responses API?
A) It restricts model usage  
B) It disables chat functionality  
C) It requires manual prompt engineering  
D) It supports structured outputs and tool calls  

**Explanation**: The Responses API enhances the SDK’s ability to handle structured outputs and tool calls.  
**Answer**: D

---

### Q64. What is the role of Pydantic in the SDK?
A) It restricts tool usage  
B) It disables tool calls  
C) It requires manual schema creation  
D) It provides automatic schema generation and validation for tools  

**Explanation**: Pydantic simplifies tool creation with automatic schema generation and validation.  
**Answer**: D

---

### Q65. How does the SDK support dynamic prompts?
A) By restricting prompts to static strings  
B) By disabling prompts  
C) By requiring manual prompt updates  
D) By allowing callable instructions for runtime generation  

**Explanation**: Callable instructions enable dynamic prompt generation based on runtime context.  
**Answer**: D

---

## Section 6: Practical Applications (Questions 66-75)

### Q66. Which industry can benefit from the OpenAI Agents SDK for real-time data retrieval?
A) Gaming  
B) Hardware manufacturing  
C) None of the above  
D) Customer support  

**Explanation**: The SDK enables AI assistants to pull real-time data (e.g., via web search) for customer support.  
**Answer**: D

---

### Q67. How can the SDK be used in legal research?
A) By restricting access to documents  
B) By disabling tool calls  
C) By limiting agent interactions  
D) By enabling agents to access internal documents via file search  

**Explanation**: The SDK supports file search tools for retrieving and processing internal documents.  
**Answer**: D

---

### Q68. What is a real-world application of multi-agent workflows?
A) Running a single agent for all tasks  
B) Disabling handoffs  
C) Restricting tool usage  
D) Coordinating research and customer support tasks between agents  

**Explanation**: Multi-agent workflows allow specialized agents to collaborate on tasks like research and support.  
**Answer**: D

---

### Q69. How does the SDK support finance applications?
A) By disabling data retrieval  
B) By restricting multi-agent workflows  
C) By disabling tracing  
D) By enabling agents to access financial data via tools  

**Explanation**: Agents can use tools like file search or APIs to process financial data.  
**Answer**: D

---

### Q70. What is a benefit of the SDK in customer support applications?
A) It restricts data access  
B) It disables multi-agent systems  
C) It requires manual state management  
D) It enables real-time data retrieval via web search  

**Explanation**: The SDK allows agents to access real-time data, enhancing customer support efficiency.  
**Answer**: D

---

### Q71. How does the SDK simplify complex task coordination?
A) By restricting tasks to single agents  
B) By disabling tool calls  
C) By clearing session history  
D) Through handoffs and multi-agent workflows  

**Explanation**: Handoffs and multi-agent workflows enable efficient task coordination.  
**Answer**: D

---

### Q72. What is a practical use case for the SDK in enterprises?
A) Disabling data integration  
B) Restricting tool usage  
C) Disabling debugging tools  
D) Integrating internal and external data for AI assistants  

**Explanation**: The SDK supports tools like web and file search for data integration in enterprises.  
**Answer**: D

---

### Q73. How does the SDK support real-time applications?
A) By disabling streaming  
B) By restricting tool calls  
C) By requiring manual output handling  
D) Through the `run_streamed` method for event streaming  

**Explanation**: `run_streamed` enables real-time event streaming for applications like live chat.  
**Answer**: D

---

### Q74. What is an example of a tool used in the SDK for enterprise applications?
A) A database connector  
B) A user authentication module  
C) A model training script  
D) A file search function  

**Explanation**: File search is a common tool for retrieving internal documents in enterprise applications.  
**Answer**: D

---

### Q75. How does the SDK reduce manual orchestration logic?
A) By requiring manual state management  
B) By disabling handoffs  
C) By restricting tool calls  
D) By automating agent coordination and task delegation  

**Explanation**: The SDK abstracts orchestration logic, automating agent coordination and task delegation.  
**Answer**: D

---

## Section 7: Community Feedback and Adoption (Questions 76-85)

### Q76. What indicates strong community adoption of the OpenAI Agents SDK?
A) Lack of GitHub stars  
B) No community contributions  
C) Restricted repository access  
D) Nearly 2,000 GitHub stars and numerous forks  

**Explanation**: The SDK’s GitHub repository has nearly 2,000 stars, showing robust community interest.  
**Answer**: D

---

### Q77. What do developers praise about the SDK’s ease of use?
A) Its complex abstractions  
B) Its lack of Python integration  
C) Its restriction to OpenAI models  
D) Its minimal abstractions and Python-first approach  

**Explanation**: Developers appreciate the SDK’s simple design and Python integration, reducing the learning curve.  
**Answer**: D

---

### Q78. How has the SDK impacted enterprise applications, according to reviews?
A) By restricting data integration  
B) By disabling multi-agent workflows  
C) By limiting debugging tools  
D) By enabling integration of internal and external data  

**Explanation**: Enterprises note that the SDK simplifies data integration for AI assistants.  
**Answer**: D

---

### Q79. What is a benefit of the SDK’s open-source nature?
A) It restricts community contributions  
B) It limits access to the codebase  
C) It disables third-party integrations  
D) It allows community-driven enhancements and examples  

**Explanation**: The open-source nature encourages community contributions and shared examples.  
**Answer**: D

---

### Q80. What do beginner guides say about the SDK?
A) It has a steep learning curve  
B) It restricts flexibility  
C) It disables Python integration  
D) It simplifies complex multi-agent setups  

**Explanation**: Beginner guides highlight the SDK’s ability to make multi-agent systems accessible.  
**Answer**: D

---

### Q81. What do developers say about the SDK’s handoff feature?
A) It complicates workflows  
B) It disables multi-agent systems  
C) It restricts tool usage  
D) It streamlines task delegation between agents  

**Explanation**: Developers praise handoffs for enabling seamless task delegation in multi-agent systems.  
**Answer**: D

---

### Q82. What is a key advantage of the SDK’s tracing tools for enterprises?
A) They disable debugging  
B) They restrict agent interactions  
C) They limit tool usage  
D) They provide clear, actionable feedback for workflow optimization  

**Explanation**: Tracing tools help enterprises optimize workflows with actionable feedback.  
**Answer**: D

---

### Q83. What is a sign of the SDK’s open-source success?
A) Lack of community contributions  
B) Restricted repository access  
C) No shared examples  
D) Active community sharing of examples and enhancements  

**Explanation**: The SDK’s community actively shares examples and suggests improvements.  
**Answer**: D

---

### Q84. How does the SDK support debugging complex workflows?
A) By disabling tracing  
B) By restricting handoffs  
C) By requiring manual logging  
D) Through built-in tracing and observability tools  

**Explanation**: Tracing tools allow visualization and debugging of complex workflows.  
**Answer**: D

---

### Q85. What is the community feedback on the SDK’s tracing feature?
A) It complicates debugging  
B) It restricts agent actions  
C) It disables tool calls  
D) It is a game-changer for visualizing and debugging interactions  

**Explanation**: Developers praise tracing for simplifying workflow visualization and debugging.  
**Answer**: D

---

## Section 8: Advanced Topics (Questions 86-100)

### Q86. What are generics in Python, as used in the SDK?
A) Fixed types for specific functions  
B) Database connectors  
C) Error handlers  
D) Flexible types for reusable code  

**Explanation**: Generics (e.g., `TypeVar`) allow flexible typing for reusable code, like `TContext` in the SDK.  
**Answer**: D

---

### Q87. Why is `TContext` used as a generic type in the SDK?
A) To restrict context to a single type  
B) To disable context usage  
C) To define tool calls  
D) To allow flexible context types for different use cases  

**Explanation**: `TContext` enables the Agent and Runner to handle various context types flexibly.  
**Answer**: D

---

### Q88. What is the benefit of the SDK’s evaluation tools?
A) They disable debugging  
B) They restrict agent interactions  
C) They disable tool calls  
D) They allow performance assessment and model fine-tuning  

**Explanation**: Evaluation tools help assess workflow performance and fine-tune models.  
**Answer**: D

---

### Q89. How does the SDK support model fine-tuning?
A) By disabling evaluation tools  
B) By restricting model usage  
C) By requiring manual fine-tuning  
D) Through built-in evaluation and fine-tuning tools  

**Explanation**: The SDK includes tools for evaluating and fine-tuning models to improve performance.  
**Answer**: D

---

### Q90. What is the significance of the `RunResult` object?
A) It stores tool definitions  
B) It defines the agent’s instructions  
C) It triggers handoffs  
D) It contains inputs, guardrail results, and the final output  

**Explanation**: The `RunResult` object encapsulates all inputs, guardrail results, and the final output.  
**Answer**: D

---

### Q91. What is the benefit of the SDK’s lightweight design?
A) It increases complexity  
B) It restricts flexibility  
C) It disables Python integration  
D) It reduces setup time and learning curve  

**Explanation**: The lightweight design with few primitives simplifies setup and learning.  
**Answer**: D

---

### Q92. What is a key feature of the SDK’s function tools?
A) They require manual schema creation  
B) They disable tool calls  
C) They restrict tool flexibility  
D) They support automatic schema generation with Pydantic  

**Explanation**: Pydantic simplifies tool creation with automatic schema generation and validation.  
**Answer**: D

---

### Q93. What happens if an agent delegates a task to another agent?
A) The loop terminates  
B) A GuardrailTripwireTriggered exception is raised  
C) The session is cleared  
D) A handoff occurs, and the loop continues with the new agent  

**Explanation**: Handoffs allow seamless task delegation, with the loop continuing under the new agent.  
**Answer**: D

---

### Q94. How does the SDK handle complex task coordination?
A) By restricting tasks to single agents  
B) By disabling tool calls  
C) By clearing session history  
D) Through handoffs and multi-agent workflows  

**Explanation**: Handoffs and multi-agent workflows enable efficient task coordination.  
**Answer**: D

---

### Q95. What is the benefit of the SDK’s compatibility with non-OpenAI models?
A) It restricts model usage  
B) It disables tool calls  
C) It requires manual API integration  
D) It allows flexibility in choosing model providers  

**Explanation**: Compatibility with the Chat Completions API format allows use of various model providers.  
**Answer**: D

---

### Q96. What is the significance of the `RunResultStreaming` object?
A) It stores session history  
B) It defines tool calls  
C) It validates inputs  
D) It provides a method to stream events in real-time  

**Explanation**: `RunResultStreaming` enables real-time streaming of events like tokens and tool calls.  
**Answer**: D

---

### Q97. How does tracing help in debugging agent workflows?
A) By disabling agent actions  
B) By restricting tool calls  
C) By clearing session history  
D) By visualizing the flow of actions and interactions  

**Explanation**: Tracing provides a visual representation of agent actions for debugging.  
**Answer**: D

---

### Q98. What is a limitation of the `run_sync` method?
A) It supports async environments  
B) It disables tool calls  
C) It restricts guardrail usage  
D) It cannot run in environments with an existing event loop  

**Explanation**: `run_sync` is a blocking call and fails in async environments like FastAPI.  
**Answer**: D

---

### Q99. What is a benefit of the SDK’s open-source nature?
A) It restricts community contributions  
B) It limits access to the codebase  
C) It disables third-party integrations  
D) It allows community-driven enhancements and examples  

**Explanation**: The open-source nature encourages community contributions and shared examples.  
**Answer**: D

---

### Q100. What is the role of the Runner class in the SDK?
A) To define agent instructions  
B) To store session history  
C) To generate tool schemas  
D) To orchestrate and control agent workflows  

**Explanation**: The Runner class manages the execution of agent workflows, controlling the loop, safety, and results.  
**Answer**: D

---

## Additional Questions from Supplemental Set

### Q101. What type of object does the `model_settings` field expect?
A) dict  
B) str  
C) BaseModel  
D) ModelSettings  

**Explanation**: The `model_settings` field expects a `ModelSettings` object, which is used to configure the model parameters for the agent.  
**Answer**: D

---

### Q102. Which field is used to describe an agent when it's used as a handoff target?
A) name  
B) instructions  
C) description  
D) handoff_description  

**Explanation**: The `handoff_description` field provides a description of the agent when it is used as a target for task delegation in a handoff.  
**Answer**: D

---

### Q103. What is the default model used by an Agent if no model is specified?
```python
agent = Agent(name="Test")  # What model will this use?
```
A) "gpt-3.5-turbo"  
B) "gpt-4"  
C) "gpt-4o-mini"  
D) "gpt-4o"  

**Explanation**: If no model is specified, the Agent defaults to using the "gpt-4o" model.  
**Answer**: D

---

### Q104. Which of the following is NOT a valid type for the `instructions` parameter?
A) str  
B) Callable[[RunContextWrapper[TContext], Agent[TContext]], MaybeAwaitable[str]]  
C) None  
D) list[str]  

**Explanation**: The `instructions` parameter can be a string, a callable returning a string, or None, but a list of strings is not a valid type.  
**Answer**: D

---

### Q105. What is the default value for the `instructions` parameter in the Agent class?
A) "You are a helpful assistant"  
B) An empty string ""  
C) A default system prompt  
D) None  

**Explanation**: The `instructions` parameter defaults to None if not specified, allowing for optional instructions or dynamic generation via callables.  
**Answer**: D

---

### Q106. Which parameter is required when creating an Agent instance?
```python
agent = Agent(
    # Options: name, instructions, model, handoffs
)
```
A) instructions  
B) model  
C) handoffs  
D) name  

**Explanation**: The `name` parameter is required to create an Agent instance, as it uniquely identifies the agent for debugging and tracing.  
**Answer**: D

---

### Q107. You have an orchestrator agent that uses 5 specialist agents. If `translation_agent` hits a temporary API rate limit and fails, with instructions:
> “If any translation fails, try an alternative approach”
What happens to the orchestrator's execution context?
A) All the specialist agents share the same execution context, so the failure affects all of them  
B) The failed specialist automatically retries 3 times before the orchestrator sees the failure  
C) Orchestrator immediately fails with the specialist's exception, and all pending tool calls are cancelled  
D) Orchestrator receives the exception as tool output, can handle it in its reasoning & continues with others  

**Explanation**: The orchestrator receives the exception as part of the tool output, allowing it to reason and proceed with alternative approaches or other agents.  
**Answer**: D

---

### Q108. Which of the following is a valid use of `FunctionTool` without decorators?
A) It only works for sync functions  
B) You don’t need to validate input  
C) You cannot use FunctionTool without `@function_tool`  
D) You must define a Pydantic schema, async function, and manually create the tool object  

**Explanation**: To use `FunctionTool` without decorators, you need a Pydantic schema for validation, an async function, and manual creation of the tool object.  
**Answer**: D

---

### Q109. Which field is used to describe an agent when it's used as a handoff target?
A) name  
B) instructions  
C) description  
D) handoff_description  

**Explanation**: The `handoff_description` field provides a description of the agent when it is used as a target for task delegation in a handoff.  
**Answer**: D

---

### Q110. What type of object does the `model_settings` field expect?
A) dict  
B) str  
C) BaseModel  
D) ModelSettings  

**Explanation**: The `model_settings` field expects a `ModelSettings` object, which is used to configure the model parameters for the agent.  
**Answer**: D

---

### Q111. Which parameter controls the agent's output format to return structured data instead of plain text?
A) return_type  
B) output_format  
C) response_format  
D) output_type  

**Explanation**: The `output_type` parameter specifies the expected format of the agent’s output, enabling structured data instead of plain text.  
**Answer**: D

---

### Q112. What is the default factory for the `tools` field?
```bash
class Agent(
    name: str,
    handoff_description: str | None = None,
    tools: list[Tool] = list,
```

A) []  
B) list()  
C) lambda: []  
D) list  

**Explanation**: The `tools` field uses `list` as its default factory to initialize an empty list of tools.  
**Answer**: D

---

### Q113. The `on_tool_end` hook is useful for:
A) Starting a new agent  
B) Skipping tool usage  
C) Deleting the agent  
D) Tracking the completion of a tool's execution  

**Explanation**: The `on_tool_end` hook is triggered after a tool’s execution completes, useful for tracking or logging the results.  
**Answer**: D

---

### Q114. Which stage is associated with finalizing logs or cleanup tasks?
A) Initialization  
B) Execution  
C) Handoff  
D) Completion/Termination  

**Explanation**: The Completion/Termination stage is where final tasks like logging or cleanup are performed after the agent finishes its work.  
**Answer**: D

---

### Q115. What happens during the `on_handoff` hook?
A) The agent deletes its logs  
B) The agent restarts its task  
C) The agent terminates immediately  
D) The agent transfers control to another agent  

**Explanation**: The `on_handoff` hook is triggered when an agent delegates a task to another agent, transferring control.  
**Answer**: D

---

### Q116. During which lifecycle stage would you typically perform initial logging?
A) Handoff  
B) Termination  
C) Initialization/Activation  
D) Execution/Processing  

**Explanation**: Initial logging typically occurs during the Execution/Processing stage, as the agent begins processing tasks.  
**Answer**: D

---

### Q117. Which hook allows you to monitor when an agent begins using an external tool?
A) on_end  
B) on_handoff  
C) on_start  
D) on_tool_start  

**Explanation**: The `on_tool_start` hook is triggered when an agent starts using an external tool, allowing monitoring of tool usage.  
**Answer**: D

---

### Q118. Which hook is triggered when an agent is first activated?
A) on_tool_start  
B) on_handoff  
C) on_end  
D) on_start  

**Explanation**: The `on_start` hook is triggered when an agent is first activated, marking the beginning of its lifecycle.  
**Answer**: D

---

### Q119. What is the primary purpose of an agent's lifecycle?
A) To limit the agent's functionality  
B) To reduce the agent's interaction with tools  
C) To delete the agent after execution  
D) To provide a structured sequence of stages from activation to task completion  

**Explanation**: An agent’s lifecycle provides a structured sequence of stages (activation, processing, handoff, termination) to manage its execution.  
**Answer**: D

---
