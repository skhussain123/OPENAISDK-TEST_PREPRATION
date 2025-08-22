## Section 1: OpenAI Agents SDK Tools Documentation (30 MCQs)

**Q1. What is the purpose of tools in the OpenAI Agents SDK?**  
a) To manage Python dependencies  
b) To allow agents to take actions like fetching data (correct)  
c) To disable asynchronous calls  
d) To generate API keys  

**Explanation**: Tools enable agents to perform actions like fetching data, running code, or calling APIs.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q2. How many classes of tools are defined in the OpenAI Agents SDK?**  
a) Two  
b) Three (correct)  
c) Four  
d) Five  

**Explanation**: The SDK defines three classes: hosted tools, function tools, and agents as tools.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q3. Which of the following is a hosted tool offered by OpenAI?**  
a) FileSearchTool (correct)  
b) FunctionTool  
c) PythonTool  
d) AgentTool  

**Explanation**: `FileSearchTool` is a hosted tool for retrieving information from vector stores.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q4. What does the `WebSearchTool` do in the OpenAI Agents SDK?**  
a) Runs Python code  
b) Searches the web for information (correct)  
c) Reads local files  
d) Generates JSON schemas  

**Explanation**: `WebSearchTool` enables agents to search the web for real-time data.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q5. What is a characteristic of hosted tools in the SDK?**  
a) They run on local servers  
b) They run on LLM servers with AI models (correct)  
c) They require manual schema creation  
d) They cannot use external APIs  

**Explanation**: Hosted tools run on LLM servers alongside AI models.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q6. What does the `@function_tool` decorator do?**  
a) Disables function execution  
b) Turns a Python function into a tool (correct)  
c) Generates API keys  
d) Manages virtual environments  

**Explanation**: The `@function_tool` decorator registers a Python function as a tool for agents.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q7. How is the tool name derived for a function tool?**  
a) From the API key  
b) From the Python function name (correct)  
c) From the agent’s name  
d) From the `.env` file  

**Explanation**: The tool name is automatically set to the Python function name unless overridden.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q8. What module does the SDK use to parse function signatures?**  
a) `json`  
b) `inspect` (correct)  
c) `asyncio`  
d) `dotenv`  

**Explanation**: The `inspect` module extracts the function signature for schema creation.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q9. What is used to parse docstrings in function tools?**  
a) `pydantic`  
b) `griffe` (correct)  
c) `typing_extensions`  
d) `asyncio`  

**Explanation**: The `griffe` library parses docstrings to extract tool and argument descriptions.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q10. Which docstring format is supported by the SDK?**  
a) YAML  
b) Google (correct)  
c) XML  
d) JSON  

**Explanation**: Supported formats include Google, Sphinx, and NumPy.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q11. What does the `params_json_schema` in a `FunctionTool` define?**  
a) The agent’s instructions  
b) The schema for function arguments (correct)  
c) The API endpoint  
d) The tracing configuration  

**Explanation**: `params_json_schema` defines the JSON schema for the tool’s input arguments.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q12. What is the purpose of the `on_invoke_tool` function in a `FunctionTool`?**  
a) To generate API keys  
b) To execute the tool’s logic (correct)  
c) To disable tracing  
d) To manage dependencies  

**Explanation**: `on_invoke_tool` is an async function that runs the tool’s logic and returns its output.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q13. What happens if `use_docstring_info` is set to `False` in a function tool?**  
a) Docstring parsing is disabled (correct)  
b) The tool is disabled  
c) The function runs synchronously  
d) The schema is manually created  

**Explanation**: Setting `use_docstring_info` to `False` disables docstring parsing for descriptions.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q14. What is the role of `pydantic` in function tools?**  
a) To manage asynchronous tasks  
b) To create JSON schemas for arguments (correct)  
c) To parse web search results  
d) To generate API endpoints  

**Explanation**: `pydantic` is used to dynamically build JSON schemas for function arguments.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q15. What does the `agents as tools` approach allow?**  
a) Disabling agent execution  
b) Using one agent as a tool for another (correct)  
c) Generating API keys  
d) Managing file systems  

**Explanation**: Agents can be used as tools, allowing one agent to call another without handoff.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q16. What is the benefit of using agents as tools?**  
a) Simplifies dependency management  
b) Enables orchestration of specialized agents (correct)  
c) Disables asynchronous execution  
d) Generates JSON schemas  

