# 60 MCQs on OpenAI Agents SDK Tools

Below are 60 multiple-choice questions (MCQs) based on the OpenAI Agents SDK tools, covering hosted tools, function calling, and agents as tools. Each question includes four options, with the correct answer marked.

---

## Hosted Tools

1. **What are hosted tools in the OpenAI Agents SDK?**  
   a) Tools running on local machines  
   b) Tools running on LLM servers with AI models  
   c) Tools requiring external APIs only  
   d) Tools limited to Python functions  
   **Answer: b)**

2. **Which is a hosted tool in the OpenAI Agents SDK?**  
   a) FunctionTool  
   b) WebSearchTool  
   c) PythonFunctionTool  
   d) CustomAgentTool  
   **Answer: b)**

3. **What does the WebSearchTool allow an agent to do?**  
   a) Execute code in a sandbox  
   b) Search the web for information  
   c) Retrieve local file data  
   d) Generate images from prompts  
   **Answer: b)**

4. **Which tool retrieves information from OpenAI Vector Stores?**  
   a) CodeInterpreterTool  
   b) FileSearchTool  
   c) LocalShellTool  
   d) ImageGenerationTool  
   **Answer: b)**

5. **What is the purpose of the ComputerTool?**  
   a) Automates computer tasks  
   b) Generates images  
   c) Runs shell commands locally  
   d) Calls external APIs  
   **Answer: a)**

6. **Which tool executes code in a sandboxed environment?**  
   a) WebSearchTool  
   b) CodeInterpreterTool  
   c) HostedMCPTool  
   d) FileSearchTool  
   **Answer: b)**

7. **What does the HostedMCPTool do?**  
   a) Generates images from prompts  
   b) Exposes remote MCP server tools  
   c) Runs local shell commands  
   d) Searches the web  
   **Answer: b)**

8. **Which tool runs shell commands on the user’s machine?**  
   a) LocalShellTool  
   b) FileSearchTool  
   c) WebSearchTool  
   d) CodeInterpreterTool  
   **Answer: a)**

9. **What is the role of the ImageGenerationTool?**  
   a) Retrieves vector store data  
   b) Generates images from prompts  
   c) Executes Python functions  
   d) Automates computer tasks  
   **Answer: b)**

10. **Which is NOT a hosted tool?**  
    a) WebSearchTool  
    b) FileSearchTool  
    c) FunctionTool  
    d) ComputerTool  
    **Answer: c)**

---

## Function Tools / Function Calling

11. **How is a Python function converted into a tool?**  
    a) By adding a docstring  
    b) Using the `@function_tool` decorator  
    c) Defining a JSON schema manually  
    d) Registering in the OpenAI dashboard  
    **Answer: b)**

12. **What is the default name of a function tool?**  
    a) Python function name  
    b) Docstring name  
    c) Random name  
    d) Agent’s name  
    **Answer: a)**

13. **Where is the tool description sourced from by default?**  
    a) Function’s return type  
    b) Function’s docstring  
    c) Agent’s instructions  
    d) Function’s arguments  
    **Answer: b)**

14. **What happens if no docstring is provided for a function tool?**  
    a) Tool fails to initialize  
    b) Description is blank  
    c) Function name becomes description  
    d) Default description generated  
    **Answer: b)**

15. **How is the schema for function inputs created?**  
    a) Manually by developer  
    b) Automatically from function arguments  
    c) From agent configuration  
    d) From docstring only  
    **Answer: b)**

16. **What does the `@function_tool` decorator do?**  
    a) Converts Python function to tool  
    b) Runs function in sandbox  
    c) Generates JSON schema manually  
    d) Registers function with API  
    **Answer: a)**

17. **What is the purpose of `name_override` in `@function_tool`?**  
    a) Overrides return type  
    b) Changes tool name for LLM  
    c) Modifies arguments  
    d) Disables docstring  
    **Answer: b)**

18. **What happens if both docstring and `description_override` are provided?**  
    a) Docstring is used  
    b) `description_override` is used  
    c) Both are combined  
    d) Error is raised  
    **Answer: b)**

19. **What is the default `strict_mode` value in `@function_tool`?**  
    a) False  
    b) True  
    c) None  
    d) Auto  
    **Answer: b)**

