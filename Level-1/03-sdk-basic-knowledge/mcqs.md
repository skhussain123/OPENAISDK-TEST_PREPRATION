# MCQs on OpenAI Agents SDK for Agentic AI Development
## Questions

**Q1. What is the main purpose of the OpenAI Agents SDK?**  
a) To generate images for AI applications  
b) To build and orchestrate agentic AI systems with multiple agents (correct)  
c) To train new language models  
d) To simplify hardware management for AI  

**Explanation**: The OpenAI Agents SDK is designed to create agentic AI systems where multiple agents work together on complex, multi-step tasks autonomously.

---

**Q2. Which of the following is a core primitive of the OpenAI Agents SDK?**  
a) Image processing  
b) Handoffs (correct)  
c) Model training  
d) Data storage  

**Explanation**: Handoffs, which allow task delegation between agents, are one of the four core primitives (Agents, Handoffs, Guardrails, Tracing & Observability).

---

**Q3. What does the "Agents" primitive in the SDK refer to?**  
a) Tools for data analysis  
b) Preconfigured LLMs with instructions and tool access (correct)  
c) Hardware components for AI systems  
d) User interface designs  

**Explanation**: Agents are language models preconfigured with instructions, tools, and safety guardrails to generate responses and make decisions.

---

**Q4. What is the role of Guardrails in the OpenAI Agents SDK?**  
a) To increase response length  
b) To validate inputs and outputs for safety (correct)  
c) To generate code automatically  
d) To reduce context size  

**Explanation**: Guardrails are built-in safety checks that ensure agents operate within defined parameters, reducing risks.

---

**Q5. How does the Tracing & Observability feature help developers?**  
a) It trains new AI models  
b) It allows visualization and debugging of agent workflows (correct)  
c) It simplifies user interface design  
d) It eliminates the need for tools  

**Explanation**: Tracing & Observability enables developers to monitor and debug complex agent workflows, improving performance.

---

**Q6. Why is the OpenAI Agents SDK considered simple for developers?**  
a) It requires advanced Python knowledge  
b) It has a minimalist design with few abstractions (correct)  
c) It avoids Python integration  
d) It focuses on hardware optimization  

**Explanation**: The SDK’s minimalist design with few abstractions makes it approachable for both new and experienced developers.

---

**Q7. What is a key feature of the OpenAI Agents SDK’s Python-first design?**  
a) It supports only non-Python languages  
b) It integrates naturally with Python for easy setup (correct)  
c) It requires complex setup processes  
d) It avoids tool integration  

**Explanation**: The Python-first design allows developers to quickly set up agents and tools using familiar Python workflows.

---

**Q8. What happens in the built-in agent loop of the OpenAI Agents SDK?**  
a) It trains the model repeatedly  
b) It sends prompts, invokes tools, handles handoffs, and repeats until output (correct)  
c) It generates images automatically  
d) It reduces context size  

**Explanation**: The agent loop sends prompts to the LLM, checks for tool invocation, handles handoffs, and repeats until a final output is produced.

---

**Q9. Which feature allows the OpenAI Agents SDK to work with non-OpenAI models?**  
a) Image processing compatibility  
b) Interoperability with Chat Completions API format (correct)  
c) Hardware optimization  
d) Built-in model training  

**Explanation**: The SDK’s interoperability allows it to work with any model provider supporting the Chat Completions API format.

---

**Q10. What is a real-world application of the OpenAI Agents SDK?**  
a) Generating random text  
b) Building AI-powered assistants for customer support (correct)  
c) Creating hardware designs  
d) Simplifying database management  

**Explanation**: Enterprises use the SDK to build assistants for industries like customer support, legal research, and finance.

---

**Q11. Why is the Agent class defined as a dataclass in the OpenAI Agents SDK?**  
a) To increase response length  
b) To simplify data structure management and initialization (correct)  
c) To reduce tool usage  
d) To eliminate tracing features  

**Explanation**: Using a dataclass simplifies the Agent’s data structure, making initialization and management easier for developers.

---

**Q12. Why can the system prompt in the Agent class be set as a callable?**  
a) To dynamically generate instructions based on context (correct)  
b) To reduce context size  
c) To avoid tool integration  
d) To simplify output formatting  

**Explanation**: A callable system prompt allows dynamic instruction generation, enhancing flexibility for agent behavior.

---

**Q13. Why is the user prompt passed as a parameter in the Runner class’s run method?**  
a) To limit tool access  
b) To allow flexible, runtime-specific user input (correct)  
c) To reduce tracing capabilities  
d) To simplify guardrails  

**Explanation**: Passing the user prompt at runtime allows the Runner to handle specific user inputs dynamically.

---

**Q14. What is the purpose of the Runner class in the OpenAI Agents SDK?**  
a) To train new models  
b) To orchestrate agent execution and manage workflows (correct)  
c) To generate images  
d) To reduce context size  

**Explanation**: The Runner class manages the execution of agents, coordinating prompts, tools, and handoffs.

---

**Q15. What are generics in Python, as used in the OpenAI Agents SDK’s TContext?**  
a) Tools for image processing  
b) Type hints for flexible, reusable code (correct)  
c) Methods to reduce context size  
d) Built-in safety checks  

**Explanation**: Generics allow type hints for flexible, reusable code, used in TContext to define adaptable context types.

---

**Q16. How does the OpenAI Agents SDK simplify multi-agent workflows?**  
a) By eliminating tool usage  
b) By enabling task handoffs between specialized agents (correct)  
c) By reducing Python integration  
d) By increasing abstractions  

**Explanation**: Handoffs allow tasks to be delegated between specialized agents, streamlining complex workflows.

---

**Q17. What makes the OpenAI Agents SDK suitable for newcomers?**  
a) Its complex abstractions  
b) Its low learning curve and minimal design (correct)  
c) Its focus on hardware optimization  
d) Its lack of tracing tools  

**Explanation**: The SDK’s minimal design and low learning curve make it accessible for newcomers.

