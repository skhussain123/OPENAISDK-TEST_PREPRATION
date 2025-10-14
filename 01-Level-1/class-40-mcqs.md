# 40 Multiple-Choice Questions on OpenAI Agents SDK
---

## Questions

1. **What’s the main advantage of custom tool behavior functions?**  
   a) They reduce memory usage  
   b) They allow flexible control over how tools are executed and processed  
   c) They disable async functionality  
   d) They simplify input validation  
   **Correct Answer**: b) They allow flexible control over how tools are executed and processed  

2. **Which method is used to execute an agent asynchronously?**  
   a) `Runner.run_sync()`  
   b) `Runner.run()`  
   c) `Runner.execute()`  
   d) `Runner.stream_sync()`  
   **Correct Answer**: b) `Runner.run()`  

3. **What’s the purpose of `RunContextWrapper`?**  
   a) To define the agent’s instructions  
   b) To manage and provide access to the runtime context of an agent’s execution  
   c) To validate input schemas  
   d) To stream responses in real-time  
   **Correct Answer**: b) To manage and provide access to the runtime context of an agent’s execution  

4. **What does `Runner.run_sync()` do?**  
   a) Executes an agent asynchronously with streaming  
   b) Executes an agent synchronously, returning a complete response  
   c) Streams responses token-by-token  
   d) Converts an agent into a tool  
   **Correct Answer**: b) Executes an agent synchronously, returning a complete response  

5. **What does `extra="forbid"` do in a Pydantic model config?**  
   a) Allows extra fields in the model  
   b) Prevents extra fields from being included in the model  
   c) Enables non-strict mode  
   d) Disables field validation  
   **Correct Answer**: b) Prevents extra fields from being included in the model  

6. **What’s the main advantage of strict schemas over non-strict?**  
   a) They allow flexible input parsing  
   b) They enforce exact data validation, reducing errors  
   c) They reduce execution time  
   d) They disable guardrails  
   **Correct Answer**: b) They enforce exact data validation, reducing errors  

7. **What happens when you combine `StopAtTools` with multiple tool names?**  
   a) The agent stops after calling any of the specified tools  
   b) The agent ignores the tools  
   c) The agent calls all tools simultaneously  
   d) The agent raises an exception  
   **Correct Answer**: a) The agent stops after calling any of the specified tools  

8. **What is the purpose of `context` in the OpenAI Agents SDK?**  
   a) To define the agent’s name  
   b) To provide additional data or state for the agent’s execution  
   c) To specify the output format  
   d) To set the maximum number of turns  
   **Correct Answer**: b) To provide additional data or state for the agent’s execution  

9. **What’s the key consideration when choosing between different `tool_use_behavior` modes?**  
   a) Memory usage  
   b) The desired balance between performance and control over tool execution  
   c) The agent’s name  
   d) The input format  
   **Correct Answer**: b) The desired balance between performance and control over tool execution  

10. **What information does `handoff_description` provide?**  
    a) The agent’s final output  
    b) A description of the agent’s purpose during handoff to another agent  
    c) The tool’s output schema  
    d) The input validation rules  
    **Correct Answer**: b) A description of the agent’s purpose during handoff to another agent  

11. **What does `ToolsToFinalOutputResult.is_final_output` indicate?**  
    a) Whether the tool call was successful  
    b) Whether the tool’s output is the final result of the agent’s execution  
    c) Whether the agent’s context has been updated  
    d) Whether the input is valid  
    **Correct Answer**: b) Whether the tool’s output is the final result of the agent’s execution  

12. **What’s the difference between hosted tools and function tools in terms of `tool_use_behavior`?**  
    a) Hosted tools are synchronous, function tools are asynchronous  
    b) Hosted tools are external, function tools are defined in Python code  
    c) Hosted tools ignore `tool_use_behavior`, function tools respect it  
    d) Hosted tools cannot be combined with `StopAtTools`  
    **Correct Answer**: b) Hosted tools are external, function tools are defined in Python code  

13. **How do you convert an agent into a tool for other agents?**  
    a) Use the `to_tool()` method  
    b) Set `tool_use_behavior` to `run_llm_again`  
    c) Define a new `Agent` class  
    d) Use the `clone()` method  
    **Correct Answer**: a) Use the `to_tool()` method  

