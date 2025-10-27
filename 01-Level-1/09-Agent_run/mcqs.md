# 50 Multiple-Choice Questions on Runner Methods

Below are 50 multiple-choice questions (MCQs) based on the `Runner.run`, `Runner.run_sync`, and `Runner.stream` methods, along with related concepts such as asynchronous programming, streaming, and agent workflows in Python. Each question includes four answer options and the correct answer.

---

## Questions

1. **What is the primary purpose of the `Runner.run` method?**  
   a) To stream responses in real-time  
   b) To send a query and receive a complete response at once  
   c) To run synchronous code without async/await  
   d) To execute tool calls only  
   **Correct Answer**: b) To send a query and receive a complete response at once

2. **What is the nature of the `Runner.run` method?**  
   a) Synchronous  
   b) Asynchronous  
   c) Both synchronous and asynchronous  
   d) Neither synchronous nor asynchronous  
   **Correct Answer**: b) Asynchronous

3. **Why is `await` required when using `Runner.run`?**  
   a) It is a synchronous method  
   b) It is an async method that needs to be awaited in an event loop  
   c) It processes tool calls automatically  
   d) It avoids buffering output  
   **Correct Answer**: b) It is an async method that needs to be awaited in an event loop

4. **Which library is used to run async functions like `Runner.run`?**  
   a) threading  
   b) asyncio  
   c) multiprocessing  
   d) os  
   **Correct Answer**: b) asyncio

5. **What does `result.last_agent` return when using `Runner.run`?**  
   a) The final output string  
   b) The Agent class instance  
   c) A list of tool calls  
   d) The input prompt  
   **Correct Answer**: b) The Agent class instance

6. **What happens if `max_turns` is exceeded in `Runner.run`?**  
   a) The loop continues indefinitely  
   b) A MaxTurnsExceeded exception is raised  
   c) The agent restarts  
   d) The input is ignored  
   **Correct Answer**: b) A MaxTurnsExceeded exception is raised

7. **Which parameter in `Runner.run` specifies the initial input to the agent?**  
   a) max_turns  
   b) context  
   c) input  
   d) hooks  
   **Correct Answer**: c) input

8. **What is the purpose of the `run_config` parameter in `Runner.run`?**  
   a) To define the agent's name  
   b) To provide global settings for the agent run  
   c) To specify the output type  
   d) To store the previous response ID  
   **Correct Answer**: b) To provide global settings for the agent run

9. **When is `Runner.run_sync` most suitable to use?**  
   a) In asynchronous applications like FastAPI  
   b) In simple scripts or CLI without async code  
   c) For real-time streaming output  
   d) When multiple agents are involved  
   **Correct Answer**: b) In simple scripts or CLI without async code

10. **What is the main difference between `Runner.run` and `Runner.run_sync`?**  
    a) `run` is synchronous, `run_sync` is asynchronous  
    b) `run` is asynchronous, `run_sync` is synchronous  
    c) `run` streams output, `run_sync` does not  
    d) `run` uses tools, `run_sync` does not  
    **Correct Answer**: b) `run` is asynchronous, `run_sync` is synchronous

11. **Why will `Runner.run_sync` not work in an async function?**  
    a) It requires `await`  
    b) It is designed for synchronous code and cannot run in an event loop  
    c) It only works with streaming  
    d) It lacks tool support  
    **Correct Answer**: b) It is designed for synchronous code and cannot run in an event loop

12. **What does `Runner.stream` provide?**  
    a) A complete response at once  
    b) Real-time streaming of responses in chunks  
    c) A synchronous output  
    d) A list of all agents  
    **Correct Answer**: b) Real-time streaming of responses in chunks

13. **What is the main advantage of using `Runner.stream`?**  
    a) It reduces memory usage  
    b) It provides faster feedback with real-time output  
    c) It avoids using async/await  
    d) It skips tool calls  
    **Correct Answer**: b) It provides faster feedback with real-time output

14. **In which scenario is `Runner.stream` most useful?**  
    a) Batch processing large datasets  
    b) Chat applications requiring live output  
    c) Synchronous scripts  
    d) Database operations  
    **Correct Answer**: b) Chat applications requiring live output

15. **What is streaming in the context of the OpenAI SDK?**  
    a) Sending the entire response at once  
    b) Receiving the response token-by-token as it is generated  
    c) Storing responses in a database  
    d) Running multiple agents simultaneously  
    **Correct Answer**: b) Receiving the response token-by-token as it is generated

16. **What is a key benefit of streaming for long responses?**  
    a) It reduces server load  
    b) It reduces perceived latency for users  
    c) It avoids async programming  
    d) It simplifies tool calls  
    **Correct Answer**: b) It reduces perceived latency for users

17. **How does synchronous mode differ from streaming mode?**  
    a) Synchronous mode sends chunks, streaming mode sends the full response  
    b) Synchronous mode waits for the full response, streaming mode sends chunks  
    c) Synchronous mode is faster for all responses  
    d) Synchronous mode uses async/await  
    **Correct Answer**: b) Synchronous mode waits for the full response, streaming mode sends chunks