---

**Q18. Which feature helps enterprises integrate internal data with real-time external information?**  
a) Image generation tools  
b) Web and file search integration (correct)  
c) Model training capabilities  
d) Hardware optimization  

**Explanation**: Web and file search tools allow agents to pull real-time external data and internal documents.

---

**Q19. What is a benefit of the SDK’s tracing capabilities?**  
a) They reduce the need for tools  
b) They help developers debug and optimize workflows (correct)  
c) They increase context size  
d) They simplify model training  

**Explanation**: Tracing capabilities allow visualization and debugging of agent actions, improving workflow optimization.

---

**Q20. Why do developers praise the OpenAI Agents SDK’s Python-first approach?**  
a) It requires complex setup  
b) It allows quick setup of agents and tools (correct)  
c) It avoids Python integration  
d) It focuses on non-Python languages  

**Explanation**: The Python-first design enables quick agent and tool setup, praised for its ease of use.

---

**Q21. What is a key advantage of the SDK’s handoff feature?**  
a) It reduces response accuracy  
b) It allows seamless task delegation between agents (correct)  
c) It eliminates the need for guardrails  
d) It increases context size  

**Explanation**: Handoffs enable agents to delegate tasks, improving efficiency in multi-agent systems.

---

**Q22. How does the SDK support complex systems in enterprises?**  
a) By avoiding tool integration  
b) By enabling agents to handle specialized tasks collaboratively (correct)  
c) By reducing Python compatibility  
d) By increasing abstractions  

**Explanation**: The SDK allows agents to collaborate on specialized tasks, supporting complex enterprise systems.

---

**Q23. What is the community response to the OpenAI Agents SDK, based on early reviews?**  
a) It has low interest with few GitHub stars  
b) It has nearly 2,000 GitHub stars and active contributions (correct)  
c) It is criticized for complexity  
d) It lacks community support  

**Explanation**: The SDK has nearly 2,000 GitHub stars and active community contributions, indicating strong interest.

---

**Q24. Why is the SDK considered a game-changer for enterprise AI?**  
a) It simplifies hardware management  
b) It reduces manual prompt engineering (correct)  
c) It avoids tool usage  
d) It increases learning curve  

**Explanation**: By abstracting orchestration logic, the SDK reduces manual prompt engineering, making AI development easier.

---

**Q25. Which feature allows developers to convert Python functions into callable tools?**  
a) Guardrails  
b) Python-first design (correct)  
c) Tracing capabilities  
d) Handoffs  

**Explanation**: The Python-first design allows developers to turn Python functions into tools for agents.

---

**Q26. What is a benefit of the SDK’s interoperability with the Chat Completions API?**  
a) It limits model compatibility  
b) It allows use with any compatible model provider (correct)  
c) It reduces tool access  
d) It increases context size  

**Explanation**: Interoperability enables the SDK to work with any model supporting the Chat Completions API format.

---

**Q27. How does the SDK make debugging easier for developers?**  
a) By eliminating tools  
b) Through integrated tracing and observability (correct)  
c) By increasing abstractions  
d) By reducing Python integration  

**Explanation**: Tracing and observability features help developers visualize and debug agent workflows.

---

**Q28. What type of tasks can agents built with the SDK perform?**  
a) Only image generation tasks  
b) Multi-step tasks like research and customer support (correct)  
c) Only model training tasks  
d) Only hardware optimization tasks  

**Explanation**: Agents can handle complex, multi-step tasks like research and customer support.

---

**Q29. Why is the OpenAI Agents SDK described as lightweight?**  
a) It requires heavy hardware resources  
b) It has few abstractions and a simple design (correct)  
c) It avoids Python integration  
d) It lacks tool support  

**Explanation**: The SDK’s minimal abstractions and simple design make it lightweight and easy to use.

---

**Q30. What is a key reason enterprises are adopting the OpenAI Agents SDK?**  
a) It simplifies model training  
b) It enables autonomous, action-oriented AI systems (correct)  
c) It reduces community contributions  
d) It increases manual prompt engineering  

**Explanation**: The SDK enables autonomous, action-oriented systems, making it valuable for enterprise applications.

# OpenAI Agents SDK 100 MCQs for Exam Preparation
## Section 1: Core Concepts (Questions 1-15)

1. **What is the primary purpose of the OpenAI Agents SDK?**  
   A) To create standalone AI models  
   B) To build multi-agent AI applications for complex tasks  
   C) To perform only natural language processing tasks  
   D) To deploy pre-trained models  
   **Answer**: B) To build multi-agent AI applications for complex tasks  
   **Explanation**: The OpenAI Agents SDK is a lightweight framework designed to orchestrate multiple AI agents to perform complex, multi-step tasks autonomously.

2. **Which of the following are core primitives of the OpenAI Agents SDK?**  
   A) APIs, Databases, Models, Tools  
   B) Agents, Handoffs, Guardrails, Sessions  
   C) Prompts, Loops, Tasks, Outputs  
   D) Servers, Clients, Networks, Interfaces  
   **Answer**: B) Agents, Handoffs, Guardrails, Sessions  
   **Explanation**: The SDK is built around four core primitives: Agents (LLMs with instructions and tools), Handoffs (task delegation), Guardrails (input validation), and Sessions (conversation history management).

3. **Why is the Agent class defined as a dataclass in the OpenAI Agents SDK?**  
   A) To implement complex logic  
   B) To reduce boilerplate code and improve readability  
   C) To slow down performance  
   D) To integrate with databases  
   **Answer**: B) To reduce boilerplate code and improve readability  
   **Explanation**: Using a dataclass minimizes boilerplate code (e.g., `__init__`, `__repr__`) and provides type hints, making the Agent class cleaner and more readable.

