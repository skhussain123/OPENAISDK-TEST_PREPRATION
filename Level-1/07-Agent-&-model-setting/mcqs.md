**Q1. What is the purpose of the `nest_asyncio` library in Python?**  
a) To manage Python package dependencies  
b) To enable nested asyncio event loops (correct)  
c) To generate AI prompts  
d) To optimize synchronous code  

**Explanation**: `nest_asyncio` patches the `asyncio` event loop to allow nested event loops, useful in environments like Jupyter notebooks.

---

**Q2. What does the `nest_asyncio.apply()` function do?**  
a) Installs a new Python version  
b) Enables running nested asyncio event loops (correct)  
c) Creates a virtual environment  
d) Runs a FastAPI server  

**Explanation**: `nest_asyncio.apply()` modifies the `asyncio` event loop to support nested loops, allowing asynchronous code to run in already-running loops.

---

**Q3. Why might `nest_asyncio` be used in a project like `OpenAISdk/01-py-uv/method1-pkg`?**  
a) To manage project dependencies  
b) To run asynchronous AI API calls in a notebook (correct)  
c) To generate images  
d) To install external libraries  

**Explanation**: In AI projects using asynchronous APIs (e.g., OpenAI APIs), `nest_asyncio` enables nested event loops, useful in notebooks or scripts with existing loops.

---

**Q4. In which scenario is `nest_asyncio` most commonly needed?**  
a) Synchronous Python scripts  
b) Jupyter notebooks with asyncio code (correct)  
c) CPU-intensive tasks  
d) Database management  

**Explanation**: `nest_asyncio` is commonly used in Jupyter notebooks, where an event loop is already running, to allow nested `asyncio` operations.

---

**Q5. How does `nest_asyncio` benefit FastAPI applications in agentic AI projects?**  
a) It simplifies dependency management  
b) It enables nested asynchronous API calls (correct)  
c) It reduces memory usage  
d) It generates AI responses  

**Explanation**: `nest_asyncio` allows FastAPI applications to handle nested asynchronous calls, useful for integrating AI APIs in complex workflows.

---


**Q1. What is the purpose of the `load_dotenv()` function in the code?**  
a) To install new Python packages  
b) To load environment variables from a `.env` file (correct)  
c) To run the Gemini model  
d) To create a virtual environment  

**Explanation**: `load_dotenv()` from the `dotenv` library loads environment variables from a `.env` file into the Python environment.

---

**Q2. What does `os.getenv("GEMINI_API_KEY")` do in the code?**  
a) Sets a new environment variable  
b) Retrieves the value of the `GEMINI_API_KEY` variable (correct)  
c) Deletes an environment variable  
d) Generates an API key  

**Explanation**: `os.getenv("GEMINI_API_KEY")` retrieves the value of the `GEMINI_API_KEY` environment variable for use in the code.

---

**Q3. What happens if `GEMINI_API_KEY` is not set in the code?**  
a) The code continues without an API key  
b) A `ValueError` is raised (correct)  
c) A new API key is generated  
d) The Gemini model is disabled  

**Explanation**: The code raises a `ValueError` with a message if `GEMINI_API_KEY` is not defined in the `.env` file.

---

**Q4. What is the role of the `AsyncOpenAI` class in the code?**  
a) To manage Python dependencies  
b) To create a client for async API calls to Gemini (correct)  
c) To run synchronous tasks only  
d) To generate AI prompts  

**Explanation**: `AsyncOpenAI` creates an asynchronous client for making API calls to the Gemini model via a custom base URL.

---

**Q5. What does the `base_url` parameter specify in the `AsyncOpenAI` initialization?**  
a) The URL for the Python package manager  
b) The endpoint for the Gemini API (correct)  
c) The local server address  
d) The URL for the OpenAI model  

**Explanation**: The `base_url` is set to `https://generativelanguage.googleapis.com/v1beta/openai/` to connect to the Gemini API.

---

