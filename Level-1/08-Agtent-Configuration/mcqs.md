# OpenAI Agents SDK Model Configuration - 50 Multiple Choice Questions

## Instructions
Choose the correct answer for each question. Each question has four options, with only one correct answer.

---

### 1. At which configuration level can you set a default OpenAI client for the entire application?
A) Agent Level  
B) Run Level  
C) Global Level  
D) Tool Level  

**Answer**: C) Global Level  

---

### 2. What is the purpose of configuring an agent at the **Agent Level**?
A) To set defaults for the entire application  
B) To allow different agents to use specific models or providers  
C) To override settings for a single run  
D) To disable tracing globally  

**Answer**: B) To allow different agents to use specific models or providers  

---

### 3. Which class is used to create a model configuration for a third-party LLM like Gemini?
A) `AsyncOpenAI`  
B) `OpenAIChatCompletionsModel`  
C) `RunConfig`  
D) `Runner`  

**Answer**: B) `OpenAIChatCompletionsModel`  

---

### 4. What happens if you do not specify a model in the `Agent` class?
A) The agent fails to initialize  
B) The default GPT-4 model is used  
C) The agent uses a random model  
D) The agent uses the last configured model  

**Answer**: B) The default GPT-4 model is used  

---

### 5. Which function is used to load environment variables from a `.env` file?
A) `set_default_openai_client`  
B) `load_dotenv`  
C) `set_tracing_disabled`  
D) `run_sync`  

**Answer**: B) `load_dotenv`  

---

### 6. What is the purpose of the `RunConfig` class?
A) To define the agent's instructions  
B) To override settings for a specific run  
C) To set global defaults for all agents  
D) To manage handoffs between agents  

**Answer**: B) To override settings for a specific run  

---

### 7. Which parameter in the `AsyncOpenAI` class specifies the API endpoint?
A) `api_key`  
B) `base_url`  
C) `timeout`  
D) `max_retries`  

**Answer**: B) `base_url`  

---

### 8. What is the default value of the `model_provider` parameter in the `RunConfig` class?
A) `AsyncOpenAI`  
B) `MultiProvider`  
C) `OpenAIChatCompletionsModel`  
D) `None`  

**Answer**: B) `MultiProvider`  

---

### 9. Which function sets the default OpenAI client for the entire application?
A) `set_default_openai_api`  
B) `set_default_openai_client`  
C) `set_tracing_disabled`  
D) `load_dotenv`  

**Answer**: B) `set_default_openai_client`  

---

### 10. What is the purpose of the `instructions` parameter in the `Agent` class?
A) To specify the model provider  
B) To define the agent's role or system prompt  
C) To configure tracing settings  
D) To set the API key  

**Answer**: B) To define the agent's role or system prompt  

---

### 11. Which configuration level is best suited for a temporary override of model settings?
A) Agent Level  
B) Run Level  
C) Global Level  
D) Tool Level  

**Answer**: B) Run Level  

---

### 12. What is the purpose of the `set_default_openai_api` function?
A) To set the default API for all agents  
B) To disable tracing globally  
C) To load environment variables  
D) To configure the model provider  

**Answer**: A) To set the default API for all agents  

---

### 13. Which parameter in the `RunConfig` class disables tracing for a specific run?
A) `model_provider`  
B) `tracing_disabled`  
C) `workflow_name`  
D) `trace_id`  

**Answer**: B) `tracing_disabled`  

---

### 14. What is the role of the `model_settings` parameter in the `Agent` class?
A) To configure model tuning parameters like temperature  
B) To specify the API key  
C) To manage handoffs  
D) To define the agent's name  

**Answer**: A) To configure model tuning parameters like temperature  

---

### 15. Which class is responsible for executing an agent's operations?
A) `Agent`  
B) `Runner`  
C) `AsyncOpenAI`  
D) `RunConfig`  

**Answer**: B) `Runner`  

---

### 16. What is the purpose of the `tools` parameter in the `Agent` class?
A) To specify the API endpoint  
B) To define Python functions the agent can use  
C) To configure tracing settings  
D) To set the default client  