4. **What is the role of the `instructions` field in the Agent class?**  
   A) Defines the output type of the agent  
   B) Specifies the system prompt or callable function to guide agent behavior  
   C) Stores the list of tool calls  
   D) Configures guardrails  
   **Answer**: B) Specifies the system prompt or callable function to guide agent behavior  
   **Explanation**: The `instructions` field defines how the agent behaves, either through a static system prompt or a callable function for dynamic prompts.

5. **Why can the `instructions` field in the Agent class be set as a callable?**  
   A) To restrict prompts to static strings  
   B) To generate dynamic prompts based on runtime context  
   C) To disable tool calls  
   D) To bypass guardrails  
   **Answer**: B) To generate dynamic prompts based on runtime context  
   **Explanation**: A callable `instructions` field allows prompts to be dynamically generated based on context, user input, or external conditions.

6. **What is the purpose of Handoffs in the OpenAI Agents SDK?**  
   A) To execute tool calls  
   B) To delegate tasks from one agent to another  
   C) To validate inputs  
   D) To format outputs  
   **Answer**: B) To delegate tasks from one agent to another  
   **Explanation**: Handoffs enable an agent to transfer a task to another specialized agent when the task is outside its domain.

7. **What is the primary role of Guardrails in the SDK?**  
   A) To modify agent outputs  
   B) To validate inputs and outputs for safety and compliance  
   C) To define agent tools  
   D) To store session history  
   **Answer**: B) To validate inputs and outputs for safety and compliance  
   **Explanation**: Guardrails are safety checks that validate inputs and outputs to ensure agents operate within defined parameters.

8. **What is the benefit of the Tracing & Observability feature in the SDK?**  
   A) Generates input prompts automatically  
   B) Visualizes and debugs agent workflows  
   C) Defines agent tools  
   D) Stores session data  
   **Answer**: B) Visualizes and debugs agent workflows  
   **Explanation**: Tracing allows developers to monitor, visualize, and debug agent actions, which is crucial for optimizing complex workflows.

9. **What does the Sessions primitive do in the OpenAI Agents SDK?**  
   A) Executes tool calls  
   B) Automatically manages conversation history across agent runs  
   C) Validates input data  
   D) Generates dynamic prompts  
   **Answer**: B) Automatically manages conversation history across agent runs  
   **Explanation**: Sessions eliminate manual state handling by automatically maintaining conversation history across multiple agent runs.

10. **What makes the OpenAI Agents SDK a Python-first framework?**  
    A) It requires no Python knowledge  
    B) It leverages Python’s built-in features for agent orchestration  
    C) It is written in multiple languages  
    D) It avoids Python type hints  
    **Answer**: B) It leverages Python’s built-in features for agent orchestration  
    **Explanation**: The SDK uses Python’s native features like dataclasses and type hints, reducing the need for new abstractions and making it intuitive for Python developers.

11. **What is the significance of the `name` field in the Agent class?**  
    A) Defines the output type  
    B) Identifies the agent for debugging and tracing  
    C) Stores tool calls  
    D) Configures guardrails  
    **Answer**: B) Identifies the agent for debugging and tracing  
    **Explanation**: The `name` field helps identify the agent in logs and tracing outputs, aiding debugging.

12. **What is the role of the `output_type` field in the Agent class?**  
    A) Defines the input format  
    B) Specifies the expected type of the agent’s final output  
    C) Stores tool calls  
    D) Configures guardrails  
    **Answer**: B) Specifies the expected type of the agent’s final output  
    **Explanation**: The `output_type` field determines when the Agent Loop terminates by matching the output type.

13. **What is the benefit of the SDK’s minimalist design?**  
    A) Increases complexity  
    B) Reduces the learning curve for developers  
    C) Restricts flexibility  
    D) Disables Python integration  
    **Answer**: B) Reduces the learning curve for developers  
    **Explanation**: The minimalist design with few primitives makes the SDK easy to learn and use.

14. **What is a key feature of the Agent class?**  
    A) It restricts tool usage  
    B) It supports instructions, tools, and output types  
    C) It disables dynamic prompts  
    D) It requires manual state management  
    **Answer**: B) It supports instructions, tools, and output types  
    **Explanation**: The Agent class is a container for instructions, tools, and output types, enabling flexible agent configuration.

15. **How does the SDK support complex task coordination?**  
    A) By restricting tasks to single agents  
    B) Through handoffs and multi-agent workflows  
    C) By disabling tool calls  
    D) By clearing session history  
    **Answer**: B) Through handoffs and multi-agent workflows  
    **Explanation**: Handoffs and multi-agent workflows enable the SDK to coordinate complex tasks efficiently.

## Section 2: Key Features (Questions 16-30)

16. **What does the built-in Agent Loop in the SDK handle?**  
    A) Database connections  
    B) Tool calls, result handling, and looping until final output  
    C) User authentication  
    D) Model training  
    **Answer**: B) Tool calls, result handling, and looping until final output  
    **Explanation**: The Agent Loop automates sending prompts to the LLM, invoking tools, handling handoffs, and looping until a final output is produced.

17. **How does the SDK support function tools?**  
    A) By restricting tools to predefined APIs  
    B) By converting any Python function into a tool with automatic schema generation  
    C) By requiring manual schema definitions  
    D) By disabling tool usage  
    **Answer**: B) By converting any Python function into a tool with automatic schema generation  
    **Explanation**: The SDK uses Pydantic-powered validation to turn Python functions into tools with automatically generated schemas.

18. **What is the benefit of the SDK’s interoperability feature?**  
    A) It restricts usage to OpenAI models only  
    B) It supports any model provider with Chat Completions API format  
    C) It disables third-party model integration  
    D) It requires custom APIs for each model  
    **Answer**: B) It supports any model provider with Chat Completions API format  
    **Explanation**: The SDK’s interoperability allows it to work with any model provider supporting the Chat Completions API.

19. **What happens if a guardrail check fails during an agent run?**  
    A) The agent continues running  
    B) The workflow stops early with a GuardrailTripwireTriggered exception  
    C) The output is reformatted  
    D) The session history is cleared  
    **Answer**: B) The workflow stops early with a GuardrailTripwireTriggered exception  
    **Explanation**: Guardrails validate inputs, and if a check fails, a GuardrailTripwireTriggered exception halts the workflow.