**Q6. What model is used in the `OpenAIChatCompletionsModel` in the code?**  
a) gpt-4o-mini  
b) gemini-2.0-flash (correct)  
c) gpt-3.5-turbo  
d) dall-e  

**Explanation**: The `OpenAIChatCompletionsModel` uses the `gemini-2.0-flash` model for processing requests.

---

**Q7. What is the purpose of the `openai_client` parameter in `OpenAIChatCompletionsModel`?**  
a) To specify the Python version  
b) To link the model to the AsyncOpenAI client (correct)  
c) To disable tracing  
d) To manage virtual environments  

**Explanation**: The `openai_client` parameter connects the model to the `AsyncOpenAI` client for API communication.

---

**Q8. What does the `RunConfig` class configure in the code?**  
a) The Python package dependencies  
b) The model, provider, and runtime settings (correct)  
c) The virtual environment path  
d) The API key generation  

**Explanation**: `RunConfig` sets up the model, provider (`external_client`), and settings like `tracing_disabled` for running the agent.

---

**Q9. What does `tracing_disabled=True` mean in the `RunConfig`?**  
a) It enables detailed logging  
b) It disables tracing for the agent run (correct)  
c) It activates web search tools  
d) It enables synchronous execution  

**Explanation**: `tracing_disabled=True` turns off tracing, which is used for debugging and monitoring agent actions.

---

**Q10. What is the role of the `Agent` class in the code?**  
a) To manage Python versions  
b) To define an AI agent with instructions and a model (correct)  
c) To install dependencies  
d) To generate environment variables  

**Explanation**: The `Agent` class defines an AI agent with a name, instructions, and a model for processing tasks.

---

**Q11. What is the name of the agent created in the code?**  
a) Gemini  
b) Assistant (correct)  
c) Runner  
d) OpenAI  

**Explanation**: The agent is named "Assistant" as specified in `Agent(name="Assistant", ...)`.

---

**Q12. What does the `instructions` parameter do in the `Agent` class?**  
a) Specifies the Python version  
b) Defines the agent’s behavior or role (correct)  
c) Sets the API key  
d) Configures the virtual environment  

**Explanation**: The `instructions` parameter (`"You are a helpful assistant"`) defines the agent’s role and behavior.

---

**Q13. What does the `Runner.run_sync` method do in the code?**  
a) Installs the Gemini model  
b) Runs the agent synchronously with a user input (correct)  
c) Creates a new agent  
d) Updates the `.env` file  

**Explanation**: `Runner.run_sync` executes the agent synchronously with the input "Hello, how are you." and returns the result.

---

**Q14. What is the input provided to the agent in the code?**  
a) What’s the capital of France?  
b) Hello, how are you. (correct)  
c) Search the latest AI news.  
d) Summarize findings.  

**Explanation**: The input `"Hello, how are you."` is passed to the agent via `Runner.run_sync`.

---

**Q15. What does `result.final_output` contain in the code?**  
a) The API key  
b) The agent’s response to the input (correct)  
c) The Python version used  
d) The dependency list  

**Explanation**: `result.final_output` contains the agent’s response to the input "Hello, how are you.".

---

**Q16. Why is the `AsyncOpenAI` client used instead of a synchronous client?**  
a) To simplify dependency management  
b) To support asynchronous API calls (correct)  
c) To disable model integration  
d) To manage synchronous tasks only  

**Explanation**: `AsyncOpenAI` enables asynchronous API calls, improving performance for I/O-bound tasks like API requests.

---

**Q17. How does the code ensure the Gemini API key is secure?**  
a) By hardcoding it in the script  
b) By loading it from a `.env` file (correct)  
c) By generating it dynamically  
d) By disabling the API key  

**Explanation**: The API key is loaded from a `.env` file using `os.getenv`, keeping it secure and separate from the code.

---

**Q18. What is the purpose of the `model_provider` in `RunConfig`?**  
a) To specify the Python version  
b) To link the model to the API client (correct)  
c) To install dependencies  
d) To enable tracing  

