# OpenAI Agents SDK - 50 Multiple Choice Questions

## Instructions
Choose the correct answer for each question. Each question has four options, with only one correct answer.

---

### 1. What is the primary purpose of the OpenAI Agents SDK?
A) To create complex machine learning models  
B) To build agentic AI applications with minimal abstractions  
C) To manage databases for AI applications  
D) To provide a UI framework for AI development  

**Answer**: B) To build agentic AI applications with minimal abstractions  

---

### 2. What is the minimum required parameter for creating an `Agent` object?
A) Instructions  
B) Name  
C) Model  
D) Tools  

**Answer**: B) Name  

---

### 3. What does the `Runner` class do in the OpenAI Agents SDK?
A) Defines the agent's tools  
B) Executes and manages the agent's thinking loop  
C) Validates API keys  
D) Configures the model settings  

**Answer**: B) Executes and manages the agent's thinking loop  

---

### 4. Which method of the `Runner` class is used for synchronous execution?
A) `run()`  
B) `run_sync()`  
C) `run_streamed()`  
D) `run_async()`  

**Answer**: B) `run_sync()`  

---

### 5. What is the role of the `AsyncOpenAI` class in the SDK?
A) To manage synchronous API calls  
B) To connect asynchronously to OpenAI-compatible APIs  
C) To generate Python functions automatically  
D) To disable tracing permanently  

**Answer**: B) To connect asynchronously to OpenAI-compatible APIs  

---

### 6. What happens when `set_tracing_disabled(True)` is called?
A) The agent stops functioning  
B) Tracing is disabled for debugging and monitoring  
C) The API key is reset  
D) The model is switched to a default one  

**Answer**: B) Tracing is disabled for debugging and monitoring  

---

### 7. Which feature of the Agents SDK automatically manages conversation history?
A) Guardrails  
B) Handoffs  
C) Sessions  
D) Tools  

**Answer**: C) Sessions  

---

### 8. What does the `instructions` parameter in the `Agent` class represent?
A) The agent's name  
B) The system prompt or persona  
C) The API key  
D) The model's configuration  

**Answer**: B) The system prompt or persona  

---

### 9. What is the purpose of the `load_dotenv` function?
A) To load Python libraries  
B) To load environment variables from a `.env` file  
C) To initialize the `Runner` class  
D) To validate API keys  

**Answer**: B) To load environment variables from a `.env` file  

---

### 10. Which class wraps an OpenAI-compatible model for use with the Agents SDK?
A) `AsyncOpenAI`  
B) `OpenAIChatCompletionsModel`  
C) `RunConfig`  
D) `Runner`  

**Answer**: B) `OpenAIChatCompletionsModel`  

---

### 11. What is the default value of `tracing_disabled` in the `RunConfig` class?
A) True  
B) False  
C) None  
D) Auto  

**Answer**: B) False  

---

### 12. Which method of the `Runner` class is best suited for real-time feedback in live UIs?
A) `run()`  
B) `run_sync()`  
C) `run_streamed()`  
D) `run_async()`  

**Answer**: C) `run_streamed()`  

---

### 13. What is the purpose of the `handoffs` feature in the Agents SDK?
A) To validate inputs and outputs  
B) To allow agents to delegate tasks to other agents  
C) To manage API keys  
D) To generate Python functions  

**Answer**: B) To allow agents to delegate tasks to other agents  

---

### 14. Which parameter in the `RunConfig` class specifies the model to use?
A) `model_provider`  
B) `model`  
C) `workflow_name`  
D) `trace_id`  

**Answer**: B) `model`  

---

### 15. What does the `OpenAIChatCompletionsModel` class require as a mandatory parameter?
A) `api_key`  
B) `openai_client`  
C) `tracing_disabled`  
D) `workflow_name`  

**Answer**: B) `openai_client`  

---

### 16. What is the purpose of the `guardrails` feature in the Agents SDK?
A) To manage conversation history  
B) To validate agent inputs and outputs  
C) To execute Python functions  
D) To connect to external APIs  

**Answer**: B) To validate agent inputs and outputs  

---

