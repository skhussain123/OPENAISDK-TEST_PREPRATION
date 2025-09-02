# MCQs: Agent Tooling and Behavior

## 1. `tool_use_behavior` – Direct Tool Output

1.  What is the primary purpose of the `tool_use_behavior` parameter in an `Agent`?
    A) To set the Agent's name.
    B) To dictate what happens after a tool is successfully executed. [1]
    C) To choose an LLM model.
    D) To configure the list of available tools.
    **Correct Answer: B**

2.  What is the default value for `tool_use_behavior`?
    A) `"stop_on_first_tool"` [1]
    B) `"run_llm_again"` [1]
    C) `"process_tool_output"`
    D) `"default"`
    **Correct Answer: B**

3.  In `"run_llm_again"` mode, what happens after a tool is successfully executed?
    A) Its output is sent directly to the user.
    B) Its output is sent back to the LLM for analysis and to decide what to do next. [1]
    C) Execution stops immediately.
    D) The Agent selects and executes a new tool.
    **Correct Answer: B**

4.  How do `"run_llm_again"` and `"stop_on_first_tool"` differ regarding LLM involvement?
    A) In both, the LLM always analyzes the tool output.
    B) In `"run_llm_again"`, the LLM analyzes tool output, whereas in `"stop_on_first_tool"`, it does not. [1]
    C) In `"stop_on_first_tool"`, the LLM analyzes tool output, whereas in `"run_llm_again"`, it does not.
    D) `"run_llm_again"` runs only one tool, while `"stop_on_first_tool"` runs multiple.
    **Correct Answer: B**

5.  What is the Agent's behavior when `tool_use_behavior` is set to `"stop_on_first_tool"`?
    A) The Agent runs all available tools and combines their outputs.
    B) Execution stops immediately after the first tool call, and its raw output becomes the Agent's final answer. [1]
    C) The Agent runs the first tool, then sends the output to the LLM for analysis.
    D) The Agent prompts the user for the next tool.
    **Correct Answer: B**

6.  If `tool_use_behavior` is `"stop_on_first_tool"`, and a user prompt triggers two tool calls, what will be the final output?
    A) The combined output of both tools.
    B) Only the output of the first tool.
    C) Only the output of the second tool.
    D) No output, as it would be an error.
    **Correct Answer: B**

7.  Which mode ensures that the LLM analyzes the result of a tool before deciding on the next action?
    A) `"stop_on_first_tool"`
    B) `"run_llm_again"` [1]
    C) `"direct_tool_output"`
    D) `"process_and_stop"`
    **Correct Answer: B**

8.  Which `tool_use_behavior` mode returns the raw output of the tool as the Agent's final answer?
    A) `"run_llm_again"`
    B) `"analyze_output"`
    C) `"stop_on_first_tool"` [1]
    D) `"continue_processing"`
    **Correct Answer: C**

9.  Consider an Agent with `tool_use_behavior="stop_on_first_tool"` and two tools, `toolA` and `toolB`. If `toolA` is triggered first, what happens to the potential execution of `toolB`?
    A) `toolB` also executes, and its output is combined with `toolA`'s.
    B) `toolB` does not execute.
    C) `toolB` executes, but its output is ignored.
    D) The Agent asks the user for confirmation before running `toolB`.
    **Correct Answer: B**

10. If an Agent's `tool_use_behavior` is not explicitly set, what will its default mode be?
    A) `"stop_on_first_tool"`
    B) `"run_llm_again"` [1]
    C) `"continue_llm_processing"`
    D) `"automatic_selection"`
    **Correct Answer: B**

## 2. `StopAtTools` – Stopping at Specific Tools

11. What is `StopAtTools`?
    A) A boolean parameter to enable/disable all tools.
    B) A TypedDict that accepts a list of `stop_at_tool_names`.
    C) A function to define custom error handling.
    D) A parameter to specify the LLM model.
    **Correct Answer: B**