**Explanation**: The `model_provider` (`external_client`) links the model to the `AsyncOpenAI` client for API communication.

---

**Q19. What happens if the `.env` file is missing in the project?**  
a) The code runs without an API key  
b) A `ValueError` is raised (correct)  
c) A new `.env` file is created  
d) The Gemini model is bypassed  

**Explanation**: If `GEMINI_API_KEY` is not found, the code raises a `ValueError`, halting execution.

---

**Q20. Why is the code relevant to agentic AI development?**  
a) It manages Python package dependencies  
b) It sets up an AI agent with the Gemini model (correct)  
c) It generates images for AI applications  
d) It replaces FastAPI servers  

**Explanation**: The code configures an AI agent using the Gemini model, aligning with agentic AI development.

---

**Q21. What is the significance of using `gemini-2.0-flash` in the code?**  
a) It specifies a Python version  
b) It defines the AI model for the agent (correct)  
c) It enables web search tools  
d) It disables asynchronous calls  

**Explanation**: `gemini-2.0-flash` is the AI model used by the `OpenAIChatCompletionsModel` for processing agent tasks.

---

**Q22. What does the `print(result.final_output)` line do?**  
a) Prints the API key  
b) Prints the agent’s response (correct)  
c) Prints the model configuration  
d) Prints the `.env` file contents  

**Explanation**: It prints the agent’s final response to the input "Hello, how are you.".

---

**Q23. Why is `tracing_disabled=True` set in the code?**  
a) To enable detailed logging  
b) To reduce debugging overhead (correct)  
c) To activate web search tools  
d) To enable synchronous execution  

**Explanation**: Disabling tracing reduces overhead by turning off monitoring of the agent’s actions.

---

**Q24. How does the code integrate with UV in a project like `OpenAISdk/01-py-uv/method1-pkg`?**  
a) By generating AI prompts  
b) By managing dependencies like `openai-agents` (correct)  
c) By replacing the asyncio event loop  
d) By creating a new model  

**Explanation**: UV can manage dependencies like `openai-agents`, ensuring a reproducible environment for the project.

---

**Q25. What is the role of the `Runner` class in the code?**  
a) To install Python packages  
b) To execute the agent’s tasks (correct)  
c) To create environment variables  
d) To configure the `.env` file  

**Explanation**: The `Runner` class handles the execution of the agent’s tasks, either synchronously or asynchronously.

---

**Q26. Why is `AsyncOpenAI` used with a custom `base_url`?**  
a) To connect to the OpenAI API  
b) To connect to the Gemini API endpoint (correct)  
c) To disable API calls  
d) To manage local servers  

**Explanation**: The custom `base_url` points to the Gemini API endpoint, allowing the use of Gemini models.

---

**Q27. What is the purpose of the `model` parameter in the `Agent` class?**  
a) To specify the Python version  
b) To define the AI model for the agent (correct)  
c) To enable tracing  
d) To install dependencies  

**Explanation**: The `model` parameter links the agent to the `OpenAIChatCompletionsModel` (`gemini-2.0-flash`) for processing.

---

**Q28. What does the `run_config` parameter in `Runner.run_sync` do?**  
a) Specifies the input prompt  
b) Configures runtime settings for the agent (correct)  
c) Installs the Gemini model  
d) Generates the API key  

**Explanation**: `run_config` provides runtime settings like the model and provider for the agent’s execution.

---

**Q1. What does the `Agent` class do in the code line?**  
a) Installs Python packages  
b) Creates an AI agent (correct)  
c) Manages virtual environments  
d) Generates API keys  

**Explanation**: The `Agent` class creates an AI agent with specific behavior and capabilities, as defined by its parameters.

---

**Q2. What is the purpose of the `name` parameter in `Agent(name="Assistant", ...)`?**  
a) To specify the Python version  
b) To identify the agent (correct)  
c) To set the API endpoint  
d) To define the project folder  

