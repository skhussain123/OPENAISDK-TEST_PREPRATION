
## Section 1: Basics of Handoffs

1. **What is the primary purpose of handoffs in the Agents SDK?**  
   a) To execute tasks independently without involving other agents  
   b) To delegate tasks to another specialized agent  
   c) To terminate the agent execution  
   d) To modify the input query  
   **Correct Answer**: b) To delegate tasks to another specialized agent  

2. **How are handoffs represented to the LLM in the Agents SDK?**  
   a) As variables  
   b) As tools  
   c) As functions  
   d) As classes  
   **Correct Answer**: b) As tools  

3. **What is the default tool name for a handoff to an agent named "Refund Agent"?**  
   a) handoff_refund_agent  
   b) transfer_to_refund_agent  
   c) call_refund_agent  
   d) delegate_refund_agent  
   **Correct Answer**: b) transfer_to_refund_agent  

4. **Which parameter in the Agent class is used to specify handoffs?**  
   a) tools  
   b) handoffs  
   c) instructions  
   d) model  
   **Correct Answer**: b) handoffs  

5. **What does the `handoff()` function in the Agents SDK allow you to do?**  
   a) Create a new agent  
   b) Customize the handoff process  
   c) Run the agent synchronously  
   d) Define the agent's model  
   **Correct Answer**: b) Customize the handoff process  

6. **What happens if the `handoffs` parameter in an Agent is left empty?**  
   a) The agent cannot delegate tasks  
   b) The agent uses default handoffs  
   c) The agent crashes  
   d) The agent processes all tasks itself  
   **Correct Answer**: a) The agent cannot delegate tasks  

7. **Which of the following is NOT a valid way to create a handoff?**  
   a) Passing an Agent directly to the handoffs parameter  
   b) Using the `handoff()` function  
   c) Defining a new model in the Agent class  
   d) Customizing handoff with tool_name_override  
   **Correct Answer**: c) Defining a new model in the Agent class  

8. **What is the purpose of the `instructions` parameter in an Agent?**  
   a) To define how the agent delegates tasks  
   b) To specify the agent's behavior when it receives a query  
   c) To override the handoff tool name  
   d) To filter the input query  
   **Correct Answer**: b) To specify the agent's behavior when it receives a query  

9. **What role does the `handoff_description` parameter play?**  
   a) It defines the agent's primary task  
   b) It provides a hint to the triage agent about when to hand off  
   c) It overrides the agent's instructions  
   d) It disables the handoff  
   **Correct Answer**: b) It provides a hint to the triage agent about when to hand off  

10. **What is the output of `result.last_agent` after a handoff?**  
    a) The input query  
    b) The final output of the agent  
    c) The Agent object that handled the query  
    d) The RunConfig object  
    **Correct Answer**: c) The Agent object that handled the query  

## Section 2: Creating Handoffs

11. **How can you pass an agent to the `handoffs` parameter of a triage agent?**  
    a) As a string  
    b) As an Agent object or Handoff object  
    c) As a dictionary  
    d) As a function  
    **Correct Answer**: b) As an Agent object or Handoff object  

12. **What does the `handoff()` function return?**  
    a) An Agent object  
    b) A Handoff object  
    c) A string  
    d) A RunContextWrapper  
    **Correct Answer**: b) A Handoff object  

13. **Which parameter in the `handoff()` function allows you to override the default tool name?**  
    a) tool_name_override  
    b) tool_description_override  
    c) input_filter  
    d) on_handoff  
    **Correct Answer**: a) tool_name_override  

14. **What is the default behavior if `tool_name_override` is not provided in the `handoff()` function?**  
    a) The tool name is set to the agent's instructions  
    b) The tool name is generated as `transfer_to_<agent_name>`  
    c) The tool name is set to `handoff_<agent_name>`  
    d) The handoff is disabled  
    **Correct Answer**: b) The tool name is generated as `transfer_to_<agent_name>`  

15. **What does the `tool_description_override` parameter do in the `handoff()` function?**  
    a) Overrides the agent's instructions  
    b) Specifies the description of the handoff tool for the triage agent  
    c) Filters the input query  
    d) Defines the agent's model  
    **Correct Answer**: b) Specifies the description of the handoff tool for the triage agent  