**Explanation**: This approach allows a central agent to orchestrate specialized agents for specific tasks.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q17. How is an agent turned into a tool in the SDK?**  
a) Using the `as_tool` method (correct)  
b) Using the `run` method  
c) Using the `clone` method  
d) Using the `connect` method  

**Explanation**: The `as_tool` method converts an agent into a tool for another agent to use.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q18. What is a limitation of the `as_tool` method?**  
a) It cannot set `max_turns` (correct)  
b) It disables tool execution  
c) It requires manual schema creation  
d) It prevents async execution  

**Explanation**: The `as_tool` method does not support advanced configurations like `max_turns`.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q19. What is the purpose of the `custom_output_extractor` in `as_tool`?**  
a) To disable tool output  
b) To modify the agent’s output before returning (correct)  
c) To generate API keys  
d) To manage tracing  

**Explanation**: `custom_output_extractor` reformats or validates the tool-agent’s output.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q20. What does the `failure_error_function` do in a function tool?**  
a) Generates JSON schemas  
b) Handles errors during tool execution (correct)  
c) Disables docstring parsing  
d) Runs the tool synchronously  

**Explanation**: It provides an error response to the LLM if the tool crashes.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q21. What happens if `failure_error_function` is set to `None`?**  
a) Errors are ignored  
b) Errors are re-raised for manual handling (correct)  
c) The tool is disabled  
d) The LLM stops processing  

**Explanation**: Setting `failure_error_function` to `None` re-raises errors for the developer to handle.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q22. What is the default behavior of `failure_error_function`?**  
a) It disables the tool  
b) It sends an error message to the LLM (correct)  
c) It generates a new tool  
d) It resets the agent  

**Explanation**: The default function informs the LLM of an error during tool execution.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q23. Which tool allows agents to execute code in a sandboxed environment?**  
a) WebSearchTool  
b) CodeInterpreterTool (correct)  
c) FileSearchTool  
d) ComputerTool  

**Explanation**: `CodeInterpreterTool` enables code execution in a sandboxed environment.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q24. What is the role of the `RunContextWrapper` in function tools?**  
a) To manage API keys  
b) To pass context to the tool (correct)  
c) To disable tracing  
d) To generate schemas  

**Explanation**: `RunContextWrapper` provides context to tools during execution.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q25. How does the SDK handle complex Python types in function tools?**  
a) It ignores them  
b) It supports them via type annotations (correct)  
c) It converts them to strings  
d) It disables them  

**Explanation**: The SDK uses type annotations to support complex types like `TypedDict`.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q26. What does the `ComputerTool` enable in the SDK?**  
a) Web searches  
b) Automating computer use tasks (correct)  
c) File reading  
d) API key generation  

**Explanation**: `ComputerTool` automates tasks like data entry or app workflows.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q27. Why is docstring parsing important for function tools?**  
a) It disables tool execution  
b) It provides descriptions for the tool and arguments (correct)  
c) It generates API endpoints  
d) It manages dependencies  

**Explanation**: Docstrings provide descriptions used in the tool’s schema and LLM interaction.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q28. What is the output format of a function tool?**  
a) A JSON object  
b) A string (correct)  
c) A dictionary  
d) A list  

**Explanation**: Function tools return a string as their output, as seen in `fetch_weather`.[](https://openai.github.io/openai-agents-python/tools/)

---

**Q29. How does the SDK prevent infinite loops in tool usage?**  
a) By disabling tools  
b) By resetting `tool_choice` to "auto" (correct)  
c) By generating new tools  
d) By stopping the agent  

**Explanation**: The SDK resets `tool_choice` to "auto" after a tool call to avoid loops.[](https://openai.github.io/openai-agents-python/agents/)

---

**Q30. How does the `HostedMCPTool` function in the SDK?**  
a) It disables hosted tools  
b) It exposes tools from a remote MCP server (correct)  
c) It generates JSON schemas  
d) It manages tracing  