18. **What happens in asynchronous mode when a response is generated?**  
    a) The entire response is sent at once  
    b) The response is sent in chunks as it is generated  
    c) The response is stored in a buffer  
    d) The response is delayed until completion  
    **Correct Answer**: b) The response is sent in chunks as it is generated

19. **What is a turn in the context of `Runner.run`?**  
    a) A single tool call  
    b) One AI invocation, including any tool calls  
    c) A complete response cycle  
    d) A context update  
    **Correct Answer**: b) One AI invocation, including any tool calls

20. **What does the `hooks` parameter in `Runner.run` do?**  
    a) Specifies the input format  
    b) Receives callbacks on lifecycle events  
    c) Defines the output type  
    d) Sets the maximum turns  
    **Correct Answer**: b) Receives callbacks on lifecycle events

21. **What does `Runner.run_streamed` provide compared to `Runner.stream`?**  
    a) Only raw response chunks  
    b) Real-time streaming with a final assembled response object  
    c) Synchronous output  
    d) No streaming, only full output  
    **Correct Answer**: b) Real-time streaming with a final assembled response object

22. **Which event type is returned by `AgentUpdatedStreamEvent`?**  
    a) raw_response_event  
    b) run_item_stream_event  
    c) agent_updated_stream_event  
    d) tool_call_item  
    **Correct Answer**: c) agent_updated_stream_event

23. **What does the `RawResponsesStreamEvent` class return?**  
    a) The agent’s name and instructions  
    b) Two properties: `data` and `type='raw_response_event'`  
    c) The final output message  
    d) A list of tool calls  
    **Correct Answer**: b) Two properties: `data` and `type='raw_response_event'`

24. **What does the `RunItemStreamEvent` class include?**  
    a) Only the agent’s context  
    b) Three properties: `name`, `item`, and `run_item_stream_event`  
    c) The complete response text  
    d) The previous response ID  
    **Correct Answer**: b) Three properties: `name`, `item`, and `run_item_stream_event`

25. **How can you extract data from a `RawResponsesStreamEvent` with type `ResponseTextDeltaEvent`?**  
    a) Check `event.type == "agent_updated_stream_event"`  
    b) Check `event.type == "raw_response_event"` and use `isinstance(event.data, ResponseTextDeltaEvent)`  
    c) Use `event.item.type`  
    d) Access `event.new_agent`  
    **Correct Answer**: b) Check `event.type == "raw_response_event"` and use `isinstance(event.data, ResponseTextDeltaEvent)`

26. **What does the `isinstance` function do in Python?**  
    a) Checks if an object is an instance of a specified class  
    b) Creates a new instance of a class  
    c) Converts an object to a different type  
    d) Compares two objects for equality  
    **Correct Answer**: a) Checks if an object is an instance of a specified class

27. **What is the purpose of `end=""` in a Python `print` statement?**  
    a) Adds a newline after the output  
    b) Prevents adding a newline, keeping output on the same line  
    c) Flushes the output buffer  
    d) Specifies the output format  
    **Correct Answer**: b) Prevents adding a newline, keeping output on the same line

28. **What does `flush=True` in a Python `print` statement do?**  
    a) Adds a newline to the output  
    b) Forces immediate writing of buffered output to the console  
    c) Formats the output as a string  
    d) Skips the output entirely  
    **Correct Answer**: b) Forces immediate writing of buffered output to the console

29. **Why is `flush=True` useful in streaming applications?**  
    a) It reduces memory usage  
    b) It ensures real-time output without buffering delays  
    c) It simplifies async programming  
    d) It formats the output as JSON  
    **Correct Answer**: b) It ensures real-time output without buffering delays

30. **What does the `agent_updated_stream_event` indicate?**  
    a) A tool call has been made  
    b) The agent’s state has been updated  
    c) The final output is ready  
    d) The response is complete  
    **Correct Answer**: b) The agent’s state has been updated

31. **What is the `tool_call_item` in `run_item_stream_event`?**  
    a) The output of a tool call  
    b) The event when a tool is called by the agent  
    c) The final message output  
    d) The agent’s context update  
    **Correct Answer**: b) The event when a tool is called by the agent

32. **What does `tool_call_output_item` represent in `run_item_stream_event`?**  
    a) The agent’s name update  
    b) The output returned by a tool call  
    c) The initial input to the agent  
    d) The complete response text  
    **Correct Answer**: b) The output returned by a tool call

33. **What is the purpose of `message_output_item` in `run_item_stream_event`?**  
    a) To update the agent’s instructions  
    b) To provide the agent’s final or intermediate message output  
    c) To call a tool  
    d) To store the context  
    **Correct Answer**: b) To provide the agent’s final or intermediate message output