**Explanation**: The `name` parameter ("Assistant") provides a unique identifier for the agent.this is a agent name

---

**Q4. What does the `instructions` parameter do in the `Agent` class?**  
a) Specifies the API key  
b) Defines the agent’s role or behavior (correct)  
c) Installs dependencies  
d) Sets the Python version  

**Explanation**: The `instructions` parameter defines the agent’s behavior, in this case, "You are a helpful assistant".Agent parsona

---
**Q6. What is the role of the `model` parameter in the `Agent` class?**  
a) To manage environment variables  
b) To specify the AI model for the agent (correct)  
c) To disable tracing  
d) To create a virtual environment  

**Explanation**: The `model` parameter links the agent to an AI model (e.g., `gemini-2.0-flash`) for processing tasks.
---

**Q7. What type of object is assigned to the `model` parameter in the code?**  
a) AsyncOpenAI  
b) OpenAIChatCompletionsModel (correct)  
c) RunConfig  
d) Runner  

**Explanation**: The `model` parameter is assigned an `OpenAIChatCompletionsModel` object configured with `gemini-2.0-flash`.

---

**Q8. Why is the `Agent` class important for agentic AI development?**  
a) It manages Python dependencies  
b) It defines autonomous AI agents (correct)  
c) It generates images  
d) It replaces FastAPI servers  

**Explanation**: The `Agent` class creates autonomous AI agents that can process tasks, key to agentic AI systems.

---

**Q18. How does the `model` parameter relate to the `AsyncOpenAI` client?**  
a) It replaces the client  
b) It uses the client for API communication (correct)  
c) It disables the client  
d) It manages the client’s dependencies  

**Explanation**: The `model` uses the `AsyncOpenAI` client (via `openai_client`) to communicate with the Gemini API.

---

**Q19. what is the default value for the instructions parameter in the agent class?
1. you are a help full assistance
2. None (Correct)  -->instructions: str | ((RunContextWrapper[Any], Agent[Any]) -> MaybeAwaitable[str]) | None = None,
3. An empty string
4. A default sysytem prompt

---

**Q1. What is the primary purpose of the `AsyncOpenAI` class in the OpenAI Agents SDK?**  
a) To manage Python dependencies  
b) To enable asynchronous API calls to OpenAI services (correct)  
c) To generate AI prompts  
d) To create virtual environments  

**Explanation**: `AsyncOpenAI` enables asynchronous API calls to OpenAI or compatible services, improving performance for I/O-bound tasks.

---

**Q2. Which parameter in `AsyncOpenAI` specifies the API endpoint?**  
a) `api_key`  
b) `base_url` (correct)  
c) `timeout`  
d) `max_retries`  

**Explanation**: The `base_url` parameter defines the API endpoint, such as `https://generativelanguage.googleapis.com/v1beta/openai/` for Gemini.

---

**Q3. What is the default value for `max_retries` in `AsyncOpenAI`?**  
a) 0  
b) DEFAULT_MAX_RETRIES (correct)  
c) None  
d) 10  

**Explanation**: The `max_retries` parameter defaults to `DEFAULT_MAX_RETRIES`, as specified in the `AsyncOpenAI` class definition.

---

**Q4. What does the `Agent` class do in the OpenAI Agents SDK?**  
a) Manages virtual environments  
b) Creates an AI agent with specific behavior (correct)  
c) Installs Python packages  
d) Generates API keys  

**Explanation**: The `Agent` class creates an AI agent with defined behavior, instructions, and a model for task processing.

---

**Q5. Which `Agent` class parameter defines the agent’s behavior?**  
a) `name`  
b) `instructions` (correct)  
c) `model_settings`  
d) `tools`  

**Explanation**: The `instructions` parameter, such as "You are a helpful assistant", defines the agent’s role and behavior.

---

**Q6. What is the purpose of the `model` parameter in the `Agent` class?**  
a) To specify the Python version  
b) To link the agent to an AI model (correct)  
c) To enable tracing  
d) To manage dependencies  