**Explanation**: `HostedMCPTool` integrates tools from a remote MCP server into the agent.[](https://openai.github.io/openai-agents-python/tools/)

## Section 2: Panaversity Learn-Agentic-AI Basic Tools (06_basic_tools) (30 MCQs)

**Q31. What is the focus of the `06_basic_tools` section in `learn-agentic-ai`?**  
a) Generating API keys  
b) Implementing basic tools for agents (correct)  
c) Managing UV dependencies  
d) Disabling tracing  

**Explanation**: The `06_basic_tools` section teaches how to implement basic tools for AI agents.

---

**Q32. What is a common example of a tool in `06_basic_tools`?**  
a) A weather fetching tool (correct)  
b) A database management tool  
c) A UV configuration tool  
d) A FastAPI server tool  

**Explanation**: Weather fetching is a common example used to demonstrate tool creation.

---

**Q33. How is a basic tool typically defined in `06_basic_tools`?**  
a) Using the `clone` method  
b) Using the `@function_tool` decorator (correct)  
c) Using the `as_tool` method  
d) Using the `run` method  

**Explanation**: The `@function_tool` decorator is used to define basic tools, as in the OpenAI SDK.

---

**Q34. What is the purpose of tools in the `06_basic_tools` context?**  
a) To manage virtual environments  
b) To enable agents to perform specific tasks (correct)  
c) To disable asynchronous execution  
d) To generate JSON schemas  

**Explanation**: Tools allow agents to perform tasks like fetching data or running code.

---

**Q35. What Python library is used for environment variables in `06_basic_tools`?**  
a) `json`  
b) `dotenv` (correct)  
c) `pydantic`  
d) `griffe`  

**Explanation**: `dotenv` is used to load environment variables, as in the provided code.

---

**Q36. What is the role of `asyncio` in `06_basic_tools` examples?**  
a) To manage dependencies  
b) To enable asynchronous tool execution (correct)  
c) To generate schemas  
d) To disable tracing  

**Explanation**: `asyncio` supports async execution of tools and agent runs.

---

**Q37. What is a typical input for a weather tool in `06_basic_tools`?**  
a) A Python version  
b) A city name (correct)  
c) An API key  
d) A model name  

**Explanation**: A weather tool typically takes a city name as input, as in `get_weather`.

---

**Q38. How does `06_basic_tools` ensure API key security?**  
a) By hardcoding the key  
b) By using a `.env` file (correct)  
c) By generating a key dynamically  
d) By disabling the key  

**Explanation**: API keys are stored in a `.env` file for security, loaded via `dotenv`.

---

**Q39. What is the output of a basic tool in `06_basic_tools`?**  
a) A JSON object  
b) A string (correct)  
c) A dictionary  
d) A list  

**Explanation**: Basic tools, like `get_weather`, return a string output.

---

**Q40. How are tools integrated into agents in `06_basic_tools`?**  
a) Through the `model` parameter  
b) Through the `tools` parameter (correct)  
c) Through the `instructions` parameter  
d) Through the `name` parameter  

**Explanation**: Tools are added to the `tools` parameter in the `Agent` class.

---

**Q41. What is the benefit of using basic tools in `06_basic_tools`?**  
a) They disable agent execution  
b) They add specific functionalities to agents (correct)  
c) They manage UV dependencies  
d) They generate API endpoints  

**Explanation**: Tools enhance agents by adding task-specific capabilities.

---

**Q42. What is a common use case for tools in `06_basic_tools`?**  
a) Managing FastAPI servers  
b) Fetching external data like weather (correct)  
c) Disabling tracing  
d) Generating virtual environments  

**Explanation**: Fetching weather data is a common example in `06_basic_tools`.

---

**Q43. How does `06_basic_tools` support UV integration?**  
a) By generating UV lockfiles  
b) By using UV to manage dependencies (correct)  
c) By disabling UV functionality  
d) By replacing UV with pip  

**Explanation**: UV manages dependencies like `openai-agents` for the project.

---

**Q44. What is the role of the docstring in a basic tool?**  
a) To disable the tool  
b) To describe the tool’s purpose (correct)  
c) To generate API keys  
d) To manage tracing  

**Explanation**: The docstring provides the tool’s description and argument details.

---

**Q45. Why is `Runner.run` used in `06_basic_tools`?**  
a) To install dependencies  
b) To execute the agent with tools (correct)  
c) To generate schemas  
d) To disable async execution  