12. What does `stop_at_tool_names` within `StopAtTools` represent?
    A) A list of tools that should always be enabled.
    B) A list of tool names that, if called by the Agent, will stop its execution and use that tool's output as the final response. [1]
    C) A list of tools that should be hidden from the LLM.
    D) A list of tools that require human approval before execution.
    **Correct Answer: B**

13. When `StopAtTools` is configured, and a specified tool is called, what happens regarding LLM processing?
    A) The Agent calls the LLM again to process the tool's output.
    B) The Agent passes the tool's output to another tool.
    C) The Agent uses the tool's output directly as the final response, without further LLM processing. [1]
    D) The LLM decides whether to process the output or not.
    **Correct Answer: C**

14. Which of the following is an accurate description of `StopAtTools` behavior?
    A) It allows the LLM to decide when to stop after any tool call.
    B) It forces the LLM to process all tool outputs before responding.
    C) It explicitly designates certain tools whose outputs will be the final response, bypassing further LLM steps.
    D) It is primarily used for logging tool execution.
    **Correct Answer: C**

15. If an Agent has `tool_use_behavior=StopAtTools(stop_at_tool_names=["get_weather"])` and the user asks a finance question that calls `finance_query_resolver`, what will happen?
    A) The `get_weather` tool will be called instead.
    B) The `finance_query_resolver` tool will be called, and its output will be the final response.
    C) The `finance_query_resolver` tool will be called, and the LLM will then process its output.
    D) An error will occur because `finance_query_resolver` is not in the `stop_at_tool_names` list.
    **Correct Answer: C**
    (The text implies that if a tool *not* in `stop_at_tool_names` is called, the default `run_llm_again` behavior, or rather, continued LLM processing, would apply unless another `tool_use_behavior` or tool-specific stopping condition is met. The example only shows what happens if a tool *in* the list is called.)

16. What is the benefit of using `StopAtTools`?
    A) It makes all tools dynamically available.
    B) It simplifies complex multi-step reasoning by forcing the LLM to always continue.
    C) It provides a mechanism for direct output of specific tool results, optimizing response flow for certain queries. [1]
    D) It ensures all tools handle errors gracefully.
    **Correct Answer: C**

17. In the given `StopAtTools` example, if the user asks "What's the weather in Karachi?", what will `result.final_output` contain?
    A) A response from the LLM summarizing the weather.
    B) The direct output from the `get_weather` tool: "The weather in Karachi is sunny".
    C) An error message.
    D) The output from the `finance_query_resolver` tool.
    **Correct Answer: B**

18. `StopAtTools` is a specialized form of `tool_use_behavior` that allows for:
    A) More complex LLM-driven decision making.
    B) Bypassing the LLM for specific, pre-determined tool outputs. [1]
    C) Only allowing tools with `is_enabled=True`.
    D) Global error handling for all tools.
    **Correct Answer: B**

19. If `StopAtTools` is used, and multiple tools from the `stop_at_tool_names` list are conceptually applicable to a user's prompt, which tool's output will be the final answer if the LLM decides to call one?
    A) All applicable tools' outputs will be combined.
    B) The output of the first tool *called by the LLM* that is in the `stop_at_tool_names` list. [1]
    C) The output of the last tool called.
    D) The LLM will ask the user to choose.
    **Correct Answer: B**

20. What type of Python object is `StopAtTools` typically?
    A) A `function`.
    B) A `class`.
    C) A `TypedDict`.
    D) A `list`.
    **Correct Answer: C**

## 3. Making Tools Appear & Disappear (`is_enabled`)

21. What is the default value for the `is_enabled` parameter in `@function_tool`?
    A) `False`
    B) `None`
    C) `True`
    D) It depends on the context.
    **Correct Answer: C**

22. When `is_enabled` is `True`, what does it imply for the tool?
    A) The tool is always hidden from the Agent and LLM.
    B) The tool is always available for the Agent and LLM to use.
    C) The tool requires explicit user permission to be used.
    D) The tool will only run once.
    **Correct Answer: B**