20. **What is the purpose of the `max_turns` parameter in the SDK?**  
    A) To limit the number of tool calls  
    B) To set the maximum number of AI invocations in a workflow  
    C) To define the output type  
    D) To configure session storage  
    **Answer**: B) To set the maximum number of AI invocations in a workflow  
    **Explanation**: `max_turns` limits the number of turns (AI invocations, including tool calls) to prevent infinite loops.

21. **What does the `hooks` parameter do in the SDK’s run methods?**  
    A) Defines agent tools  
    B) Provides callbacks for lifecycle events  
    C) Stores session history  
    D) Generates input prompts  
    **Answer**: B) Provides callbacks for lifecycle events  
    **Explanation**: Hooks allow developers to receive callbacks for events like agent start, action, or completion for monitoring and debugging.

22. **What is the role of the `previous_response_id` parameter?**  
    A) To define the starting agent  
    B) To skip passing previous turn input when using OpenAI Responses API  
    C) To validate guardrails  
    D) To set the output type  
    **Answer**: B) To skip passing previous turn input when using OpenAI Responses API  
    **Explanation**: `previous_response_id` references prior responses, avoiding redundant input in the Responses API.

23. **How does the SDK simplify multi-agent workflows?**  
    A) By restricting workflows to single agents  
    B) By enabling task delegation and coordination between multiple agents  
    C) By disabling handoffs  
    D) By requiring manual state management  
    **Answer**: B) By enabling task delegation and coordination between multiple agents  
    **Explanation**: Handoffs allow agents to delegate tasks, enabling complex, collaborative workflows.

24. **What is the benefit of the Python-first design in the SDK?**  
    A) It requires learning new abstractions  
    B) It integrates seamlessly with Python’s native features  
    C) It avoids Python type hints  
    D) It restricts usage to non-Python environments  
    **Answer**: B) It integrates seamlessly with Python’s native features  
    **Explanation**: The Python-first design leverages Python’s built-in features, reducing the learning curve for developers.

25. **What does the built-in tracing feature allow developers to do?**  
    A) Train new models  
    B) Visualize, debug, and monitor workflows  
    C) Define guardrails  
    D) Store session data  
    **Answer**: B) Visualize, debug, and monitor workflows  
    **Explanation**: Tracing provides tools to visualize agent actions, debug issues, and monitor performance.

26. **What is the benefit of automatic schema generation for tools?**  
    A) It requires manual schema creation  
    B) It simplifies tool integration with Pydantic validation  
    C) It disables tool usage  
    D) It restricts tool flexibility  
    **Answer**: B) It simplifies tool integration with Pydantic validation  
    **Explanation**: Pydantic enables automatic schema generation and validation for tools created from Python functions.

27. **How does the SDK handle conversation history?**  
    A) By requiring manual state management  
    B) Through automatic session management  
    C) By disabling history tracking  
    D) By restricting session usage  
    **Answer**: B) Through automatic session management  
    **Explanation**: The Sessions primitive automatically manages conversation history across agent runs.

28. **What is a turn in the context of the Agent Loop?**  
    A) A single tool call  
    B) One AI invocation, including any tool calls  
    C) A session update  
    D) A guardrail check  
    **Answer**: B) One AI invocation, including any tool calls  
    **Explanation**: A turn is one AI invocation, which may include tool calls, in the Agent Loop.

29. **How does the SDK reduce manual prompt engineering?**  
    A) By requiring manual prompt creation  
    B) By automating prompt handling in the Agent Loop  
    C) By disabling prompts  
    D) By restricting dynamic prompts  
    **Answer**: B) By automating prompt handling in the Agent Loop  
    **Explanation**: The Agent Loop automates prompt sending and result handling, reducing manual prompt engineering.

30. **What is an example of a tool an agent might use in the SDK?**  
    A) A database connection  
    B) A web search function  
    C) A user authentication module  
    D) A model training script  
    **Answer**: B) A web search function  
    **Explanation**: Agents can use tools like web search or file retrieval, integrated via Python functions.

## Section 3: Runner Methods (Questions 31-45)

31. **What is the primary difference between `run_sync` and `run_streamed` methods?**  
    A) `run_sync` streams events, while `run_streamed` waits for final output  
    B) `run_sync` waits for final output, while `run_streamed` streams events as they occur  
    C) Both methods are identical  
    D) `run_streamed` disables tool calls  
    **Answer**: B) `run_sync` waits for final output, while `run_streamed` streams events as they occur  
    **Explanation**: `run_sync` blocks until the final output is ready, while `run_streamed` provides real-time event streaming.

32. **In which scenario will `run_sync` NOT work?**  
    A) In a synchronous Python script  
    B) In an async environment like FastAPI or Jupyter notebook  
    C) When using OpenAI models  
    D) When guardrails are disabled  
    **Answer**: B) In an async environment like FastAPI or Jupyter notebook  
    **Explanation**: `run_sync` is a blocking call and cannot run in environments with an existing event loop.

33. **What happens in the Agent Loop when a final output is produced?**  
    A) The loop continues indefinitely  
    B) The loop terminates  
    C) The loop triggers a handoff  
    D) The loop raises an exception  
    **Answer**: B) The loop terminates  
    **Explanation**: When an agent produces a final output of type `agent.output_type`, the Agent Loop stops.

34. **What exception is raised if `max_turns` is exceeded in a workflow?**  
    A) GuardrailTripwireTriggered  
    B) MaxTurnsExceeded  
    C) OutputParserException  
    D) TypeError  
    **Answer**: B) MaxTurnsExceeded  
    **Explanation**: If the number of turns exceeds `max_turns`, a `MaxTurnsExceeded` exception is raised.

