# Model Configuration MCQs

Below are 50 multiple-choice questions to help you prepare for your exam on the Agents SDK Model Configuration. Each question has four options, with only one correct answer.

## General Concepts

1. **What is the primary purpose of the Agents SDK in terms of model configuration?**  
   a) To restrict all agents to use OpenAI models only  
   b) To allow flexible configuration of models and providers at different levels  
   c) To disable tracing for all applications  
   d) To enforce a single model for the entire application  
   **Answer**: b) To allow flexible configuration of models and providers at different levels  

2. **Which configuration level allows setting defaults for the entire application?**  
   a) Agent Level  
   b) Run Level  
   c) Global Level  
   d) Model Level  
   **Answer**: c) Global Level  

3. **What is a key benefit of Agent Level configuration?**  
   a) It applies settings to all agents in the application  
   b) It allows different agents to use different models or providers in the same workflow  
   c) It disables tracing for a specific run  
   d) It sets a default API key for all runs  
   **Answer**: b) It allows different agents to use different models or providers in the same workflow  

4. **When would you use Run Level configuration?**  
   a) To set a default provider for the entire application  
   b) To override settings for a specific execution, like model or tracing options  
   c) To configure tools for all agents  
   d) To define a global API key  
   **Answer**: b) To override settings for a specific execution, like model or tracing options  

5. **What happens if you do not specify a model in the Agent configuration?**  
   a) The agent fails to initialize  
   b) The default GPT-4o model is used with the OpenAI API  
   c) The agent uses a random model  
   d) The agent uses the last configured model  
   **Answer**: b) The default GPT-4o model is used with the OpenAI API  

6. **Which level is best suited for mixing different models for specialized tasks (e.g., Spanish agent using GPT-3.5, English agent using Gemini)?**  
   a) Global Level  
   b) Run Level  
   c) Agent Level  
   d) None of the above  
   **Answer**: c) Agent Level  

7. **What is the scope of Global Level configuration?**  
   a) A single agent  
   b) A single run  
   c) The entire SDK/application  
   d) A specific model  
   **Answer**: c) The entire SDK/application  

8. **Which function is used to set the default OpenAI client for the entire application?**  
   a) `set_tracing_disabled()`  
   b) `set_default_openai_client()`  
   c) `set_default_openai_api()`  
   d) `load_dotenv()`  
   **Answer**: b) `set_default_openai_client()`  

9. **What is the purpose of `set_tracing_disabled(True)`?**  
   a) To enable tracing for debugging  
   b) To disable tracing for debugging or logging purposes  
   c) To set a default model  
   d) To configure guardrails  
   **Answer**: b) To disable tracing for debugging or logging purposes  

10. **Which configuration level is used for temporary overrides like high-temperature settings?**  
    a) Agent Level  
    b) Run Level  
    c) Global Level  
    d) Model Level  
    **Answer**: b) Run Level  

## Environment Variables and `dotenv`

11. **What does `from dotenv import load_dotenv` do?**  
    a) Loads Python modules from a directory  
    b) Loads environment variables from a `.env` file into the system environment  
    c) Configures the default OpenAI client  
    d) Initializes the Runner class  
    **Answer**: b) Loads environment variables from a `.env` file into the system environment  

12. **What is the purpose of a `.env` file?**  
    a) To store Python scripts  
    b) To store configuration values like API keys or database URLs  
    c) To define agent instructions  
    d) To configure model settings  
    **Answer**: b) To store configuration values like API keys or database URLs  

13. **What does `os.getenv('GEMINI_API_KEY')` do?**  
    a) Sets the API key in the environment  
    b) Retrieves the value of the `GEMINI_API_KEY` environment variable  
    c) Loads the `.env` file  
    d) Initializes the AsyncOpenAI client  
    **Answer**: b) Retrieves the value of the `GEMINI_API_KEY` environment variable  

14. **What happens if `os.getenv('GEMINI_API_KEY')` returns `None`?**  
    a) The program continues without an API key  
    b) An error is raised if the code checks for a missing API key  
    c) The default OpenAI API key is used  
    d) The model automatically switches to GPT-4o  
    **Answer**: b) An error is raised if the code checks for a missing API key  

15. **In the provided code, what is the purpose of `load_dotenv()`?**  
    a) To load Python dependencies  
    b) To read environment variables from a `.env` file  
    c) To initialize the Agent class  
    d) To disable tracing  
    **Answer**: b) To read environment variables from a `.env` file  

## OpenAIChatCompletionsModel