14. **What method returns all tools available to an agent?**  
    a) `get_tools()`  
    b) `list_tools()`  
    c) `available_tools()`  
    d) `tools()`  
    **Correct Answer**: a) `get_tools()`  

15. **What is the first parameter of every function tool?**  
    a) `context`  
    b) `agent`  
    c) `input`  
    d) None, function tools have no parameters  
    **Correct Answer**: a) `context`  

16. **What is the purpose of the `get_system_prompt()` method?**  
    a) To generate the agent’s final output  
    b) To retrieve or generate the system prompt for the agent  
    c) To validate input schemas  
    d) To execute a tool call  
    **Correct Answer**: b) To retrieve or generate the system prompt for the agent  

17. **What’s the difference between `InputGuardrail` and `OutputGuardrail`?**  
    a) `InputGuardrail` validates output, `OutputGuardrail` validates input  
    b) `InputGuardrail` checks input before processing, `OutputGuardrail` checks output after processing  
    c) `InputGuardrail` is synchronous, `OutputGuardrail` is asynchronous  
    d) `InputGuardrail` is for tools, `OutputGuardrail` is for agents  
    **Correct Answer**: b) `InputGuardrail` checks input before processing, `OutputGuardrail` checks output after processing  

18. **What is the primary purpose of the `instructions` parameter in an Agent?**  
    a) To define the agent’s behavior and role  
    b) To specify the output format  
    c) To set the maximum number of turns  
    d) To provide the input string  
    **Correct Answer**: a) To define the agent’s behavior and role  

19. **What does the `reset_tool_choice` parameter control?**  
    a) Whether the agent resets its tool selection after each turn  
    b) Whether the agent’s context is cleared  
    c) Whether the tool’s output is final  
    d) Whether the input is validated  
    **Correct Answer**: a) Whether the agent resets its tool selection after each turn  

20. **What happens if a function tool raises an exception?**  
    a) The agent ignores the exception and continues  
    b) The agent stops and raises the exception to the caller  
    c) The agent retries the tool call  
    d) The agent switches to another tool  
    **Correct Answer**: b) The agent stops and raises the exception to the caller  

21. **What does the `clone()` method do?**  
    a) Creates a copy of the agent with the same configuration  
    b) Converts the agent to a tool  
    c) Resets the agent’s context  
    d) Updates the agent’s instructions  
    **Correct Answer**: a) Creates a copy of the agent with the same configuration  

22. **What is `ToolsToFinalOutputFunction` in the OpenAI Agents SDK?**  
    a) A function that defines the agent’s instructions  
    b) A function that converts tool outputs to the final agent output  
    c) A method to validate input schemas  
    d) A tool for streaming responses  
    **Correct Answer**: b) A function that converts tool outputs to the final agent output  

23. **What is the return type of `Runner.run()`?**  
    a) A string  
    b) A `RunResult` object  
    c) A list of tool calls  
    d) A raw response chunk  
    **Correct Answer**: b) A `RunResult` object  

24. **What happens if a custom tool behavior function returns `is_final_output=False`?**  
    a) The agent stops execution  
    b) The agent continues processing, potentially calling more tools or the LLM  
    c) The agent raises an exception  
    d) The agent resets its context  
    **Correct Answer**: b) The agent continues processing, potentially calling more tools or the LLM  

25. **When would you use `StopAtTools` instead of `stop_on_first_tool`?**  
    a) When you want to stop after calling specific tools  
    b) When you want to run the LLM again  
    c) When you want to skip tool calls  
    d) When you want to reset the agent  
    **Correct Answer**: a) When you want to stop after calling specific tools  

26. **What is the default value for `tool_use_behavior` in an Agent?**  
    a) `stop_on_first_tool`  
    b) `run_llm_again`  
    c) `none`  
    d) `custom`  
    **Correct Answer**: b) `run_llm_again`  

27. **What’s the key difference between `run_llm_again` and `stop_on_first_tool` in terms of performance?**  
    a) `run_llm_again` is faster because it skips tool calls  
    b) `stop_on_first_tool` is faster because it avoids additional LLM calls  
    c) `run_llm_again` reduces memory usage  
    d) `stop_on_first_tool` increases latency  
    **Correct Answer**: b) `stop_on_first_tool` is faster because it avoids additional LLM calls  