### 17. Which of the following is NOT a primitive of the OpenAI Agents SDK?
A) Agents  
B) Handoffs  
C) Guardrails  
D) Models  

**Answer**: D) Models  

---

### 18. What does the `tools` parameter in the `Agent` class specify?
A) The list of Python functions the agent can use  
B) The API keys for external providers  
C) The agent's name and instructions  
D) The tracing configuration  

**Answer**: A) The list of Python functions the agent can use  

---

### 19. What is the role of the `model_provider` parameter in the `RunConfig` class?
A) Specifies the external API client  
B) Defines the agent's name  
C) Configures the conversation history  
D) Sets the tracing metadata  

**Answer**: A) Specifies the external API client  

---

### 20. Which method is used to run an agent in an asynchronous environment?
A) `run_sync()`  
B) `run()`  
C) `run_streamed()`  
D) Both B and C  

**Answer**: D) Both B and C  

---

### 21. What is the default value of `trace_include_sensitive_data` in the `RunConfig` class?
A) True  
B) False  
C) None  
D) Auto  

**Answer**: A) True  

---

### 22. What does the `Runner.run_sync()` method return?
A) `RunResult`  
B) `RunResultStreaming`  
C) `AsyncOpenAI`  
D) `OpenAIChatCompletionsModel`  

**Answer**: A) `RunResult`  

---

### 23. Which parameter in the `AsyncOpenAI` class specifies the API endpoint?
A) `api_key`  
B) `base_url`  
C) `timeout`  
D) `max_retries`  

**Answer**: B) `base_url`  

---

### 24. What is the purpose of the `model_settings` parameter in the `RunConfig` class?
A) To configure model tuning parameters like temperature  
B) To specify the agent's instructions  
C) To manage handoffs between agents  
D) To disable tracing  

**Answer**: A) To configure model tuning parameters like temperature  

---

### 25. Which feature of the Agents SDK allows turning Python functions into tools?
A) Handoffs  
B) Function tools  
C) Guardrails  
D) Sessions  

**Answer**: B) Function tools  

---

### 26. What happens if the `gemini_api_key` is not found in the `.env` file?
A) The program continues with a default key  
B) A `ValueError` is raised  
C) The agent uses a fallback model  
D) Tracing is automatically disabled  

**Answer**: B) A `ValueError` is raised  

---

### 27. Which class is responsible for managing the agent's execution loop?
A) `Agent`  
B) `Runner`  
C) `OpenAIChatCompletionsModel`  
D) `AsyncOpenAI`  

**Answer**: B) `Runner`  

---

### 28. What is the purpose of the `workflow_name` parameter in the `RunConfig` class?
A) To identify the agent  
B) To name the agentic workflow for tracing  
C) To specify the model provider  
D) To configure the API key  

**Answer**: B) To name the agentic workflow for tracing  

---

### 29. Which of the following is a valid model parameter for `OpenAIChatCompletionsModel`?
A) `gpt-4`  
B) `agent-name`  
C) `api-key`  
D) `tracing-enabled`  

**Answer**: A) `gpt-4`  

---

### 30. What does the `input_guardrails` parameter in the `RunConfig` class do?
A) Validates the agent's output  
B) Validates the agent's input before processing  
C) Manages conversation history  
D) Configures the model provider  

**Answer**: B) Validates the agent's input before processing  

---

### 31. Which method is best for simple scripts or CLI tools?
A) `run()`  
B) `run_sync()`  
C) `run_streamed()`  
D) `run_async()`  

**Answer**: B) `run_sync()`  

---

### 32. What is the purpose of the `trace_id` parameter in the `RunConfig` class?
A) To identify the model  
B) To track a specific run for debugging  
C) To specify the API key  
D) To configure handoffs  

**Answer**: B) To track a specific run for debugging  

---

### 33. Which class is used to create an agent instance?
A) `Runner`  
B) `Agent`  
C) `AsyncOpenAI`  
D) `RunConfig`  

**Answer**: B) `Agent`  

---

### 34. What is the purpose of the `output_guardrails` parameter in the `RunConfig` class?
A) To validate the agent's output  
B) To configure the model provider  
C) To manage handoffs  
D) To disable tracing  