34. **Which method is unsuitable for use in a FastAPI application?**  
    a) `Runner.run`  
    b) `Runner.stream`  
    c) `Runner.run_sync`  
    d) `Runner.run_streamed`  
    **Correct Answer**: c) `Runner.run_sync`

35. **What does the `previous_response_id` parameter do in `Runner.run`?**  
    a) Specifies the agent’s name  
    b) Allows skipping input from the previous turn for OpenAI models  
    c) Defines the output type  
    d) Sets the maximum turns  
    **Correct Answer**: b) Allows skipping input from the previous turn for OpenAI models

36. **What happens if a guardrail tripwire is triggered in `Runner.run`?**  
    a) The loop restarts  
    b) A GuardrailTripwireTriggered exception is raised  
    c) The agent skips the input  
    d) The response is buffered  
    **Correct Answer**: b) A GuardrailTripwireTriggered exception is raised

37. **Which event type is typically skipped in streaming applications?**  
    a) `agent_updated_stream_event`  
    b) `raw_response_event`  
    c) `run_item_stream_event`  
    d) `tool_call_output_item`  
    **Correct Answer**: b) `raw_response_event`

38. **What is the role of the `starting_agent` parameter in `Runner.run`?**  
    a) Specifies the initial agent to run the workflow  
    b) Defines the output format  
    c) Sets the maximum number of turns  
    d) Provides the input string  
    **Correct Answer**: a) Specifies the initial agent to run the workflow

39. **What does the `context` parameter in `Runner.run_sync` do?**  
    a) Specifies the agent’s name  
    b) Provides the context for running the agent  
    c) Defines the output type  
    d) Sets the maximum turns  
    **Correct Answer**: b) Provides the context for running the agent

40. **What is the output type of `Runner.run`?**  
    a) A single string  
    b) A `RunResult` containing inputs, guardrail results, and the last agent’s output  
    c) A list of tool calls  
    d) A raw response chunk  
    **Correct Answer**: b) A `RunResult` containing inputs, guardrail results, and the last agent’s output

41. **What is the main use case for `Runner.run_streamed`?**  
    a) To run synchronous scripts  
    b) To provide real-time streaming with a final response object  
    c) To avoid async programming  
    d) To skip tool calls  
    **Correct Answer**: b) To provide real-time streaming with a final response object

42. **What does the `ItemHelpers.text_message_output` function do?**  
    a) Calls a tool  
    b) Extracts the text from a `message_output_item`  
    c) Updates the agent’s state  
    d) Formats the input string  
    **Correct Answer**: b) Extracts the text from a `message_output_item`

43. **Which of the following is a valid parameter for `Runner.stream`?**  
    a) `max_turns`  
    b) `output_type`  
    c) `agent_name`  
    d) `response_format`  
    **Correct Answer**: a) `max_turns`

44. **What is the default behavior of Python’s `print` function regarding newlines?**  
    a) It adds a space after each output  
    b) It adds a newline after each output  
    c) It buffers the output  
    d) It skips the output  
    **Correct Answer**: b) It adds a newline after each output

45. **What is the purpose of the `function_tool` decorator in the provided code?**  
    a) To define a synchronous function  
    b) To register a function as a tool for the agent  
    c) To format the output  
    d) To update the agent’s state  
    **Correct Answer**: b) To register a function as a tool for the agent

46. **What does the `how_many_jokes` tool return in the example code?**  
    a) A fixed number of jokes  
    b) A random integer between 1 and 10  
    c) A string of jokes  
    d) The agent’s name  
    **Correct Answer**: b) A random integer between 1 and 10

47. **What is the significance of `set_tracing_disabled(False)`?**  
    a) It enables tracing for debugging  
    b) It disables the agent’s tools  
    c) It skips streaming output  
    d) It formats the response  
    **Correct Answer**: a) It enables tracing for debugging

48. **What does the `AsyncOpenAI` client do in the example code?**  
    a) Defines the agent’s instructions  
    b) Provides the API client for interacting with the model  
    c) Specifies the output format  
    d) Sets the maximum turns  
    **Correct Answer**: b) Provides the API client for interacting with the model

49. **What is the purpose of the `load_dotenv` function in the example code?**  
    a) To load environment variables from a `.env` file  
    b) To define the agent’s tools  
    c) To format the output  
    d) To update the agent’s state  
    **Correct Answer**: a) To load environment variables from a `.env` file

50. **What is the output of the example code with the `how_many_jokes` tool?**  
    a) A fixed number of jokes  
    b) A random number of jokes based on the tool’s output  
    c) The agent’s name and instructions  
    d) A raw response chunk  
    **Correct Answer**: b) A random number of jokes based on the tool’s output

---

This `readme.md` file contains 50 MCQs covering the key concepts of `Runner.run`, `Runner.run_sync`, `Runner.stream`, and related topics. Each question is designed to test understanding of the methods, their parameters, use cases, and associated Python concepts.