23. What happens if `is_enabled` is set to `False` for a tool?
    A) The tool will still be available but will return an error if called.
    B) The tool will be completely hidden from the Agent and LLM, preventing the LLM from calling it.
    C) The tool will be available, but the LLM will prioritize other tools.
    D) The tool will be marked as deprecated.
    **Correct Answer: B**

24. What is the advantage of using a function (callable) for the `is_enabled` parameter?
    A) It makes the tool always available, regardless of conditions.
    B) It allows for static configuration of tool availability.
    C) It enables dynamic enabling or disabling of the tool based on context-specific logic. [5]
    D) It forces the LLM to call the tool regardless of its availability.
    **Correct Answer: C**

25. In the `is_enabled Dynamic On/Off Switch` example, what is the role of `UserData(user_role='admin')`?
    A) It defines the instructions for the Agent.
    B) It sets the model for the Agent.
    C) It provides the context object (`ctx`) that the `is_user_admin` function can access.
    D) It is the input for the `delete_user_database` tool.
    **Correct Answer: C**

26. If the `user_role` in `UserData` is `'guest'` instead of `'admin'` in the `is_enabled` dynamic example, and the user asks to delete the database, what will happen?
    A) The `delete_user_database` tool will still be called.
    B) The `delete_user_database` tool will be hidden from the LLM, and it won't be called. [5]
    C) The tool will be called, but it will return an error.
    D) The Agent will ask for admin credentials.
    **Correct Answer: B**

27. The `is_enabled` parameter can accept which types of values?
    A) Only boolean values (`True`/`False`). [5]
    B) Only callable functions. [5]
    C) Boolean values, callable functions, or async functions. [5]
    D) Only strings representing the tool's state.
    **Correct Answer: C**

28. When a tool is `is_enabled=False`, it is considered:
    A) Active but with low priority.
    B) Hidden from the LLM at runtime. [5]
    C) Deprecated.
    D) In a testing phase.
    **Correct Answer: B**

29. What is a practical use case for dynamic `is_enabled` based on context?
    A) Changing the tool's name at runtime.
    B) Feature gating based on user permissions. [5]
    C) Overriding the tool's description.
    D) Modifying the tool's input schema.
    **Correct Answer: B**

30. How does the `RunContextWrapper` facilitate dynamic `is_enabled` logic?
    A) It directly executes the tool.
    B) It provides access to runtime context data (like `user_role`) to the `is_enabled` function.
    C) It handles error messages for disabled tools.
    D) It manages the LLM's decision-making process.
    **Correct Answer: B**

## 4. Graceful Error Handling (Basic `try-except`)

31. What is the main purpose of `Graceful Error Handling` in the context of tools?
    A) To prevent the LLM from making mistakes.
    B) To ensure tools always return a successful output.
    C) To manage and respond to errors in a controlled and user-friendly way, rather than crashing. [3]
    D) To speed up tool execution.
    **Correct Answer: C**

32. In the `divide` tool example, what specific error is being handled?
    A) `TypeError`
    B) `ValueError`
    C) `ZeroDivisionError`
    D) `IOError`
    **Correct Answer: C**

33. If `divide(10, 0)` is called using the provided code, what will be the return value?
    A) `ZeroDivisionError` will be raised.
    B) `"Error: You cannot divide by zero. Please ask for a different number."`
    C) `None`
    D) The program will crash.
    **Correct Answer: B**

34. Why is it important to handle exceptions like `ZeroDivisionError` within a tool?
    A) To prevent the LLM from seeing any errors.
    B) To ensure the tool provides a meaningful and actionable response to the Agent (and potentially the user) when an expected issue occurs. [3, 4]
    C) To make the tool run faster.
    D) To bypass the LLM entirely.
    **Correct Answer: B**