**Answer**: B) To define Python functions the agent can use  

---

### 17. Which method of the `Runner` class is used for synchronous execution?
A) `run`  
B) `run_sync`  
C) `run_streamed`  
D) `run_async`  

**Answer**: B) `run_sync`  

---

### 18. What is the default value of `tracing_disabled` in the `RunConfig` class?
A) True  
B) False  
C) None  
D) Auto  

**Answer**: B) False  

---

### 19. Which parameter in the `AsyncOpenAI` class specifies the maximum number of API retries?
A) `timeout`  
B) `max_retries`  
C) `base_url`  
D) `api_key`  

**Answer**: B) `max_retries`  

---

### 20. What is the purpose of the `handoffs` parameter in the `Agent` class?
A) To configure the model provider  
B) To allow delegation to other agents  
C) To validate inputs  
D) To set the API key  

**Answer**: B) To allow delegation to other agents  

---

### 21. Which configuration level allows different agents to use different models in the same workflow?
A) Global Level  
B) Run Level  
C) Agent Level  
D) Tool Level  

**Answer**: C) Agent Level  

---

### 22. What does the `load_dotenv` function do?
A) Loads Python libraries  
B) Loads environment variables from a `.env` file  
C) Configures the model provider  
D) Disables tracing  

**Answer**: B) Loads environment variables from a `.env` file  

---

### 23. Which class is used to connect to third-party LLMs like Gemini?
A) `AsyncOpenAI`  
B) `OpenAIChatCompletionsModel`  
C) `RunConfig`  
D) `Runner`  

**Answer**: B) `OpenAIChatCompletionsModel`  

---

### 24. What is the purpose of the `trace_id` parameter in the `RunConfig` class?
A) To identify the model  
B) To track a specific run for debugging  
C) To specify the API key  
D) To configure handoffs  

**Answer**: B) To track a specific run for debugging  

---

### 25. Which parameter in the `Agent` class is required?
A) `instructions`  
B) `model`  
C) `name`  
D) `tools`  

**Answer**: C) `name`  

---

### 26. What is the default value of `trace_include_sensitive_data` in the `RunConfig` class?
A) True  
B) False  
C) None  
D) Auto  

**Answer**: A) True  

---

### 27. What happens if the `gemini_api_key` is not found in the `.env` file?
A) The program continues with a default key  
B) A `ValueError` is raised  
C) The agent uses a fallback model  
D) Tracing is automatically disabled  

**Answer**: B) A `ValueError` is raised  

---

### 28. Which function sets the default API for the OpenAI SDK?
A) `set_default_openai_client`  
B) `set_default_openai_api`  
C) `set_tracing_disabled`  
D) `load_dotenv`  

**Answer**: B) `set_default_openai_api`  

---

### 29. What is the purpose of the `model_provider` parameter in the `RunConfig` class?
A) To specify the external API client  
B) To define the agent's name  
C) To configure the conversation history  
D) To set the tracing metadata  

**Answer**: A) To specify the external API client  

---

### 30. Which method of the `Runner` class is best for real-time feedback in live UIs?
A) `run`  
B) `run_sync`  
C) `run_streamed`  
D) `run_async`  

**Answer**: C) `run_streamed`  

---

### 31. What is the purpose of the `input_guardrails` parameter in the `RunConfig` class?
A) To validate the agent's output  
B) To validate the agent's input before processing  
C) To manage conversation history  
D) To configure the model provider  

**Answer**: B) To validate the agent's input before processing  

---

### 32. Which configuration level is used to set a consistent LLM provider for the entire application?
A) Agent Level  
B) Run Level  
C) Global Level  
D) Tool Level  

**Answer**: C) Global Level  

---

### 33. What is the purpose of the `workflow_name` parameter in the `RunConfig` class?
A) To identify the agent  
B) To name the agentic workflow for tracing  
C) To specify the model provider  
D) To configure the API key  

**Answer**: B) To name the agentic workflow for tracing  

---

### 34. Which parameter in the `OpenAIChatCompletionsModel` class is mandatory?
A) `api_key`  
B) `openai_client`  
C) `tracing_disabled`  
D) `workflow_name`  