16. **What is the purpose of the `on_handoff` callback function?**  
    a) To validate the input query  
    b) To execute logic when the handoff is invoked  
    c) To define the agent's instructions  
    d) To override the tool name  
    **Correct Answer**: b) To execute logic when the handoff is invoked  

17. **What does the `is_enabled` parameter in the `handoff()` function control?**  
    a) Whether the agent is active  
    b) Whether the handoff is available to the LLM  
    c) Whether the input filter is applied  
    d) Whether the model is loaded  
    **Correct Answer**: b) Whether the handoff is available to the LLM  

18. **What happens if `is_enabled` is set to `False` in the `handoff()` function?**  
    a) The agent is disabled  
    b) The handoff tool is hidden from the LLM  
    c) The input query is filtered  
    d) The handoff is executed automatically  
    **Correct Answer**: b) The handoff tool is hidden from the LLM  

19. **What type of value can `is_enabled` accept in the `handoff()` function?**  
    a) Only a boolean  
    b) A boolean or a function returning a boolean  
    c) A string  
    d) A dictionary  
    **Correct Answer**: b) A boolean or a function returning a boolean  

20. **What is the purpose of the `input_filter` parameter in the `handoff()` function?**  
    a) To modify or validate the input before it reaches the next agent  
    b) To override the tool description  
    c) To execute a callback function  
    d) To define the agent's model  
    **Correct Answer**: a) To modify or validate the input before it reaches the next agent  

## Section 3: Differences Between Normal Agent and `handoff()` Function

21. **What is the main difference between passing a normal agent and using the `handoff()` function?**  
    a) Normal agents cannot be used for handoffs  
    b) The `handoff()` function allows for more customization  
    c) Normal agents are always disabled  
    d) The `handoff()` function does not support tool names  
    **Correct Answer**: b) The `handoff()` function allows for more customization  

22. **When passing a normal agent to the `handoffs` parameter, what does the triage agent rely on to make handoff decisions?**  
    a) The agent's name and instructions  
    b) The agent's model  
    c) The agent's tools  
    d) The agent's input filter  
    **Correct Answer**: a) The agent's name and instructions  

23. **What happens when you use `tool_name_override` in the `handoff()` function?**  
    a) It changes the agent's instructions  
    b) It customizes the name of the handoff tool  
    c) It disables the handoff  
    d) It filters the input query  
    **Correct Answer**: b) It customizes the name of the handoff tool  

24. **When is it appropriate to use a normal agent for handoffs?**  
    a) When customization is required  
    b) When the handoff logic is simple and based on agent instructions  
    c) When the handoff needs to be disabled  
    d) When the input needs to be filtered  
    **Correct Answer**: b) When the handoff logic is simple and based on agent instructions  

25. **What is a key advantage of using the `handoff()` function over a normal agent?**  
    a) It simplifies the agent's instructions  
    b) It allows precise control over handoff logic  
    c) It disables the handoff by default  
    d) It removes the need for a triage agent  
    **Correct Answer**: b) It allows precise control over handoff logic  

26. **Which parameter in the `handoff()` function allows you to specify the type of queries the agent should handle?**  
    a) tool_name_override  
    b) tool_description_override  
    c) input_filter  
    d) on_handoff  
    **Correct Answer**: b) tool_description_override  

27. **What does the triage agent use to decide which agent to hand off to when using a normal agent?**  
    a) The agent's model  
    b) The agent's instructions and name  
    c) The input filter  
    d) The tool description  
    **Correct Answer**: b) The agent's instructions and name  

28. **What is a limitation of using a normal agent for handoffs?**  
    a) It cannot be used in the `handoffs` parameter  
    b) It lacks fine-tuned control over handoff logic  
    c) It requires a custom model  
    d) It disables the triage agent  
    **Correct Answer**: b) It lacks fine-tuned control over handoff logic  

29. **When should you use the `handoff()` function instead of a normal agent?**  
    a) When you want the handoff to be disabled  
    b) When you need specific handoff logic for certain query types  
    c) When you want to simplify the agent's instructions  
    d) When you want to bypass the triage agent  
    **Correct Answer**: b) When you need specific handoff logic for certain query types  