**Answer**: A) To validate the agent's output  

---

### 35. Which parameter in the `Agent` class specifies the LLM to use?
A) `name`  
B) `instructions`  
C) `model`  
D) `tools`  

**Answer**: C) `model`  

---

### 36. What does the `Runner.run_streamed()` method return?
A) `RunResult`  
B) `RunResultStreaming`  
C) `AsyncOpenAI`  
D) `OpenAIChatCompletionsModel`  

**Answer**: B) `RunResultStreaming`  

---

### 37. What is the purpose of the `handoff_input_filter` parameter in the `RunConfig` class?
A) To filter inputs before handoff to another agent  
B) To configure the model settings  
C) To manage conversation history  
D) To disable tracing  

**Answer**: A) To filter inputs before handoff to another agent  

---

### 38. Which of the following is a key feature of the Agents SDK?
A) Complex abstractions for advanced users  
B) Built-in tracing for debugging and monitoring  
C) Manual conversation history management  
D) Hard-coded API keys  

**Answer**: B) Built-in tracing for debugging and monitoring  

---

### 39. What is the purpose of the `max_retries` parameter in the `AsyncOpenAI` class?
A) To set the maximum number of API retries  
B) To configure the model temperature  
C) To specify the API key  
D) To manage handoffs  

**Answer**: A) To set the maximum number of API retries  

---

### 40. Which parameter in the `AsyncOpenAI` class specifies the timeout for API requests?
A) `base_url`  
B) `timeout`  
C) `api_key`  
D) `max_retries`  

**Answer**: B) `timeout`  

---

### 41. What does the `Agent` class represent in the OpenAI Agents SDK?
A) A database manager  
B) An intelligent AI actor  
C) A model configuration tool  
D) A tracing utility  

**Answer**: B) An intelligent AI actor  

---

### 42. Which feature of the Agents SDK allows coordination between multiple agents?
A) Sessions  
B) Handoffs  
C) Guardrails  
D) Function tools  

**Answer**: B) Handoffs  

---

### 43. What is the default value of the `model_provider` parameter in the `RunConfig` class?
A) `AsyncOpenAI`  
B) `MultiProvider`  
C) `OpenAIChatCompletionsModel`  
D) `None`  

**Answer**: B) `MultiProvider`  

---

### 44. Which of the following is NOT a method of the `Runner` class?
A) `run()`  
B) `run_sync()`  
C) `run_streamed()`  
D) `run_config()`  

**Answer**: D) `run_config()`  

---

### 45. What is the purpose of the `trace_metadata` parameter in the `RunConfig` class?
A) To store additional metadata for tracing  
B) To configure the model provider  
C) To manage conversation history  
D) To validate inputs  

**Answer**: A) To store additional metadata for tracing  

---

### 46. Which class is used to load environment variables securely?
A) `Agent`  
B) `Runner`  
C) `dotenv`  
D) `AsyncOpenAI`  

**Answer**: C) `dotenv`  

---

### 47. What is the purpose of the `openai_client` parameter in the `OpenAIChatCompletionsModel` class?
A) To specify the model name  
B) To connect to an OpenAI-compatible API  
C) To configure tracing  
D) To manage handoffs  

**Answer**: B) To connect to an OpenAI-compatible API  

---

### 48. Which parameter in the `Agent` class defines the agent's role or persona?
A) `name`  
B) `instructions`  
C) `model`  
D) `tools`  

**Answer**: B) `instructions`  

---

### 49. What is the purpose of the `group_id` parameter in the `RunConfig` class?
A) To group multiple runs for tracking  
B) To specify the model provider  
C) To configure the API key  
D) To manage conversation history  

**Answer**: A) To group multiple runs for tracking  

---

### 50. Which feature of the Agents SDK eliminates the need for manual state handling?
A) Guardrails  
B) Handoffs  
C) Sessions  
D) Function tools  

**Answer**: C) Sessions  

---

## End of MCQs
This set of questions covers the key concepts, classes, and features of the OpenAI Agents SDK as described in the provided content. Use these questions to test your understanding or prepare for assessments.