35. **When are guardrails applied in the Agent Loop?**  
    A) Only for the first agent’s input  
    B) For every agent’s input  
    C) For the final output only  
    D) For tool calls only  
    **Answer**: A) Only for the first agent’s input  
    **Explanation**: Guardrails are applied only to the initial agent’s input to validate it before processing.

36. **What does the `run` method return in the OpenAI Agents SDK?**  
    A) A list of tool calls  
    B) A RunResult containing inputs, guardrail results, and final output  
    C) A new agent instance  
    D) A session object  
    **Answer**: B) A RunResult containing inputs, guardrail results, and final output  
    **Explanation**: The `run` method returns a `RunResult` with all inputs, guardrail results, and the final output.

37. **What is the role of the `context` parameter in the `run_sync` method?**  
    A) Defines the output format  
    B) Provides execution context for the agent  
    C) Specifies tool calls  
    D) Stores previous responses  
    **Answer**: B) Provides execution context for the agent  
    **Explanation**: The `context` parameter supplies optional data or state for the agent during execution.

38. **What does the `run_streamed` method return?**  
    A) A RunResult with final output only  
    B) A RunResultStreaming object with a method to stream events  
    C) A list of guardrail results  
    D) A session history  
    **Answer**: B) A RunResultStreaming object with a method to stream events  
    **Explanation**: `run_streamed` returns a `RunResultStreaming` object for streaming events like tokens and tool calls.

39. **What happens if a handoff occurs in the Agent Loop?**  
    A) The loop terminates  
    B) The loop continues with a new agent  
    C) The loop raises an exception  
    D) The loop skips tool calls  
    **Answer**: B) The loop continues with a new agent  
    **Explanation**: A handoff transfers control to a new agent, and the loop continues with that agent.

40. **Which method should be used in an async environment like FastAPI?**  
    A) `run_sync`  
    B) `run`  
    C) `run_streamed`  
    D) Both B and C  
    **Answer**: D) Both B and C  
    **Explanation**: `run` (async) and `run_streamed` are suitable for async environments, while `run_sync` is not.

41. **Why is the `run` method defined as a classmethod?**  
    A) To restrict access to instances  
    B) To allow invocation without creating a Runner instance  
    C) To disable async functionality  
    D) To limit tool calls  
    **Answer**: B) To allow invocation without creating a Runner instance  
    **Explanation**: As a classmethod, `run` can be called directly on the Runner class, simplifying usage.

42. **What is the role of the `run_config` parameter?**  
    A) Defines the agent’s output type  
    B) Specifies global settings for the agent run  
    C) Stores session history  
    D) Triggers handoffs  
    **Answer**: B) Specifies global settings for the agent run  
    **Explanation**: `run_config` provides global configuration settings for the entire agent workflow.

43. **What is the purpose of the `session` parameter in the run methods?**  
    A) Defines tool calls  
    B) Manages conversation history across runs  
    C) Validates inputs  
    D) Generates dynamic prompts  
    **Answer**: B) Manages conversation history across runs  
    **Explanation**: The `session` parameter enables automatic management of conversation history.

44. **What is a common use case for the `run_streamed` method?**  
    A) Batch processing of inputs  
    B) Real-time applications needing event streaming  
    C) Disabling tool calls  
    D) Clearing session history  
    **Answer**: B) Real-time applications needing event streaming  
    **Explanation**: `run_streamed` is ideal for applications requiring real-time feedback, like live chat.

45. **What happens if no final output is produced within `max_turns`?**  
    A) The loop continues indefinitely  
    B) A MaxTurnsExceeded exception is raised  
    C) A GuardrailTripwireTriggered exception is raised  
    D) The session is cleared  
    **Answer**: B) A MaxTurnsExceeded exception is raised  
    **Explanation**: If `max_turns` is exceeded without a final output, a `MaxTurnsExceeded` exception is raised.

## Section 4: Exceptions and Error Handling (Questions 46-55)

46. **What exception is raised if a guardrail tripwire is triggered?**  
    A) MaxTurnsExceeded  
    B) GuardrailTripwireTriggered  
    C) OutputParserException  
    D) TypeError  
    **Answer**: B) GuardrailTripwireTriggered  
    **Explanation**: A `GuardrailTripwireTriggered` exception is raised when a guardrail check fails, halting the workflow.

47. **What causes a `MaxTurnsExceeded` exception?**  
    A) Invalid input format  
    B) Exceeding the maximum number of allowed turns  
    C) Failed tool call  
    D) Missing session object  
    **Answer**: B) Exceeding the maximum number of allowed turns  
    **Explanation**: This exception occurs when the workflow exceeds the `max_turns` limit.

48. **What happens if an LLM output fails the declared `output_type` schema?**  
    A) GuardrailTripwireTriggered  
    B) MaxTurnsExceeded  
    C) OutputParserException  
    D) TypeError  
    **Answer**: C) OutputParserException  
    **Explanation**: An `OutputParserException` is raised when the LLM output does not match the expected `output_type` schema.

49. **What happens if a tool call fails during an agent run?**  
    A) The loop terminates with a final output  
    B) The loop continues after handling the failure  
    C) A MaxTurnsExceeded exception is raised  
    D) The session is cleared  
    **Answer**: B) The loop continues after handling the failure  
    **Explanation**: The Agent Loop handles tool call failures and continues unless a final output or exception occurs.

50. **What happens if a tool call is not defined in the agent?**  
    A) The loop terminates  
    B) An error is raised during execution  
    C) The loop skips the tool call  
    D) The session is cleared  
    **Answer**: B) An error is raised during execution  
    **Explanation**: An invalid or undefined tool call raises an error (e.g., `ToolExecutionError`) during execution.

51. **How does the SDK ensure safety in multi-agent systems?**  
    A) By disabling handoffs  
    B) Through guardrails that validate inputs  
    C) By restricting tool usage  
    D) By clearing session history  
    **Answer**: B) Through guardrails that validate inputs  
    **Explanation**: Guardrails validate inputs to ensure safe and compliant operation in multi-agent systems.