**Explanation**: `Runner.run` executes the agent, invoking tools as needed.

---

**Q46. What is a key feature of function tools in `06_basic_tools`?**  
a) Manual schema creation  
b) Automatic schema generation (correct)  
c) Disabling docstring parsing  
d) Synchronous execution only  

**Explanation**: The SDK automatically generates schemas from function signatures.

---

**Q47. How does `06_basic_tools` handle async functions?**  
a) By disabling them  
b) By supporting both sync and async functions (correct)  
c) By converting them to sync functions  
d) By generating new functions  

**Explanation**: Function tools can be sync or async, as shown in `fetch_weather`.

---

**Q48. What is the purpose of the `tools` list in `06_basic_tools`?**  
a) To disable agent execution  
b) To specify tools the agent can use (correct)  
c) To manage environment variables  
d) To generate API keys  

**Explanation**: The `tools` list defines tools available to the agent.

---

**Q49. How does `06_basic_tools` align with FastAPI?**  
a) By replacing FastAPI servers  
b) By supporting async tool execution (correct)  
c) By disabling API endpoints  
d) By managing FastAPI dependencies  

**Explanation**: Async tool execution is compatible with FastAPI’s async framework.

---

**Q50. What is the final output in `06_basic_tools` examples?**  
a) The API key  
b) The agent’s response with tool output (correct)  
c) The model configuration  
d) The `.env` file contents  

**Explanation**: The agent’s response includes tool outputs, like weather data.

---

**Q51. Why is `pydantic` used in `06_basic_tools`?**  
a) To manage async tasks  
b) To create JSON schemas for tools (correct)  
c) To disable tracing  
d) To generate API endpoints  

**Explanation**: `pydantic` generates JSON schemas for tool arguments.

---

**Q52. What is a typical tool example in `06_basic_tools`?**  
a) A file reading tool (correct)  
b) A UV configuration tool  
c) A database management tool  
d) A FastAPI server tool  

**Explanation**: File reading is a common tool example, alongside weather fetching.

---

**Q53. How does `06_basic_tools` ensure tool reusability?**  
a) By disabling tools  
b) By using the `@function_tool` decorator (correct)  
c) By generating new agents  
d) By managing dependencies  

**Explanation**: The `@function_tool` decorator makes functions reusable as tools.

---

**Q54. What is the role of `RunContextWrapper` in `06_basic_tools`?**  
a) To generate API keys  
b) To pass context to tools (correct)  
c) To disable docstring parsing  
d) To manage tracing  

**Explanation**: `RunContextWrapper` provides context to tools during execution.

---

**Q55. How does `06_basic_tools` support learning agentic AI?**  
a) By disabling agent execution  
b) By providing practical tool examples (correct)  
c) By generating UV lockfiles  
d) By replacing FastAPI  

**Explanation**: Practical examples like `get_weather` teach tool creation.

---

**Q56. What is the input type for a weather tool in `06_basic_tools`?**  
a) A JSON object  
b) A string (correct)  
c) A dictionary  
d) A list  

**Explanation**: The weather tool typically takes a string (e.g., city name) as input.

---

**Q57. How are tool descriptions generated in `06_basic_tools`?**  
a) From API endpoints  
b) From function docstrings (correct)  
c) From agent instructions  
d) From UV configurations  

**Explanation**: Tool descriptions are derived from function docstrings.

---

**Q58. What is the benefit of automatic schema generation in `06_basic_tools`?**  
a) It disables tool execution  
b) It simplifies tool creation (correct)  
c) It generates API keys  
d) It manages dependencies  

**Explanation**: Automatic schema generation reduces manual configuration.

---

**Q59. How does `06_basic_tools` handle tool errors?**  
a) By disabling the tool  
b) By using `failure_error_function` (correct)  
c) By generating new tools  
d) By stopping the agent  

**Explanation**: `failure_error_function` handles errors during tool execution.

---

**Q60. Why is the `tools` parameter important in `06_basic_tools`?**  
a) It disables async execution  
b) It enables task-specific functionality (correct)  
c) It generates API endpoints  
d) It manages UV dependencies  

**Explanation**: The `tools` parameter allows agents to perform specific tasks.