30. **What is the effect of using `tool_description_override` in the `handoff()` function?**  
    a) It changes the agent's instructions  
    b) It provides a specific description for the handoff tool  
    c) It filters the input query  
    d) It disables the handoff  
    **Correct Answer**: b) It provides a specific description for the handoff tool  

## Section 4: `is_enabled` Parameter

31. **What is the default value of the `is_enabled` parameter in the `handoff()` function?**  
    a) False  
    b) True  
    c) None  
    d) A function  
    **Correct Answer**: b) True  

32. **What happens if `is_enabled` is set to `False` in a handoff?**  
    a) The agent is disabled  
    b) The handoff tool is not shown to the LLM  
    c) The input query is filtered  
    d) The handoff is executed automatically  
    **Correct Answer**: b) The handoff tool is not shown to the LLM  

33. **What type of value can `is_enabled` accept?**  
    a) Only a string  
    b) A boolean or a function returning a boolean  
    c) A dictionary  
    d) A Pydantic model  
    **Correct Answer**: b) A boolean or a function returning a boolean  

34. **What is the purpose of setting `is_enabled` to a function?**  
    a) To filter the input query  
    b) To dynamically enable or disable the handoff at runtime  
    c) To override the tool name  
    d) To define the agent's instructions  
    **Correct Answer**: b) To dynamically enable or disable the handoff at runtime  

35. **If `is_enabled` is a function, what does it take as input?**  
    a) The agent's instructions  
    b) The RunContextWrapper and the agent  
    c) The input query  
    d) The tool description  
    **Correct Answer**: b) The RunContextWrapper and the agent  

36. **What happens if `is_enabled` returns `False` at runtime?**  
    a) The handoff tool is hidden from the LLM  
    b) The agent is terminated  
    c) The input query is filtered  
    d) The handoff is executed  
    **Correct Answer**: a) The handoff tool is hidden from the LLM  

37. **What is the benefit of using a dynamic `is_enabled` function?**  
    a) It simplifies the agent's instructions  
    b) It allows conditional handoffs based on runtime conditions  
    c) It filters the input query  
    d) It overrides the tool description  
    **Correct Answer**: b) It allows conditional handoffs based on runtime conditions  

38. **If `is_enabled` is set to `True`, what happens?**  
    a) The handoff tool is always available to the LLM  
    b) The handoff is disabled  
    c) The input query is filtered  
    d) The agent is terminated  
    **Correct Answer**: a) The handoff tool is always available to the LLM  

39. **Can `is_enabled` be used to control multiple handoffs?**  
    a) No, it applies to all handoffs  
    b) Yes, each handoff can have its own `is_enabled` setting  
    c) Only for normal agents  
    d) Only for the triage agent  
    **Correct Answer**: b) Yes, each handoff can have its own `is_enabled` setting  

40. **What is the effect of disabling a handoff using `is_enabled=False`?**  
    a) The agent is disabled  
    b) The handoff tool is not presented to the LLM  
    c) The input query is modified  
    d) The triage agent is terminated  
    **Correct Answer**: b) The handoff tool is not presented to the LLM  

## Section 5: `input_filter` Parameter

41. **What is the purpose of the `input_filter` parameter in the `handoff()` function?**  
    a) To override the tool name  
    b) To modify or validate the input before it reaches the next agent  
    c) To define the agent's instructions  
    d) To execute a callback function  
    **Correct Answer**: b) To modify or validate the input before it reaches the next agent  

42. **What type of input does the `input_filter` function receive?**  
    a) A string  
    b) A HandoffInputData object  
    c) A RunContextWrapper  
    d) A Pydantic model  
    **Correct Answer**: b) A HandoffInputData object  

43. **What must the `input_filter` function return?**  
    a) A string  
    b) A HandoffInputData object  
    c) A boolean  
    d) An Agent object  
    **Correct Answer**: b) A HandoffInputData object  

44. **What is an example use case for the `input_filter` function?**  
    a) To change the agent's instructions  
    b) To convert the input query to uppercase  
    c) To disable the handoff  
    d) To override the tool description  
    **Correct Answer**: b) To convert the input query to uppercase  