52. **What is the significance of the `on_agent_action` hook?**  
    A) It is called after tool invocation  
    B) It is called after agent reasoning but before tool invocation  
    C) It terminates the agent loop  
    D) It validates inputs  
    **Answer**: B) It is called after agent reasoning but before tool invocation  
    **Explanation**: The `on_agent_action` hook is triggered when the agent decides to take an action, before tool execution.

53. **What is the role of the `on_agent_start` hook?**  
    A) Called after tool invocation  
    B) Called when the agent begins processing  
    C) Called after the final output  
    D) Called during guardrail validation  
    **Answer**: B) Called when the agent begins processing  
    **Explanation**: The `on_agent_start` hook is triggered when the agent starts its execution.

54. **What is a common use case for the `on_agent_end` hook?**  
    A) To validate inputs  
    B) To log the final output of an agent  
    C) To trigger a handoff  
    D) To define tool calls  
    **Answer**: B) To log the final output of an agent  
    **Explanation**: The `on_agent_end` hook is triggered when an agent completes, useful for logging or processing the output.

55. **How does the SDK handle tool call results?**  
    A) By ignoring them  
    B) By sending them back to the LLM in the Agent Loop  
    C) By terminating the loop  
    D) By clearing the session  
    **Answer**: B) By sending them back to the LLM in the Agent Loop  
    **Explanation**: Tool call results are sent back to the LLM for further processing within the Agent Loop.

## Section 5: APIs and Integration (Questions 56-65)

56. **What is the primary difference between the Chat Completions API and Responses API?**  
    A) Chat Completions API supports tool calls, Responses API does not  
    B) Responses API is more flexible, handling text completions, chat, and tool calls  
    C) Chat Completions API is newer than Responses API  
    D) Responses API is restricted to OpenAI models  
    **Answer**: B) Responses API is more flexible, handling text completions, chat, and tool calls  
    **Explanation**: The Responses API supports multiple tasks, making it more versatile than the Chat Completions API.

57. **Which API does the OpenAI Agents SDK primarily integrate with?**  
    A) Chat Completions API  
    B) Responses API  
    C) Embedding API  
    D) Fine-Tuning API  
    **Answer**: B) Responses API  
    **Explanation**: The SDK is designed to work seamlessly with the Responses API for newer OpenAI models.

58. **What does the Responses API support that the Chat Completions API does not?**  
    A) Only chat messages  
    B) Structured outputs and tool calls  
    C) Only text completions  
    D) Only image generation  
    **Answer**: B) Structured outputs and tool calls  
    **Explanation**: The Responses API supports text completions, chat, structured outputs, and tool calls.

59. **Which models are compatible with the OpenAI Agents SDK?**  
    A) Only OpenAI models  
    B) Any model supporting the Chat Completions API format  
    C) Only GPT-4.1  
    D) Only Gemini models  
    **Answer**: B) Any model supporting the Chat Completions API format  
    **Explanation**: The SDK’s interoperability supports any model provider with the Chat Completions API format.

60. **What is the benefit of using the `previous_response_id` with the Responses API?**  
    A) It defines the agent’s instructions  
    B) It avoids redundant input from previous turns  
    C) It disables guardrails  
    D) It triggers a handoff  
    **Answer**: B) It avoids redundant input from previous turns  
    **Explanation**: `previous_response_id` references prior responses, reducing redundant input data.

61. **What is a key feature of the Responses API compared to the Chat Completions API?**  
    A) It only supports chat messages  
    B) It supports structured outputs and tool calls  
    C) It is less flexible  
    D) It restricts model usage  
    **Answer**: B) It supports structured outputs and tool calls  
    **Explanation**: The Responses API’s versatility enhances the SDK’s functionality for complex tasks.

62. **How does the SDK support non-OpenAI models?**  
    A) By restricting model usage  
    B) Through compatibility with the Chat Completions API format  
    C) By disabling third-party models  
    D) By requiring custom integrations  
    **Answer**: B) Through compatibility with the Chat Completions API format  
    **Explanation**: The SDK supports any model provider with the Chat Completions API format.

63. **What is a benefit of the SDK’s integration with the Responses API?**  
    A) It restricts model usage  
    B) It supports structured outputs and tool calls  
    C) It disables chat functionality  
    D) It requires manual prompt engineering  
    **Answer**: B) It supports structured outputs and tool calls  
    **Explanation**: The Responses API enhances the SDK’s ability to handle structured outputs and tool calls.

64. **What is the role of Pydantic in the SDK?**  
    A) It restricts tool usage  
    B) It provides automatic schema generation and validation for tools  
    C) It disables tool calls  
    D) It requires manual schema creation  
    **Answer**: B) It provides automatic schema generation and validation for tools  
    **Explanation**: Pydantic simplifies tool creation with automatic schema generation and validation.

65. **How does the SDK support dynamic prompts?**  
    A) By restricting prompts to static strings  
    B) By allowing callable instructions for runtime generation  
    C) By disabling prompts  
    D) By requiring manual prompt updates  
    **Answer**: B) By allowing callable instructions for runtime generation  
    **Explanation**: Callable instructions enable dynamic prompt generation based on runtime context.

## Section 6: Practical Applications (Questions 66-75)

66. **Which industry can benefit from the OpenAI Agents SDK for real-time data retrieval?**  
    A) Gaming  
    B) Customer support  
    C) Hardware manufacturing  
    D) None of the above  
    **Answer**: B) Customer support  
    **Explanation**: The SDK enables AI assistants to pull real-time data (e.g., via web search) for customer support.

67. **How can the SDK be used in legal research?**  
    A) By restricting access to documents  
    B) By enabling agents to access internal documents via file search  
    C) By disabling tool calls  
    D) By limiting agent interactions  
    **Answer**: B) By enabling agents to access internal documents via file search  
    **Explanation**: The SDK supports file search tools for retrieving and processing internal documents.