20. **What does `use_docstring_info` control?**  
    a) Function argument usage  
    b) Docstring for description and schema  
    c) Tool enablement  
    d) Async function usage  
    **Answer: b)**

21. **What does the LLM read for a function tool?**  
    a) Function body  
    b) Function signature  
    c) Function schema  
    d) Return value  
    **Answer: c)**

22. **Can an async function be used with `@function_tool`?**  
    a) No, only synchronous functions  
    b) Yes, async functions supported  
    c) Only with no arguments  
    d) Only with docstring  
    **Answer: b)**

23. **What is the purpose of `failure_error_function` in `@function_tool`?**  
    a) Handles execution errors  
    b) Overrides return value  
    c) Generates schema  
    d) Disables tool  
    **Answer: a)**

24. **What is the default `is_enabled` value in `@function_tool`?**  
    a) False  
    b) True  
    c) None  
    d) Auto  
    **Answer: b)**

25. **What does `docstring_style` in `@function_tool` control?**  
    a) Return type format  
    b) Docstring parsing style  
    c) Execution environment  
    d) Schema generation  
    **Answer: b)**

---

## Agents as Tools

26. **What is the main difference between handoff and agent as tool?**  
    a) Handoffs don’t use tools  
    b) Handoffs pass history, tools pass input  
    c) Tools pass history, handoffs pass input  
    d) Handoffs are synchronous, tools asynchronous  
    **Answer: b)**

27. **What happens to conversation control in a handoff?**  
    a) Original agent retains control  
    b) New agent takes over  
    c) Both share control  
    d) Conversation terminates  
    **Answer: b)**

28. **What happens when an agent is used as a tool?**  
    a) New agent takes over  
    b) Original agent continues after output  
    c) History is reset  
    d) Tool processes history  
    **Answer: b)**

29. **What is required for the `as_tool` method?**  
    a) `tool_name` and `tool_description`  
    b) `custom_output_extractor` only  
    c) `model` and `instructions`  
    d) `vector_store_ids`  
    **Answer: a)**

30. **What is the default output of an agent as a tool without `custom_output_extractor`?**  
    a) Conversation history  
    b) Last message from agent  
    c) Agent instructions  
    d) JSON schema  
    **Answer: b)**

31. **What is the purpose of `custom_output_extractor` in `as_tool`?**  
    a) Defines tool name  
    b) Extracts and formats output  
    c) Overrides instructions  
    d) Passes history  
    **Answer: b)**

32. **What is passed to an agent used as a tool?**  
    a) Conversation history  
    b) Generated input  
    c) Agent instructions  
    d) Tool schema  
    **Answer: b)**

33. **Why use an agent as a tool instead of a handoff?**  
    a) Retains conversation control  
    b) Passes conversation history  
    c) Terminates conversation  
    d) Disables original agent  
    **Answer: a)**

34. **What happens if `tool_name` is not provided in `as_tool`?**  
    a) Random name used  
    b) Agent’s name used  
    c) Error raised  
    d) Description used  
    **Answer: b)**

35. **What is the role of `tool_description` in `as_tool`?**  
    a) Defines agent instructions  
    b) Describes tool purpose and usage  
    c) Overrides model  
    d) Specifies output format  
    **Answer: b)**

---

## Custom Function Tools

36. **What is required to create a custom FunctionTool?**  
    a) `name`, `description`, `params_json_schema`, `on_invoke_tool`  
    b) `tool_name` and `tool_description` only  
    c) `@function_tool` and Python function  
    d) `vector_store_ids` and `max_num_results`  
    **Answer: a)**

37. **What does `on_invoke_tool` do in a custom FunctionTool?**  
    a) Defines schema  
    b) Processes input and returns output  
    c) Overrides name  
    d) Generates description  
    **Answer: b)**

38. **What is `params_json_schema` in a custom FunctionTool?**  
    a) Schema for arguments  
    b) Schema for output  
    c) Schema for instructions  
    d) Schema for history  
    **Answer: a)**

39. **When should you create a custom FunctionTool instead of `@function_tool`?**  
    a) For Python functions  
    b) Without Python functions  
    c) With docstring  
    d) For async functions  
    **Answer: b)**

40. **What does `ToolContext` provide in a custom FunctionTool?**  
    a) Arguments and execution context  
    b) Conversation history  
    c) JSON schema  
    d) Agent instructions  
    **Answer: a)**