45. **What happens if the `input_filter` function modifies the input query?**  
    a) The modified query is passed to the next agent  
    b) The query is discarded  
    c) The handoff is disabled  
    d) The triage agent is terminated  
    **Correct Answer**: a) The modified query is passed to the next agent  

46. **What is the benefit of using an `input_filter` function?**  
    a) It simplifies the agent's instructions  
    b) It ensures the input is in the correct format for the next agent  
    c) It disables the handoff  
    d) It overrides the tool name  
    **Correct Answer**: b) It ensures the input is in the correct format for the next agent  

47. **Can the `input_filter` function add a prefix to the input query?**  
    a) Yes  
    b) No  
    c) Only if the query is a string  
    d) Only if the query is a Pydantic model  
    **Correct Answer**: a) Yes  

48. **What happens if the `input_filter` function raises an error?**  
    a) The handoff is executed normally  
    b) The handoff fails, and an error is thrown  
    c) The input query is discarded  
    d) The triage agent is terminated  
    **Correct Answer**: b) The handoff fails, and an error is thrown  

49. **What is the `input_history` attribute in the `HandoffInputData` object?**  
    a) The agent's instructions  
    b) The query string being processed  
    c) The tool description  
    d) The RunContextWrapper  
    **Correct Answer**: b) The query string being processed  

50. **How does the `input_filter` function interact with the `HandoffInputData` object?**  
    a) It modifies the agent's instructions  
    b) It processes the `input_history` and other fields  
    c) It disables the handoff  
    d) It overrides the tool name  
    **Correct Answer**: b) It processes the `input_history` and other fields  

## Section 6: `on_handoff` Parameter

51. **What is the purpose of the `on_handoff` parameter in the `handoff()` function?**  
    a) To filter the input query  
    b) To execute logic when the handoff is invoked  
    c) To define the agent's instructions  
    d) To override the tool description  
    **Correct Answer**: b) To execute logic when the handoff is invoked  

52. **What does the `on_handoff` callback function receive as input?**  
    a) The input query  
    b) The RunContextWrapper and optionally structured input  
    c) The agent's instructions  
    d) The tool description  
    **Correct Answer**: b) The RunContextWrapper and optionally structured input  

53. **What must the `on_handoff` callback function return?**  
    a) A string  
    b) An Agent object  
    c) A boolean  
    d) A HandoffInputData object  
    **Correct Answer**: b) An Agent object  

54. **When is the `on_handoff` callback function executed?**  
    a) When the agent is initialized  
    b) When the handoff is invoked  
    c) When the input query is filtered  
    d) When the triage agent is terminated  
    **Correct Answer**: b) When the handoff is invoked  

55. **What is an example use case for the `on_handoff` callback?**  
    a) To modify the input query  
    b) To log the handoff event  
    c) To override the tool name  
    d) To disable the handoff  
    **Correct Answer**: b) To log the handoff event  

56. **Can the `on_handoff` callback function receive structured input?**  
    a) Yes, if `input_type` is specified  
    b) No, it only receives the RunContextWrapper  
    c) Only if the input is a string  
    d) Only if the handoff is disabled  
    **Correct Answer**: a) Yes, if `input_type` is specified  

57. **What happens if the `on_handoff` callback raises an error?**  
    a) The handoff is executed normally  
    b) The handoff fails, and an error is thrown  
    c) The input query is discarded  
    d) The triage agent is terminated  
    **Correct Answer**: b) The handoff fails, and an error is thrown  

58. **What is the role of the `RunContextWrapper` in the `on_handoff` callback?**  
    a) It provides context about the current execution  
    b) It filters the input query  
    c) It defines the agent's instructions  
    d) It overrides the tool description  
    **Correct Answer**: a) It provides context about the current execution  

59. **Can the `on_handoff` callback return a different agent than the one specified in the handoff?**  
    a) Yes  
    b) No  
    c) Only if the input is filtered  
    d) Only if the handoff is disabled  
    **Correct Answer**: a) Yes  

60. **What is the benefit of using the `on_handoff` callback?**  
    a) It simplifies the agent's instructions  
    b) It allows custom logic during the handoff process  
    c) It disables the handoff  
    d) It overrides the tool name  
    **Correct Answer**: b) It allows custom logic during the handoff process  

