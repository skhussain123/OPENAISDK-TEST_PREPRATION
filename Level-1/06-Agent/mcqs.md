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