**Explanation**: The `model` parameter links the agent to an AI model, such as `gemini-2.0-flash`, for processing tasks.

---

**Q7. What does the `handoffs` parameter in the `Agent` class allow?**  
a) Installing dependencies  
b) Transferring tasks to other agents (correct)  
c) Disabling tracing  
d) Generating API keys  

**Explanation**: The `handoffs` parameter enables task delegation to other agents or handoff objects, supporting multi-agent workflows.

---

**Q8. What is a system prompt in the context of the `Agent` class?**  
a) A user input prompt  
b) Instructions defining the agent’s behavior (correct)  
c) A tool schema  
d) A Python script  

**Explanation**: The system prompt, set via `instructions`, defines the agent’s behavior, such as "You are a helpful assistant".

---

**Q9. What happens to a tool’s final answer in the `Agent` workflow?**  
a) It is stored in the `.env` file  
b) It is sent back to the agent (correct)  
c) It is discarded  
d) It is sent to the API client  

**Explanation**: The final answer from a tool is returned to the agent for further processing or response generation.

---

**Q10. What is the role of the `Runner` class in the code?**  
a) To install dependencies  
b) To execute AI agent tasks (correct)  
c) To manage environment variables  
d) To create API endpoints  

**Explanation**: The `Runner` class handles the execution of AI agents, either synchronously or asynchronously.

---

**Q11. What does the `Runner.run_sync` method do?**  
a) Runs the agent asynchronously  
b) Runs the agent synchronously (correct)  
c) Installs the agent’s model  
d) Generates a system prompt  

**Explanation**: `Runner.run_sync` executes the agent’s tasks synchronously, without requiring `await`.

---

**Q12. Why is `await` required for the `Runner.run` method?**  
a) It is a synchronous method  
b) It is an asynchronous method (correct)  
c) It manages dependencies  
d) It disables tracing  

**Explanation**: `Runner.run` is an asynchronous method, requiring `await` and an event loop to execute.

---

**Q13. What is the purpose of `Runner.stream` in the OpenAI Agents SDK?**  
a) To install dependencies in real-time  
b) To provide real-time streaming responses (correct)  
c) To run synchronous tasks  
d) To disable tools  

**Explanation**: `Runner.stream` delivers responses in real-time chunks, ideal for chat apps or live outputs.

---

**Q14. Which `Runner` method is best for simple scripts without async/await?**  
a) `Runner.run`  
b) `Runner.run_sync` (correct)  
c) `Runner.stream`  
d) `Runner.install`  

**Explanation**: `Runner.run_sync` is synchronous, making it suitable for simple scripts without async/await.

---

**Q15. What is printed when using `print(result.final_output)` after `Runner.run_sync`?**  
a) The API key  
b) The agent’s final response (correct)  
c) The model configuration  
d) The environment variables  

**Explanation**: `result.final_output` contains the agent’s final response, such as "I am doing well, thank you!".

---

**Q16. What is a use case for `Runner.stream`?**  
a) Installing Python packages  
b) Real-time chat applications (correct)  
c) Synchronous script execution  
d) Generating API keys  

**Explanation**: `Runner.stream` is used for real-time applications like chat apps, where responses are streamed token-by-token.

---

**Q17. How does `asyncio.run(main())` relate to `Runner.run`?**  
a) It disables asynchronous execution  
b) It runs the async `main` function with `Runner.run` (correct)  
c) It installs dependencies  
d) It generates a system prompt  

**Explanation**: `asyncio.run(main())` executes the async `main` function, which uses `await Runner.run` to run the agent.

---

**Q18. What does the `tool_use_behavior` parameter in the `Agent` class control?**  
a) The Python version used  
b) How tools are handled during execution (correct)  
c) The API endpoint  
d) The environment variables  

**Explanation**: `tool_use_behavior` (e.g., "run_llm_again") defines how the agent processes tool outputs.