## Section 7: `input_type` Parameter

61. **What is the purpose of the `input_type` parameter in the `handoff()` function?**  
    a) To override the tool name  
    b) To specify the expected structure of the input to the handoff  
    c) To filter the input query  
    d) To define the agent's instructions  
    **Correct Answer**: b) To specify the expected structure of the input to the handoff  

62. **What type of input can the `input_type` parameter accept?**  
    a) A string  
    b) A Pydantic model, string, or dict  
    c) A boolean  
    d) An Agent object  
    **Correct Answer**: b) A Pydantic model, string, or dict  

63. **What happens if the input does not match the `input_type` specified in the `handoff()` function?**  
    a) The handoff is executed normally  
    b) An error is thrown  
    c) The input is filtered  
    d) The triage agent is terminated  
    **Correct Answer**: b) An error is thrown  

64. **What is the benefit of using a Pydantic model for `input_type`?**  
    a) It simplifies the agent's instructions  
    b) It ensures type safety and structured input  
    c) It disables the handoff  
    d) It overrides the tool description  
    **Correct Answer**: b) It ensures type safety and structured input  

65. **What is an example of a valid `input_type`?**  
    a) A string  
    b) A Pydantic model  
    c) A boolean  
    d) A RunContextWrapper  
    **Correct Answer**: b) A Pydantic model  

66. **How does the `input_type` parameter interact with the `on_handoff` callback?**  
    a) It filters the input query  
    b) It validates the input before passing it to the callback  
    c) It overrides the tool name  
    d) It disables the handoff  
    **Correct Answer**: b) It validates the input before passing it to the callback  

67. **What happens if `input_type` is not specified in the `handoff()` function?**  
    a) The handoff is disabled  
    b) The input is passed as-is without validation  
    c) The input is filtered  
    d) The triage agent is terminated  
    **Correct Answer**: b) The input is passed as-is without validation  

68. **What is the role of the `EscalationData` class in the `input_type` example?**  
    a) It defines the agent's instructions  
    b) It specifies the structure of the input for the handoff  
    c) It filters the input query  
    d) It overrides the tool description  
    **Correct Answer**: b) It specifies the structure of the input for the handoff  

69. **Can the `input_type` parameter ensure that the input contains specific fields?**  
    a) Yes  
    b) No  
    c) Only if the input is a string  
    d) Only if the handoff is disabled  
    **Correct Answer**: a) Yes  

70. **What is the benefit of using `input_type` with a Pydantic model?**  
    a) It simplifies the agent's instructions  
    b) It ensures the input is strongly typed and validated  
    c) It disables the handoff  
    d) It overrides the tool name  
    **Correct Answer**: b) It ensures the input is strongly typed and validated  

## Section 8: Practical Code-Based Questions

71. **What does the following code do?**  
    ```python
    Nextjs_agent = Agent(name="Nextjs_agent", instructions="You are a helpful Next.js assistant.")
    triage_agent = Agent(name="Assistance", instructions="If the query is about Next.js, hand off to the Next.js agent.", handoffs=[Nextjs_agent])
    ```  
    a) Defines a single agent with no handoffs  
    b) Creates a triage agent that can hand off to a Next.js agent  
    c) Filters the input query  
    d) Overrides the tool name  
    **Correct Answer**: b) Creates a triage agent that can hand off to a Next.js agent  

72. **What is the purpose of the `Runner.run_sync` function in the provided code?**  
    a) To filter the input query  
    b) To execute the agent synchronously with the given input  
    c) To define the agent's instructions  
    d) To disable the handoff  
    **Correct Answer**: b) To execute the agent synchronously with the given input  

73. **What will the following code output for `result.last_agent`?**  
    ```python
    result = Runner.run_sync(starting_agent=triage_agent, input="I have some issues with Python ops", run_config=config)
    ```  
    a) The triage agent  
    b) The Python agent  
    c) The Next.js agent  
    d) None  
    **Correct Answer**: b) The Python agent  