35. What is `try-except` block used for in Python?
    A) To define new functions.
    B) To declare variables.
    C) To catch and handle exceptions that might occur during the execution of a block of code.
    D) To iterate over a list.
    **Correct Answer: C**

36. Without the `try-except` block in the `divide` tool, what would typically happen if `b` was `0`?
    A) The function would return `None`.
    B) Python would raise a `ZeroDivisionError`, potentially crashing the program or the Agent's workflow.
    C) The LLM would automatically correct the input.
    D) The Agent would retry the tool call with different parameters.
    **Correct Answer: B**

37. What makes error handling in agentic systems particularly critical?
    A) Agents always deal with perfect information.
    B) Tool interactions often involve external systems that operate outside the agent's core logic and can fail. [3]
    C) LLMs are incapable of understanding any errors.
    D) Only mathematical operations can fail.
    **Correct Answer: B**

38. Which of the following is NOT a typical source of tool execution errors?
    A) Network and Connectivity issues. [3]
    B) External Service Errors (e.g., API returning 4xx/5xx). [3]
    C) Tool's internal logic errors (bugs). [3]
    D) The LLM always providing perfect, valid inputs.
    **Correct Answer: D**

39. What is the goal of error handling in LLM agent tools?
    A) To prevent the LLM from generating tool calls.
    B) To prevent the tool from crashing uncontrollably and to provide the LLM with enough information to understand the failure. [4]
    C) To ensure every tool call succeeds.
    D) To remove the need for LLM involvement after a tool call.
    **Correct Answer: B**

40. When `Graceful Degradation` is mentioned in error handling, what does it refer to?
    A) The system completely shutting down on error.
    B) The system continuing to function, possibly with reduced capabilities, when errors occur. [4, 13]
    C) The LLM degrading its performance.
    D) Tools becoming permanently disabled after an error.
    **Correct Answer: B**

## 5. Custom Error With `failure_error_function`

41. What is `failure_error_function`?
    A) A mandatory parameter for every `@function_tool`.
    B) An optional parameter that defines a custom function to handle tool errors and provide a specific error message to the LLM. [5]
    C) A global error handler for all Agent operations.
    D) A function that prevents any tool from failing.
    **Correct Answer: B**

42. When does the `failure_error_function` get executed?
    A) Before the tool function is called.
    B) After the tool function returns successfully.
    C) When the tool function throws an error (e.g., an exception). [5]
    D) Only if the LLM requests an error message.
    **Correct Answer: C**

43. If a `failure_error_function` is *not* specified for a tool, what happens by default?
    A) The tool crashes, and no message is sent to the LLM.
    B) The SDK uses a `default_tool_error_function` which returns a generic error message to the LLM. [5]
    C) The LLM automatically retries the tool call.
    D) The error is re-raised and handled by the Agent's top-level error handling.
    **Correct Answer: B**

44. What happens if you explicitly set `failure_error_function=None`?
    A) The `default_tool_error_function` is still used.
    B) The tool's output will be `None`.
    C) Errors will be re-raised (the tool will crash, and a fallback message will not be generated for the LLM). [5]
    D) The LLM will ignore any errors.
    **Correct Answer: C**

45. In the `custom_error_handler` example, what is the purpose of `ctx: RunContextWrapper[Any]`?
    A) It's the output of the tool.
    B) It's the error that occurred.
    C) It provides access to the current run context, which can contain shared data or state. [5]
    D) It's used to define the tool's parameters.
    **Correct Answer: C**

46. What does the `custom_error_handler` function in the example return?
    A) An `Exception` object.
    B) A boolean indicating success or failure.
    C) A formatted string message that will be sent to the LLM. [5]
    D) The original input `x`.
    **Correct Answer: C**

47. The `broken_tool` in the example is designed to:
    A) Always return `1 / 0`.
    B) Always return `0`.
    C) Always raise a `ZeroDivisionError`.
    D) Always raise an arbitrary error, specifically by attempting `1 / 0`.
    **Correct Answer: D**