16. **What is the primary function of `OpenAIChatCompletionsModel`?**  
    a) To connect only to OpenAI GPT models  
    b) To connect to third-party LLMs that support the same message format as OpenAI  
    c) To disable tracing for all agents  
    d) To set global API keys  
    **Answer**: b) To connect to third-party LLMs that support the same message format as OpenAI  

17. **What are the required parameters for `OpenAIChatCompletionsModel`?**  
    a) `model` and `openai_client`  
    b) `api_key` and `base_url`  
    c) `model_settings` and `tools`  
    d) `tracing_disabled` and `model_provider`  
    **Answer**: a) `model` and `openai_client`  

18. **When using `OpenAIChatCompletionsModel` with a third-party LLM, what is required?**  
    a) Only an API key  
    b) Both an API key and a base URL  
    c) Only a base URL  
    d) A model provider only  
    **Answer**: b) Both an API key and a base URL  

19. **What happens if you use `OpenAIChatCompletionsModel` without specifying a base URL?**  
    a) It defaults to the OpenAI API endpoint  
    b) It raises an error  
    c) It uses a random endpoint  
    d) It switches to a local LLM  
    **Answer**: a) It defaults to the OpenAI API endpoint  

20. **Which model is used in the Agent Level code example?**  
    a) GPT-4o  
    b) Gemini-2.0-flash  
    c) Gemini-2.0-pro  
    d) GPT-3.5  
    **Answer**: b) Gemini-2.0-flash  

## RunConfig

21. **What is the purpose of the `RunConfig` class?**  
    a) To configure the default OpenAI client  
    b) To override settings for a specific `Runner.run()` call  
    c) To set global tracing options  
    d) To define agent instructions  
    **Answer**: b) To override settings for a specific `Runner.run()` call  

22. **Which parameter in `RunConfig` controls whether tracing is enabled or disabled?**  
    a) `model_provider`  
    b) `tracing_disabled`  
    c) `input_guardrails`  
    d) `workflow_name`  
    **Answer**: b) `tracing_disabled`  

23. **What is the default value of `tracing_disabled` in `RunConfig`?**  
    a) True  
    b) False  
    c) None  
    d) NotGiven  
    **Answer**: b) False  

24. **What does the `model_provider` parameter in `RunConfig` default to?**  
    a) OpenAI  
    b) MultiProvider  
    c) Gemini  
    d) None  
    **Answer**: b) MultiProvider  

25. **Which of the following is NOT a parameter of `RunConfig`?**  
    a) `model_settings`  
    b) `input_guardrails`  
    c) `api_key`  
    d) `trace_id`  
    **Answer**: c) `api_key`  

## AsyncOpenAI

26. **What is the purpose of the `AsyncOpenAI` class?**  
    a) To make synchronous API calls to OpenAI  
    b) To enable asynchronous API calls to OpenAI or compatible services  
    c) To configure agent instructions  
    d) To disable tracing globally  
    **Answer**: b) To enable asynchronous API calls to OpenAI or compatible services  

27. **Which parameter is required to initialize an `AsyncOpenAI` client for a third-party LLM?**  
    a) `model`  
    b) `api_key`  
    c) `instructions`  
    d) `tools`  
    **Answer**: b) `api_key`  

28. **What does the `base_url` parameter in `AsyncOpenAI` specify?**  
    a) The default model to use  
    b) The endpoint for the LLM provider’s API  
    c) The agent’s name  
    d) The tracing configuration  
    **Answer**: b) The endpoint for the LLM provider’s API  

29. **What is the default value of `timeout` in `AsyncOpenAI`?**  
    a) 0  
    b) NOT_GIVEN  
    c) 60  
    d) None  
    **Answer**: b) NOT_GIVEN  

30. **In the provided code, what is the `base_url` used for the Gemini API?**  
    a) `https://api.openai.com/v1`  
    b) `https://generativelanguage.googleapis.com/v1beta/openai/`  
    c) `https://gemini.api.com`  
    d) `https://openai.gemini.com`  
    **Answer**: b) `https://generativelanguage.googleapis.com/v1beta/openai/`  

## Agent Class

31. **Which parameter is required when creating an `Agent` instance?**  
    a) `instructions`  
    b) `name`  
    c) `model`  
    d) `tools`  
    **Answer**: b) `name`  

32. **What is the purpose of the `instructions` parameter in the `Agent` class?**  
    a) To specify the model provider  
    b) To define the system prompt or developer message  
    c) To configure tracing options  
    d) To set the API key  
    **Answer**: b) To define the system prompt or developer message  