74. **What does the `handoff_description` in the following code do?**  
    ```python
    Python_agent = Agent(name="Python_agent", instructions="You are a helpful Python Assistant", handoff_description="You are a poem writer")
    ```  
    a) It defines the agent's instructions  
    b) It provides a hint to the triage agent for handoff decisions  
    c) It filters the input query  
    d) It overrides the tool name  
    **Correct Answer**: b) It provides a hint to the triage agent for handoff decisions  

75. **What will happen if the `input_filter` function in the following code raises an error?**  
    ```python
    def Convert_capital_letter(handoff_input: HandoffInputData) -> HandoffInputData:
        raise ValueError("Invalid input")
    ```  
    a) The handoff will proceed normally  
    b) The handoff will fail with an error  
    c) The input query will be discarded  
    d) The triage agent will be terminated  
    **Correct Answer**: b) The handoff will fail with an error  

76. **What does the following `input_filter` function do?**  
    ```python
    def Convert_capital_letter(handoff_input: HandoffInputData) -> HandoffInputData:
        query = handoff_input.input_history.upper()
        return HandoffInputData(input_history=query, pre_handoff_items=handoff_input.pre_handoff_items, new_items=handoff_input.new_items, run_context=handoff_input.run_context)
    ```  
    a) It disables the handoff  
    b) It converts the input query to uppercase  
    c) It overrides the tool description  
    d) It defines the agent's instructions  
    **Correct Answer**: b) It converts the input query to uppercase  

77. **What is the purpose of the `RunConfig` object in the provided code?**  
    a) To filter the input query  
    b) To configure the model and provider for the agent  
    c) To override the tool name  
    d) To disable the handoff  
    **Correct Answer**: b) To configure the model and provider for the agent  

78. **What will the following code output for `result.final_output`?**  
    ```python
    result = Runner.run_sync(starting_agent=triage_agent, input="I have some issues with Next.js ops", run_config=config)
    ```  
    a) The input query  
    b) The response from the Next.js agent  
    c) The response from the triage agent  
    d) None  
    **Correct Answer**: b) The response from the Next.js agent  

79. **What does the `on_handoff_callback` function do in the following code?**  
    ```python
    def on_handoff_callback(ctx: RunContextWrapper[Any]):
        print("Handoff trigger hua — context:", ctx)
        return Nextjs_agent
    ```  
    a) It filters the input query  
    b) It logs the handoff event and returns the Next.js agent  
    c) It overrides the tool name  
    d) It disables the handoff  
    **Correct Answer**: b) It logs the handoff event and returns the Next.js agent  

80. **What is the purpose of the `EscalationData` class in the following code?**  
    ```python
    class EscalationData(BaseModel):
        reason: str
    ```  
    a) It defines the agent's instructions  
    b) It specifies the structure of the input for the handoff  
    c) It filters the input query  
    d) It overrides the tool description  
    **Correct Answer**: b) It specifies the structure of the input for the handoff  

## Section 9: Advanced Concepts

81. **What happens if the `tool_name_override` is not unique in a handoff?**  
    a) The handoff is disabled  
    b) The LLM may get confused and select the wrong agent  
    c) The input query is filtered  
    d) The triage agent is terminated  
    **Correct Answer**: b) The LLM may get confused and select the wrong agent  

82. **What is the benefit of using a dynamic `is_enabled` function?**  
    a) It simplifies the agent's instructions  
    b) It allows conditional handoffs based on runtime conditions  
    c) It filters the input query  
    d) It overrides the tool description  
    **Correct Answer**: b) It allows conditional handoffs based on runtime conditions  

83. **What is the role of the `HandoffInputData` object in the `input_filter` function?**  
    a) It defines the agent's instructions  
    b) It contains the input query and other metadata  
    c) It overrides the tool name  
    d) It disables the handoff  
    **Correct Answer**: b) It contains the input query and other metadata  

84. **Can the `input_filter` function modify fields other than `input_history` in the `HandoffInputData` object?**  
    a) Yes  
    b) No  
    c) Only if the input is a string  
    d) Only if the handoff is disabled  
    **Correct Answer**: a) Yes  

85. **What is the purpose of the `pre_handoff_items` attribute in the `HandoffInputData` object?**  
    a) To store the agent's instructions  
    b) To store metadata from previous handoffs  
    c) To filter the input query  
    d) To override the tool description  
    **Correct Answer**: b) To store metadata from previous handoffs  