68. **What is a real-world application of multi-agent workflows?**  
    A) Running a single agent for all tasks  
    B) Coordinating research and customer support tasks between agents  
    C) Disabling handoffs  
    D) Restricting tool usage  
    **Answer**: B) Coordinating research and customer support tasks between agents  
    **Explanation**: Multi-agent workflows allow specialized agents to collaborate on tasks like research and support.

69. **How does the SDK support finance applications?**  
    A) By disabling data retrieval  
    B) By enabling agents to access financial data via tools  
    C) By restricting multi-agent workflows  
    D) By disabling tracing  
    **Answer**: B) By enabling agents to access financial data via tools  
    **Explanation**: Agents can use tools like file search or APIs to process financial data.

70. **What is a benefit of the SDK in customer support applications?**  
    A) It restricts data access  
    B) It enables real-time data retrieval via web search  
    C) It disables multi-agent systems  
    D) It requires manual state management  
    **Answer**: B) It enables real-time data retrieval via web search  
    **Explanation**: The SDK allows agents to access real-time data, enhancing customer support efficiency.

71. **How does the SDK simplify complex task coordination?**  
    A) By restricting tasks to single agents  
    B) Through handoffs and multi-agent workflows  
    C) By disabling tool calls  
    D) By clearing session history  
    **Answer**: B) Through handoffs and multi-agent workflows  
    **Explanation**: Handoffs and multi-agent workflows enable efficient task coordination.

72. **What is a practical use case for the SDK in enterprises?**  
    A) Disabling data integration  
    B) Integrating internal and external data for AI assistants  
    C) Restricting tool usage  
    D) Disabling debugging tools  
    **Answer**: B) Integrating internal and external data for AI assistants  
    **Explanation**: The SDK supports tools like web and file search for data integration in enterprises.

73. **How does the SDK support real-time applications?**  
    A) By disabling streaming  
    B) Through the `run_streamed` method for event streaming  
    C) By restricting tool calls  
    D) By requiring manual output handling  
    **Answer**: B) Through the `run_streamed` method for event streaming  
    **Explanation**: `run_streamed` enables real-time event streaming for applications like live chat.

74. **What is an example of a tool used in the SDK for enterprise applications?**  
    A) A database connector  
    B) A file search function  
    C) A user authentication module  
    D) A model training script  
    **Answer**: B) A file search function  
    **Explanation**: File search is a common tool for retrieving internal documents in enterprise applications.

75. **How does the SDK reduce manual orchestration logic?**  
    A) By requiring manual state management  
    B) By automating agent coordination and task delegation  
    C) By disabling handoffs  
    D) By restricting tool calls  
    **Answer**: B) By automating agent coordination and task delegation  
    **Explanation**: The SDK abstracts orchestration logic, automating agent coordination and task delegation.

## Section 7: Community Feedback and Adoption (Questions 76-85)

76. **What indicates strong community adoption of the OpenAI Agents SDK?**  
    A) Lack of GitHub stars  
    B) Nearly 2,000 GitHub stars and numerous forks  
    C) No community contributions  
    D) Restricted repository access  
    **Answer**: B) Nearly 2,000 GitHub stars and numerous forks  
    **Explanation**: The SDK’s GitHub repository has nearly 2,000 stars, showing robust community interest.

77. **What do developers praise about the SDK’s ease of use?**  
    A) Its complex abstractions  
    B) Its minimal abstractions and Python-first approach  
    C) Its lack of Python integration  
    D) Its restriction to OpenAI models  
    **Answer**: B) Its minimal abstractions and Python-first approach  
    **Explanation**: Developers appreciate the SDK’s simple design and Python integration, reducing the learning curve.

78. **How has the SDK impacted enterprise applications, according to reviews?**  
    A) By restricting data integration  
    B) By enabling integration of internal and external data  
    C) By disabling multi-agent workflows  
    D) By limiting debugging tools  
    **Answer**: B) By enabling integration of internal and external data  
    **Explanation**: Enterprises note that the SDK simplifies data integration for AI assistants.

79. **What is a benefit of the SDK’s open-source nature?**  
    A) It restricts community contributions  
    B) It allows community-driven enhancements and examples  
    C) It limits access to the codebase  
    D) It disables third-party integrations  
    **Answer**: B) It allows community-driven enhancements and examples  
    **Explanation**: The open-source nature encourages community contributions and shared examples.

80. **What do beginner guides say about the SDK?**  
    A) It has a steep learning curve  
    B) It simplifies complex multi-agent setups  
    C) It restricts flexibility  
    D) It disables Python integration  
    **Answer**: B) It simplifies complex multi-agent setups  
    **Explanation**: Beginner guides highlight the SDK’s ability to make multi-agent systems accessible.

81. **What do developers say about the SDK’s handoff feature?**  
    A) It complicates workflows  
    B) It streamlines task delegation between agents  
    C) It disables multi-agent systems  
    D) It restricts tool usage  
    **Answer**: B) It streamlines task delegation between agents  
    **Explanation**: Developers praise handoffs for enabling seamless task delegation in multi-agent systems.

82. **What is a key advantage of the SDK’s tracing tools for enterprises?**  
    A) They disable debugging  
    B) They provide clear, actionable feedback for workflow optimization  
    C) They restrict agent interactions  
    D) They limit tool usage  
    **Answer**: B) They provide clear, actionable feedback for workflow optimization  
    **Explanation**: Tracing tools help enterprises optimize workflows with actionable feedback.

83. **What is a sign of the SDK’s open-source success?**  
    A) Lack of community contributions  
    B) Active community sharing of examples and enhancements  
    C) Restricted repository access  
    D) No shared examples  
    **Answer**: B) Active community sharing of examples and enhancements  
    **Explanation**: The SDK’s community actively shares examples and suggests improvements.

84. **How does the SDK support debugging complex workflows?**  
    A) By disabling tracing  
    B) Through built-in tracing and observability tools  
    C) By restricting handoffs  
    D) By requiring manual logging  
    **Answer**: B) Through built-in tracing and observability tools  
    **Explanation**: Tracing tools allow visualization and debugging of complex workflows.