**Answer**: B) `openai_client`  

---

### 35. What is the purpose of the `output_guardrails` parameter in the `RunConfig` class?
A) To validate the agent's output  
B) To configure the model provider  
C) To manage handoffs  
D) To disable tracing  

**Answer**: A) To validate the agent's output  

---

### 36. Which class creates an AI agent with specific behavior and capabilities?
A) `Runner`  
B) `Agent`  
C) `AsyncOpenAI`  
D) `RunConfig`  

**Answer**: B) `Agent`  

---

### 37. What is the purpose of the `handoff_input_filter` parameter in the `RunConfig` class?
A) To filter inputs before handoff to another agent  
B) To configure the model settings  
C) To manage conversation history  
D) To disable tracing  

**Answer**: A) To filter inputs before handoff to another agent  

---

### 38. Which feature allows the use of over 100 models with LiteLLM?
A) `AsyncOpenAI`  
B) `OpenAIChatCompletionsModel`  
C) `RunConfig`  
D) `Runner`  

**Answer**: B) `OpenAIChatCompletionsModel`  

---

### 39. What is the default API set by `set_default_openai_api` if not specified?
A) `chat_completions`  
B) `None`  
C) `completions`  
D) `embeddings`  

**Answer**: B) `None`  

---

### 40. Which parameter in the `Agent` class specifies the LLM to use?
A) `name`  
B) `instructions`  
C) `model`  
D) `tools`  

**Answer**: C) `model`  

---

### 41. What is the purpose of the `trace_metadata` parameter in the `RunConfig` class?
A) To store additional metadata for tracing  
B) To configure the model provider  
C) To manage conversation history  
D) To validate inputs  

**Answer**: A) To store additional metadata for tracing  

---

### 42. Which class is responsible for managing asynchronous API calls to OpenAI-compatible services?
A) `Agent`  
B) `Runner`  
C) `AsyncOpenAI`  
D) `RunConfig`  

**Answer**: C) `AsyncOpenAI`  

---

### 43. What is the purpose of the `tool_use_behavior` parameter in the `Agent` class?
A) To configure the API key  
B) To define how tools are used by the agent  
C) To set the model provider  
D) To manage conversation history  

**Answer**: B) To define how tools are used by the agent  

---

### 44. Which method of the `Runner` class returns a `RunResultStreaming` object?
A) `run`  
B) `run_sync`  
C) `run_streamed`  
D) `run_async`  

**Answer**: C) `run_streamed`  

---

### 45. What is the purpose of the `group_id` parameter in the `RunConfig` class?
A) To group multiple runs for tracking  
B) To specify the model provider  
C) To configure the API key  
D) To manage conversation history  

**Answer**: A) To group multiple runs for tracking  

---

### 46. Which configuration level is used to mix and match models for specialized agents?
A) Global Level  
B) Run Level  
C) Agent Level  
D) Tool Level  

**Answer**: C) Agent Level  

---

### 47. What is the default value of the `reset_tool_choice` parameter in the `Agent` class?
A) True  
B) False  
C) None  
D) Auto  

**Answer**: A) True  

---

### 48. Which parameter in the `AsyncOpenAI` class specifies the timeout for API requests?
A) `base_url`  
B) `timeout`  
C) `api_key`  
D) `max_retries`  

**Answer**: B) `timeout`  

---

### 49. What is the purpose of the `mcp_config` parameter in the `Agent` class?
A) To configure the model provider  
B) To define the agent's multi-agent communication protocol  
C) To validate inputs  
D) To set the API key  

**Answer**: B) To define the agent's multi-agent communication protocol  

---

### 50. Which class is used to handle the execution of AI agents?
A) `Agent`  
B) `Runner`  
C) `AsyncOpenAI`  
D) `RunConfig`  

**Answer**: B) `Runner`  

---

## End of MCQs
This set of questions covers the key concepts, configuration levels, and classes related to model configuration in the OpenAI Agents SDK. Use these questions to test your understanding or prepare for assessments.