86. **What happens if the `on_handoff` callback returns `None`?**  
    a) The handoff proceeds normally  
    b) The handoff fails with an error  
    c) The input query is filtered  
    d) The triage agent is terminated  
    **Correct Answer**: b) The handoff fails with an error  

87. **What is the benefit of using a Pydantic model for `input_type`?**  
    a) It simplifies the agent's instructions  
    b) It ensures type safety and structured input  
    c) It disables the handoff  
    d) It overrides the tool description  
    **Correct Answer**: b) It ensures type safety and structured input  

88. **What does the `RunContextWrapper` provide in the `on_handoff` callback?**  
    a) The input query  
    b) Contextual information about the current execution  
    c) The agent's instructions  
    d) The tool description  
    **Correct Answer**: b) Contextual information about the current execution  

89. **Can multiple handoffs be defined for a single triage agent?**  
    a) Yes  
    b) No  
    c) Only if the handoffs are disabled  
    d) Only if the input is filtered  
    **Correct Answer**: a) Yes  

90. **What happens if the triage agent cannot decide which agent to hand off to?**  
    a) The handoff is disabled  
    b) The LLM may select an incorrect agent or none  
    c) The input query is filtered  
    d) The triage agent is terminated  
    **Correct Answer**: b) The LLM may select an incorrect agent or none  

## Section 10: Miscellaneous

91. **What is the role of the `model` parameter in the Agent class?**  
    a) To define the agent's instructions  
    b) To specify the LLM model used by the agent  
    c) To filter the input query  
    d) To override the tool description  
    **Correct Answer**: b) To specify the LLM model used by the agent  

92. **What does the `tracing_disabled` parameter in `RunConfig` do?**  
    a) It disables the handoff  
    b) It disables tracing for the agent execution  
    c) It filters the input query  
    d) It overrides the tool name  
    **Correct Answer**: b) It disables tracing for the agent execution  

93. **What is the purpose of the `AsyncOpenAI` client in the provided code?**  
    a) To filter the input query  
    b) To provide an API client for the LLM  
    c) To define the agent's instructions  
    d) To disable the handoff  
    **Correct Answer**: b) To provide an API client for the LLM  

94. **What does the `OpenAIChatCompletionsModel` class do in the provided code?**  
    a) It filters the input query  
    b) It defines the LLM model configuration  
    c) It overrides the tool description  
    d) It disables the handoff  
    **Correct Answer**: b) It defines the LLM model configuration  

95. **What happens if the `handoff_description` is not provided for an agent?**  
    a) The handoff is disabled  
    b) The triage agent relies on the agent's instructions  
    c) The input query is filtered  
    d) The triage agent is terminated  
    **Correct Answer**: b) The triage agent relies on the agent's instructions  

96. **What is the benefit of using the `handoff()` function for complex scenarios?**  
    a) It simplifies the agent's instructions  
    b) It allows fine-tuned control over handoff logic  
    c) It disables the handoff  
    d) It overrides the tool name  
    **Correct Answer**: b) It allows fine-tuned control over handoff logic  

97. **What does the `tool_choice` parameter in the `ModelSettings` class control?**  
    a) The agent's instructions  
    b) The selection of tools by the LLM  
    c) The input query filtering  
    d) The handoff enablement  
    **Correct Answer**: b) The selection of tools by the LLM  

98. **What is the role of the `input_guardrails` parameter in the Agent class?**  
    a) To define the agent's instructions  
    b) To validate or restrict the input to the agent  
    c) To override the tool description  
    d) To disable the handoff  
    **Correct Answer**: b) To validate or restrict the input to the agent  

99. **What happens if the `model` parameter is not provided in the Agent class?**  
    a) The agent uses a default model  
    b) The agent cannot execute  
    c) The input query is filtered  
    d) The handoff is disabled  
    **Correct Answer**: b) The agent cannot execute  

100. **What is the purpose of the `result.final_output` in the provided code?**  
     a) To store the input query  
     b) To store the final response from the agent  
     c) To filter the input query  
     d) To override the tool description  
     **Correct Answer**: b) To store the final response from the agent