## Section 3: Panaversity Learn-Agentic-AI Tools and Agents as Tools (08_tools, 09_agents_as_tool) (30 MCQs)

**Q61. What is the focus of the `08_tools` section in `learn-agentic-ai`?**  
a) Generating API keys  
b) Advanced tool implementation (correct)  
c) Managing UV dependencies  
d) Disabling tracing  

**Explanation**: The `08_tools` section covers advanced tool creation and configuration.

---

**Q62. What is a key feature of `09_agents_as_tool`?**  
a) Disabling agent execution  
b) Using agents as tools for other agents (correct)  
c) Generating JSON schemas  
d) Managing FastAPI servers  

**Explanation**: The `09_agents_as_tool` section focuses on agents acting as tools.

---

**Q63. How is an agent used as a tool in `09_agents_as_tool`?**  
a) Using the `clone` method  
b) Using the `as_tool` method (correct)  
c) Using the `run` method  
d) Using the `connect` method  

**Explanation**: The `as_tool` method converts an agent into a tool for another agent.

---

**Q64. What is an example of a tool in `08_tools`?**  
a) A UV configuration tool  
b) A file reading tool (correct)  
c) A FastAPI server tool  
d) A database management tool  

**Explanation**: File reading is a common advanced tool example in `08_tools`.

---

**Q65. What is the purpose of `custom_output_extractor` in `09_agents_as_tool`?**  
a) To disable tool output  
b) To modify agent-tool output (correct)  
c) To generate API keys  
d) To manage tracing  

**Explanation**: `custom_output_extractor` reformats or validates the output of an agent used as a tool.

---

**Q66. How does `08_tools` handle complex argument types?**  
a) By ignoring them  
b) By using type annotations (correct)  
c) By converting them to strings  
d) By disabling them  

**Explanation**: Complex types like `TypedDict` are supported via type annotations.

---

**Q67. What is the role of the `orchestrator_agent` in `09_agents_as_tool`?**  
a) To disable tool execution  
b) To coordinate specialized agent-tools (correct)  
c) To generate API endpoints  
d) To manage UV dependencies  

**Explanation**: The `orchestrator_agent` manages agent-tools, like translation agents.

---

**Q68. What is a common use case in `09_agents_as_tool`?**  
a) Managing FastAPI servers  
b) Translating text using agent-tools (correct)  
c) Disabling tracing  
d) Generating UV lockfiles  

**Explanation**: Translation (e.g., Spanish or French) is a common example.

---

**Q69. How does `08_tools` support error handling?**  
a) By disabling tools  
b) By using `failure_error_function` (correct)  
c) By generating new tools  
d) By stopping the agent  

**Explanation**: `failure_error_function` provides error responses for tool failures.

---

**Q70. What is the output of an agent-tool in `09_agents_as_tool`?**  
a) A JSON object  
b) A string (correct)  
c) A dictionary  
d) A list  

**Explanation**: Agent-tools return a string, as seen in translation examples.

---

**Q71. Why is `as_tool` used in `09_agents_as_tool`?**  
a) To disable agent execution  
b) To allow one agent to call another (correct)  
c) To generate schemas  
d) To manage dependencies  

**Explanation**: `as_tool` enables one agent to use another as a tool without handoff.

---

**Q72. What is a limitation of `as_tool` in `09_agents_as_tool`?**  
a) It cannot set `max_turns` (correct)  
b) It disables async execution  
c) It requires manual schemas  
d) It prevents tool execution  

**Explanation**: The `as_tool` method does not support advanced settings like `max_turns`.

---

**Q73. How does `08_tools` ensure tool modularity?**  
a) By disabling tools  
b) By using `@function_tool` (correct)  
c) By generating new agents  
d) By managing FastAPI servers  

**Explanation**: The `@function_tool` decorator creates modular, reusable tools.

---

**Q74. What is the role of `RunContextWrapper` in `08_tools`?**  
a) To generate API keys  
b) To provide context to tools (correct)  
c) To disable tracing  
d) To manage schemas  

**Explanation**: `RunContextWrapper` passes context to tools during execution.

---

**Q75. How does `09_agents_as_tool` support multi-agent systems?**  
a) By disabling agents  
b) By orchestrating agent-tools (correct)  
c) By generating UV lockfiles  
d) By replacing FastAPI  