---

**Q19. What is the default value of `tool_use_behavior` in the `Agent` class?**  
a) stop_on_first_tool  
b) run_llm_again (correct)  
c) disable_tools  
d) generate_output  

**Explanation**: The default `tool_use_behavior` is `"run_llm_again"`, as specified in the `Agent` class.

---

**Q20. At which level can you configure a model provider in the OpenAI Agents SDK?**  
a) Agent, Run, and Global levels (correct)  
b) Only Agent level  
c) Only Run level  
d) Only Global level  

**Explanation**: The SDK allows model provider configuration at Agent, Run, and Global levels for flexibility.

---

**Q21. How is the model provider set at the Agent level?**  
a) Using `set_default_openai_client`  
b) In the `Agent` class’s `model` parameter (correct)  
c) In the `RunConfig` class  
d) Using `asyncio.run`  

**Explanation**: The model provider is set via the `model` parameter in the `Agent` class, as shown in the Agent-level example.

---

**Q22. What does `RunConfig` do in the Run-level configuration?**  
a) Installs dependencies  
b) Specifies the model and provider for a run (correct)  
c) Generates API keys  
d) Disables asynchronous calls  

**Explanation**: `RunConfig` sets the model and provider for a specific run, as shown in the Run-level example.

---

**Q23. What is the purpose of `set_default_openai_client` in Global-level configuration?**  
a) To disable tracing  
b) To set a default client for all agents (correct)  
c) To run synchronous tasks  
d) To create a virtual environment  

**Explanation**: `set_default_openai_client` sets a default API client globally, used unless overridden.

---

**Q24. What happens if you override the model at the Run level?**  
a) The Agent-level model is used  
b) The Run-level model takes precedence (correct)  
c) The Global-level model is used  
d) The model is disabled  

**Explanation**: Run-level configuration in `RunConfig` overrides Agent or Global-level settings for that run.

---

**Q25. Why is `set_tracing_disabled(True)` used in the Global-level example?**  
a) To enable detailed logging  
b) To disable tracing for all runs (correct)  
c) To activate web search tools  
d) To run synchronous tasks  

**Explanation**: `set_tracing_disabled(True)` turns off tracing globally, reducing debugging overhead.

---

**Q26. What is the role of the `input_guardrails` parameter in the `Agent` class?**  
a) To validate input data (correct)  
b) To generate output responses  
c) To install dependencies  
d) To set the API endpoint  

**Explanation**: `input_guardrails` validates input data to ensure it meets safety or format requirements.

---

**Q27. What does the `output_guardrails` parameter in the `Agent` class do?**  
a) Manages Python versions  
b) Validates output data (correct)  
c) Generates API keys  
d) Disables asynchronous calls  

**Explanation**: `output_guardrails` ensures the agent’s output meets defined safety or format standards.

---

**Q28. Why is the `AsyncOpenAI` client useful in the `OpenAISdk` project?**  
a) It simplifies dependency management  
b) It supports asynchronous AI API calls (correct)  
c) It disables model integration  
d) It generates environment variables  

**Explanation**: `AsyncOpenAI` enables efficient asynchronous API calls, ideal for AI-driven projects like `OpenAISdk`.

---

**Q29. What is a benefit of using `Runner.run_sync` in simple scripts?**  
a) It requires async/await  
b) It avoids async/await complexity (correct)  
c) It streams responses in real-time  
d) It installs dependencies  

**Explanation**: `Runner.run_sync` allows synchronous execution, simplifying scripts without needing async/await.

---

**Q30. How does the `Agent` class support FastAPI integration in `OpenAISdk`?**  
a) By replacing FastAPI servers  
b) By enabling async AI task processing (correct)  
c) By managing FastAPI dependencies  
d) By disabling API endpoints  

**Explanation**: The `Agent` class, with `AsyncOpenAI`, supports async task processing, making it compatible with FastAPI for AI applications.