85. **What is the community feedback on the SDK’s tracing feature?**  
    A) It complicates debugging  
    B) It is a game-changer for visualizing and debugging interactions  
    C) It restricts agent actions  
    D) It disables tool calls  
    **Answer**: B) It is a game-changer for visualizing and debugging interactions  
    **Explanation**: Developers praise tracing for simplifying workflow visualization and debugging.

## Section 8: Advanced Topics (Questions 86-100)

86. **What are generics in Python, as used in the SDK?**  
    A) Fixed types for specific functions  
    B) Flexible types for reusable code  
    C) Database connectors  
    D) Error handlers  
    **Answer**: B) Flexible types for reusable code  
    **Explanation**: Generics (e.g., `TypeVar`) allow flexible typing for reusable code, like `TContext` in the SDK.

87. **Why is `TContext` used as a generic type in the SDK?**  
    A) To restrict context to a single type  
    B) To allow flexible context types for different use cases  
    C) To disable context usage  
    D) To define tool calls  
    **Answer**: B) To allow flexible context types for different use cases  
    **Explanation**: `TContext` enables the Agent and Runner to handle various context types flexibly.

88. **What is the benefit of the SDK’s evaluation tools?**  
    A) They disable debugging  
    B) They allow performance assessment and model fine-tuning  
    C) They restrict agent interactions  
    D) They disable tool calls  
    **Answer**: B) They allow performance assessment and model fine-tuning  
    **Explanation**: Evaluation tools help assess workflow performance and fine-tune models.

89. **How does the SDK support model fine-tuning?**  
    A) By disabling evaluation tools  
    B) Through built-in evaluation and fine-tuning tools  
    C) By restricting model usage  
    D) By requiring manual fine-tuning  
    **Answer**: B) Through built-in evaluation and fine-tuning tools  
    **Explanation**: The SDK includes tools for evaluating and fine-tuning models to improve performance.

90. **What is the significance of the `RunResult` object?**  
    A) It stores tool definitions  
    B) It contains inputs, guardrail results, and the final output  
    C) It defines the agent’s instructions  
    D) It triggers handoffs  
    **Answer**: B) It contains inputs, guardrail results, and the final output  
    **Explanation**: The `RunResult` object encapsulates all inputs, guardrail results, and the final output.

91. **What is the benefit of the SDK’s lightweight design?**  
    A) It increases complexity  
    B) It reduces setup time and learning curve  
    C) It restricts flexibility  
    D) It disables Python integration  
    **Answer**: B) It reduces setup time and learning curve  
    **Explanation**: The lightweight design with few primitives simplifies setup and learning.

92. **What is a key feature of the SDK’s function tools?**  
    A) They require manual schema creation  
    B) They support automatic schema generation with Pydantic  
    C) They disable tool calls  
    D) They restrict tool flexibility  
    **Answer**: B) They support automatic schema generation with Pydantic  
    **Explanation**: Pydantic simplifies tool creation with automatic schema generation and validation.

93. **What happens if an agent delegates a task to another agent?**  
    A) The loop terminates  
    B) A handoff occurs, and the loop continues with the new agent  
    C) A GuardrailTripwireTriggered exception is raised  
    D) The session is cleared  
    **Answer**: B) A handoff occurs, and the loop continues with the new agent  
    **Explanation**: Handoffs allow seamless task delegation, with the loop continuing under the new agent.

94. **How does the SDK handle complex task coordination?**  
    A) By restricting tasks to single agents  
    B) Through handoffs and multi-agent workflows  
    C) By disabling tool calls  
    D) By clearing session history  
    **Answer**: B) Through handoffs and multi-agent workflows  
    **Explanation**: Handoffs and multi-agent workflows enable efficient task coordination.

95. **What is the benefit of the SDK’s compatibility with non-OpenAI models?**  
    A) It restricts model usage  
    B) It allows flexibility in choosing model providers  
    C) It disables tool calls  
    D) It requires manual API integration  
    **Answer**: B) It allows flexibility in choosing model providers  
    **Explanation**: Compatibility with the Chat Completions API format allows use of various model providers.

96. **What is the significance of the `RunResultStreaming` object?**  
    A) It stores session history  
    B) It provides a method to stream events in real-time  
    C) It defines tool calls  
    D) It validates inputs  
    **Answer**: B) It provides a method to stream events in real-time  
    **Explanation**: `RunResultStreaming` enables real-time streaming of events like tokens and tool calls.

97. **How does tracing help in debugging agent workflows?**  
    A) By disabling agent actions  
    B) By visualizing the flow of actions and interactions  
    C) By restricting tool calls  
    D) By clearing session history  
    **Answer**: B) By visualizing the flow of actions and interactions  
    **Explanation**: Tracing provides a visual representation of agent actions for debugging.

98. **What is a limitation of the `run_sync` method?**  
    A) It supports async environments  
    B) It cannot run in environments with an existing event loop  
    C) It disables tool calls  
    D) It restricts guardrail usage  
    **Answer**: B) It cannot run in environments with an existing event loop  
    **Explanation**: `run_sync` is a blocking call and fails in async environments like FastAPI.

99. **What is a benefit of the SDK’s open-source nature?**  
    A) It restricts community contributions  
    B) It allows community-driven enhancements and examples  
    C) It limits access to the codebase  
    D) It disables third-party integrations  
    **Answer**: B) It allows community-driven enhancements and examples  
    **Explanation**: The open-source nature encourages community contributions and shared examples.

100. **What is the role of the Runner class in the SDK?**  
     A) To define agent instructions  
     B) To orchestrate and control agent workflows  
     C) To store session history  
     D) To generate tool schemas  
     **Answer**: B) To orchestrate and control agent workflows  
     **Explanation**: The Runner class manages the execution of agent workflows, controlling the loop, safety, and results.