48. When `broken_tool` is called in `assistant_agent` with `failure_error_function=custom_error_handler`, what will `result.final_output` contain?
    A) A `ZeroDivisionError` object.
    B) `"Oops! Something went wrong: division by zero"`.
    C) The default generic error message.
    D) `None`, because the tool crashes.
    **Correct Answer: B**

49. What is a key benefit of providing a custom `failure_error_function` over the default error handling?
    A) It completely hides the error from the LLM.
    B) It allows for more specific, user-friendly, or LLM-actionable error messages. [3, 4]
    C) It makes the tool execution faster.
    D) It changes the tool's input schema.
    **Correct Answer: B**

50. The `failure_error_function` takes an `error: Exception` parameter. What does this parameter represent?
    A) The expected error type.
    B) The actual exception object that was raised by the tool. [5]
    C) A custom error message predefined by the user.
    D) A boolean indicating if an error occurred.
    **Correct Answer: B**

## General Agent Tooling Concepts

51. What is the purpose of `instructions` in an `Agent`?
    A) To list all available tools.
    B) To define the LLM model.
    C) To provide a system prompt that guides the model's behavior, defining its role, tone, and task boundaries. [17]
    D) To set the Agent's name.
    **Correct Answer: C**

52. Which of the following is NOT a core component of an `Agent` as discussed in the context?
    A) `name`
    B) `instructions`
    C) `database_connection`
    D) `model`
    **Correct Answer: C**

53. How does the Agents SDK generally determine the name of a `function_tool` if not explicitly provided?
    A) It uses a default generic name.
    B) It takes the name of the Python function. [5]
    C) It asks the user for a name.
    D) It randomly generates a name.
    **Correct Answer: B**

54. The description for a `function_tool` is typically derived from its:
    A) Function signature.
    B) Docstring. [5]
    C) Return type.
    D) Parameter names.
    **Correct Answer: B**

55. `RunContextWrapper` is mentioned in several sections. What is its general role?
    A) It wraps the Agent's final output.
    B) It provides a mechanism for dependency injection, passing context-specific data and state throughout the Agent's execution. [5, 6]
    C) It solely handles error messages.
    D) It defines the Agent's model.
    **Correct Answer: B**

56. When designing tools for an Agent, what is a crucial aspect to consider for robustness?
    A) Always making the tool `is_enabled=True`.
    B) Minimizing the number of parameters.
    C) Anticipating potential failures and implementing error handling (e.g., `try-except` blocks). [3, 4, 13]
    D) Ensuring the tool always returns a string.
    **Correct Answer: C**

57. If an Agent's workflow involves multiple steps, some of which are conditional based on external data or user roles, which tooling feature would be most relevant for managing tool availability?
    A) `tool_use_behavior="stop_on_first_tool"`
    B) `failure_error_function`
    C) Dynamic `is_enabled` with a callable function.
    D) `StopAtTools`
    **Correct Answer: C**

58. What is a key principle for effective error handling in agentic AI systems?
    A) Ignoring all errors to maintain flow.
    B) Preventing any tool from ever failing.
    C) Providing informative error messages back to the LLM so it can understand and potentially act upon the failure. [3, 4]
    D) Relying solely on the default error messages.
    **Correct Answer: C**

59. The `Agent` class constructor requires which of these parameters as fundamental?
    A) `tools` and `tool_use_behavior`
    B) `name`, `instructions`, and `model` [1]
    C) `RunContextWrapper` and `external_client`
    D) `StopAtTools` and `is_enabled`
    **Correct Answer: B**

60. Why might a developer choose to set `failure_error_function=None` for a tool?
    A) To make the tool run silently without any error indications.
    B) To allow lower-level exceptions to propagate, giving more granular control to higher-level error handling mechanisms in their application. [5]
    C) To always return a successful output.
    D) To automatically retry the tool call indefinitely.
    **Correct Answer: B**