**Explanation**: It enables a central agent to orchestrate specialized agent-tools.

---

**Q76. What is the benefit of using agents as tools in `09_agents_as_tool`?**  
a) Simplifies dependency management  
b) Enables modular task delegation (correct)  
c) Disables async execution  
d) Generates API endpoints  

**Explanation**: Agent-tools allow modular task delegation without handoffs.

---

**Q77. How does `08_tools` align with FastAPI?**  
a) By replacing FastAPI servers  
b) By supporting async tool execution (correct)  
c) By disabling API endpoints  
d) By managing FastAPI dependencies  

**Explanation**: Async tools are compatible with FastAPI’s async framework.

---

**Q78. What is the purpose of docstrings in `08_tools`?**  
a) To disable tool execution  
b) To describe tool functionality (correct)  
c) To generate API keys  
d) To manage tracing  

**Explanation**: Docstrings provide descriptions for tools and their arguments.

---

**Q79. How does `09_agents_as_tool` handle output formatting?**  
a) By disabling output  
b) By using `custom_output_extractor` (correct)  
c) By generating new agents  
d) By managing dependencies  

**Explanation**: `custom_output_extractor` formats or validates agent-tool output.

---

**Q80. What is a typical agent-tool in `09_agents_as_tool`?**  
a) A UV configuration tool  
b) A translation agent (correct)  
c) A FastAPI server tool  
d) A database management tool  

**Explanation**: Translation agents (e.g., Spanish or French) are common examples.

---

**Q81. How does `08_tools` support UV integration?**  
a) By generating UV lockfiles  
b) By using UV to manage dependencies (correct)  
c) By disabling UV functionality  
d) By replacing UV with pip  

**Explanation**: UV manages dependencies like `openai-agents` for the project.

---

**Q82. What is the role of `Runner.run` in `09_agents_as_tool`?**  
a) To install dependencies  
b) To execute the orchestrator agent (correct)  
c) To generate schemas  
d) To disable async execution  

**Explanation**: `Runner.run` executes the orchestrator agent with its tools.

---

**Q83. Why is `pydantic` used in `08_tools`?**  
a) To manage async tasks  
b) To create JSON schemas for tools (correct)  
c) To disable tracing  
d) To generate API endpoints  

**Explanation**: `pydantic` generates JSON schemas for tool arguments.

---

**Q84. How does `09_agents_as_tool` ensure modularity?**  
a) By disabling agents  
b) By using agents as tools (correct)  
c) By generating new schemas  
d) By managing FastAPI servers  

**Explanation**: Using agents as tools promotes modular task delegation.

---

**Q85. What is the output of a translation agent-tool in `09_agents_as_tool`?**  
a) A JSON object  
b) A translated string (correct)  
c) A dictionary  
d) A list  

**Explanation**: Translation agent-tools return translated text as strings.

---

**Q86. How does `08_tools` handle synchronous functions?**  
a) By disabling them  
b) By supporting both sync and async functions (correct)  
c) By converting them to async  
d) By generating new functions  

**Explanation**: Function tools support both sync and async functions.

---

**Q87. What is the benefit of automatic schema generation in `08_tools`?**  
a) It disables tool execution  
b) It simplifies tool creation (correct)  
c) It generates API keys  
d) It manages dependencies  

**Explanation**: Automatic schema generation reduces manual configuration.

---

**Q88. How does `09_agents_as_tool` handle errors in agent-tools?**  
a) By disabling the agent  
b) By using `failure_error_function` (correct)  
c) By generating new tools  
d) By stopping the agent  

**Explanation**: `failure_error_function` handles errors in agent-tool execution.

---

**Q89. What is the role of the `tools` parameter in `09_agents_as_tool`?**  
a) To disable async execution  
b) To specify agent-tools for the orchestrator (correct)  
c) To generate API endpoints  
d) To manage UV dependencies  

**Explanation**: The `tools` parameter defines agent-tools for the orchestrator agent.

---

**Q90. Why is the `orchestrator_agent` important in `09_agents_as_tool`?**  
a) It disables tool execution  
b) It coordinates specialized agent-tools (correct)  
c) It generates JSON schemas  
d) It manages tracing  

**Explanation**: The `orchestrator_agent` manages and invokes specialized agent-tools.