28. **Which Pydantic v2 decorator is used for field validation?**  
    a) `@field_validator`  
    b) `@model_validator`  
    c) `@schema_validator`  
    d) `@property`  
    **Correct Answer**: a) `@field_validator`  

29. **What is the purpose of `model_settings` in an Agent?**  
    a) To define the agent’s name  
    b) To configure parameters like temperature, max_tokens, and others for the model  
    c) To specify the input format  
    d) To set the maximum number of turns  
    **Correct Answer**: b) To configure parameters like temperature, max_tokens, and others for the model  

30. **How do you enable non-strict mode for flexible schemas?**  
    a) Set `extra="allow"` in the Pydantic model config  
    b) Set `strict=False` in the Pydantic model config  
    c) Use the `@non_strict` decorator  
    d) Set `validate_all=True`  
    **Correct Answer**: a) Set `extra="allow"` in the Pydantic model config  

31. **What does the `handoff_description` parameter do?**  
    a) Defines the output schema  
    b) Provides a description for transitioning to another agent during handoff  
    c) Validates the input data  
    d) Specifies the tool’s behavior  
    **Correct Answer**: b) Provides a description for transitioning to another agent during handoff  

32. **How do you implement schema evolution while maintaining backward compatibility?**  
    a) Use strict schemas only  
    b) Add optional fields and use `extra="allow"` for flexibility  
    c) Remove old fields entirely  
    d) Disable validation  
    **Correct Answer**: b) Add optional fields and use `extra="allow"` for flexibility  

33. **Can dynamic instructions be async functions?**  
    a) No, they must be synchronous  
    b) Yes, they can be async if defined as async functions  
    c) Only if `tool_use_behavior` is set to `run_llm_again`  
    d) Only if guardrails are disabled  
    **Correct Answer**: b) Yes, they can be async if defined as async functions  

34. **What happens when `tool_use_behavior` is set to `stop_on_first_tool`?**  
    a) The agent continues calling the LLM after a tool call  
    b) The agent stops after the first tool call  
    c) The agent skips all tool calls  
    d) The agent raises an exception  
    **Correct Answer**: b) The agent stops after the first tool call  

35. **What’s the difference between mutable and immutable context patterns?**  
    a) Mutable contexts can be modified during execution, immutable cannot  
    b) Immutable contexts are faster but less flexible  
    c) Mutable contexts are synchronous, immutable are asynchronous  
    d) Immutable contexts disable tool calls  
    **Correct Answer**: a) Mutable contexts can be modified during execution, immutable cannot  

36. **What causes the error `'additionalProperties should not be set for object types'`?**  
    a) Using `extra="forbid"` in a Pydantic model  
    b) Setting `additionalProperties` in a JSON schema for an object type  
    c) Defining a non-strict schema  
    d) Using async functions in a synchronous context  
    **Correct Answer**: b) Setting `additionalProperties` in a JSON schema for an object type  

37. **When should you use non-strict schemas over strict schemas?**  
    a) When performance is the primary concern  
    b) When flexibility is needed for handling unknown or extra fields  
    c) When strict validation is required  
    d) When guardrails are disabled  
    **Correct Answer**: b) When flexibility is needed for handling unknown or extra fields  

38. **In a custom tool behavior function, what parameters does it receive?**  
    a) `agent` and `input`  
    b) `context`, `tools`, and `tool_outputs`  
    c) `output` and `schema`  
    d) `instructions` and `model_settings`  
    **Correct Answer**: b) `context`, `tools`, and `tool_outputs`  

39. **What does `Runner.run_streamed()` return?**  
    a) A complete `RunResult` object  
    b) An async iterator yielding stream events and a final response object  
    c) A synchronous response  
    d) A list of tool calls  
    **Correct Answer**: b) An async iterator yielding stream events and a final response object  

40. **How do you create dynamic instructions that change based on context?**  
    a) Use a static string in the `instructions` parameter  
    b) Define a function or async function for `instructions` that uses the context  
    c) Set `tool_use_behavior` to `dynamic`  
    d) Disable guardrails  
    **Correct Answer**: b) Define a function or async function for `instructions` that uses the context  

---