---

## Customizing Tool-Agents

41. **What is the purpose of `max_turns` in `Runner.run`?**  
    a) Limits LLM calls or tool uses  
    b) Defines agent count  
    c) Specifies output format  
    d) Sets history length  
    **Answer: a)**

42. **What is the default `max_turns` value in `Runner.run`?**  
    a) 5  
    b) 10  
    c) 15  
    d) 20  
    **Answer: b)**

43. **What does the `run_my_agent` function do in the tool-agent example?**  
    a) Runs sub-agent with custom config  
    b) Generates JSON schema  
    c) Overrides instructions  
    d) Passes history  
    **Answer: a)**

44. **How is the output of a custom tool-agent returned?**  
    a) As JSON schema  
    b) As string from `result.final_output`  
    c) As argument dictionary  
    d) As conversation history  
    **Answer: b)**

45. **What is the benefit of a custom tool-agent?**  
    a) Runs sub-agent with specific configs  
    b) Disables original agent  
    c) Passes conversation history  
    d) Generates images  
    **Answer: a)**

---

## General Questions

46. **What is the primary purpose of tools in the OpenAI Agents SDK?**  
    a) Replace LLM  
    b) Enable real-world actions  
    c) Generate history  
    d) Disable instructions  
    **Answer: b)**

47. **How many categories are tools divided into?**  
    a) Two  
    b) Three or four  
    c) Five  
    d) Six  
    **Answer: b)**

48. **What is the role of `Runner.run_sync`?**  
    a) Executes agent synchronously  
    b) Generates JSON schema  
    c) Overrides model  
    d) Disables tools  
    **Answer: a)**

49. **What is the purpose of `RunConfig`?**  
    a) Configures model and execution settings  
    b) Defines instructions  
    c) Generates schema  
    d) Overrides history  
    **Answer: a)**

50. **What does `tracing_disabled` in `RunConfig` do?**  
    a) Disables error handling  
    b) Disables execution tracing  
    c) Disables tools  
    d) Disables history  
    **Answer: b)**

51. **What is the role of `handoff_description` in an agent?**  
    a) Describes purpose during handoff  
    b) Overrides tool name  
    c) Generates schema  
    d) Defines output format  
    **Answer: a)**

52. **What happens if a tool fails to execute?**  
    a) Conversation terminates  
    b) `failure_error_function` handles error  
    c) Schema regenerates  
    d) History resets  
    **Answer: b)**

53. **What is the purpose of `external_client` in code examples?**  
    a) Defines instructions  
    b) Provides external API client  
    c) Generates schema  
    d) Overrides history  
    **Answer: b)**

54. **What does `model_provider` in `RunConfig` specify?**  
    a) External API client  
    b) Agent instructions  
    c) Tool schema  
    d) Conversation history  
    **Answer: a)**

55. **What is the benefit of emojis in `transfer_to_Shoping_agent`?**  
    a) Makes output visually distinct  
    b) Overrides schema  
    c) Disables tool  
    d) Resets history  
    **Answer: a)**

56. **What does the `custom_output_extractor` do in `as_tool`?**  
    a) Defines tool name  
    b) Processes and formats agent output  
    c) Overrides agent model  
    d) Passes conversation history  
    **Answer: b)**

57. **What is the default behavior if `custom_output_extractor` is not provided?**  
    a) Returns full history  
    b) Returns last agent message  
    c) Returns JSON schema  
    d) Returns error  
    **Answer: b)**

58. **What is passed to an LLM for a function tool’s execution?**  
    a) Function body  
    b) Function schema  
    c) Function return value  
    d) Agent instructions  
    **Answer: b)**

59. **What is the purpose of the `poetry_agent` in the example?**  
    a) Handles shopping queries  
    b) Writes English poetry  
    c) Manages post-purchase returns  
    d) Searches the web  
    **Answer: b)**

60. **What is the benefit of using agents as tools in a workflow?**  
    a) Terminates conversation  
    b) Centralizes conversation control  
    c) Passes full history to all agents  
    d) Disables original agent  
    **Answer: b)**

---

This `readme.md` file contains 60 MCQs based on the OpenAI Agents SDK tools, covering hosted tools, function calling, agents as tools, and general concepts. Each question has four options with the correct answer marked.