33. **What is the default value of `tool_use_behavior` in the `Agent` class?**  
    a) `stop_on_first_tool`  
    b) `run_llm_again`  
    c) `None`  
    d) `ToolsToFinalOutputFunction`  
    **Answer**: b) `run_llm_again`  

34. **What does the `model_settings` parameter in the `Agent` class configure?**  
    a) API keys and base URLs  
    b) Model tuning parameters like temperature and top_p  
    c) Tracing options  
    d) Guardrail settings  
    **Answer**: b) Model tuning parameters like temperature and top_p  

35. **In the Agent Level code example, what is the name of the agent?**  
    a) Assistance  
    b) Assistant  
    c) GeminiAgent  
    d) OpenAIAgent  
    **Answer**: b) Assistant  

## Runner Class

36. **What is the primary role of the `Runner` class?**  
    a) To configure global API settings  
    b) To handle the execution of AI agents  
    c) To load environment variables  
    d) To define agent instructions  
    **Answer**: b) To handle the execution of AI agents  

37. **Which method is used to run an agent synchronously?**  
    a) `Runner.run()`  
    b) `Runner.run_sync()`  
    c) `Runner.run_streamed()`  
    d) `Runner.execute()`  
    **Answer**: b) `Runner.run_sync()`  

38. **What does `Runner.run_sync()` return?**  
    a) The agent instance  
    b) The final output of the agent’s execution  
    c) The model configuration  
    d) The API key  
    **Answer**: b) The final output of the agent’s execution  

39. **In the Run Level code example, what input is provided to `Runner.run_sync()`?**  
    a) Write a blog  
    b) Hi, how are you  
    c) Configure the model  
    d) Set tracing disabled  
    **Answer**: b) Hi, how are you  

40. **Which method is NOT part of the `Runner` class based on `dir(Runner)`?**  
    a) `run`  
    b) `run_streamed`  
    c) `configure`  
    d) `run_sync`  
    **Answer**: c) `configure`  

## Global Level Configuration

41. **What does `set_default_openai_api('chat_completions')` do?**  
    a) Sets the default model to GPT-4o  
    b) Specifies the default OpenAI API endpoint to use  
    c) Disables tracing globally  
    d) Loads environment variables  
    **Answer**: b) Specifies the default OpenAI API endpoint to use  

42. **What is the default return value of `set_tracing_disabled()`?**  
    a) True  
    b) False  
    c) None  
    d) NotGiven  
    **Answer**: c) None  

43. **In the Global Level code example, which model is used by the agent?**  
    a) GPT-4o  
    b) Gemini-2.0-flash  
    c) Gemini-2.0-pro  
    d) GPT-3.5  
    **Answer**: b) Gemini-2.0-flash  

44. **What is the use case for Global Level configuration?**  
    a) To configure a single agent  
    b) To set consistent settings across the entire application  
    c) To override settings for a single run  
    d) To define tools for a specific agent  
    **Answer**: b) To set consistent settings across the entire application  

## Code-Specific Questions

45. **What error is raised if the `GEMINI_API_KEY` is not loaded in the provided code?**  
    a) `KeyError`  
    b) `ValueError`  
    c) `TypeError`  
    d) `ImportError`  
    **Answer**: b) `ValueError`  

46. **In the Agent Level code, what is the purpose of `print(result.final_output)`?**  
    a) To display the agent’s configuration  
    b) To print the output generated by the agent  
    c) To show the API key  
    d) To list available models  
    **Answer**: b) To print the output generated by the agent  

47. **Which import is used to load the `RunConfig` class in the Run Level code?**  
    a) `from agents import RunConfig`  
    b) `from agents.run import RunConfig`  
    c) `from openai import RunConfig`  
    d) `from dotenv import RunConfig`  
    **Answer**: b) `from agents.run import RunConfig`  

48. **In the Global Level code, what does `set_default_openai_client(external_client)` do?**  
    a) Sets the default model for all agents  
    b) Configures the default OpenAI client for all agents and runs  
    c) Disables tracing for the application  
    d) Loads the `.env` file  
    **Answer**: b) Configures the default OpenAI client for all agents and runs  

49. **What is the input provided to `Runner.run_sync()` in the Global Level code example?**  
    a) Write a blog  
    b) Hi, how are you  
    c) Configure the model  
    d) Set the API key  
    **Answer**: b) Hi, how are you  

50. **Which parameter in the `Agent` class is used to specify tools the agent can use?**  
    a) `model_settings`  
    b) `instructions`  
    c) `tools`  
    d) `handoffs`  
    **Answer**: c) `tools`  

---
