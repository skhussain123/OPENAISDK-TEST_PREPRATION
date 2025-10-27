# Tracing MCQs

1. **What is the primary purpose of the Tracing feature in the Agents SDK?**  
   a) To optimize the agent's performance  
   b) To collect a comprehensive record of events during an agent run  
   c) To disable logging for production environments  
   d) To modify the agent's instructions dynamically  
   **Answer**: b) To collect a comprehensive record of events during an agent run  

2. **How can you globally disable tracing in the Agents SDK?**  
   a) Set `tracing_disabled = True` in `RunConfig`  
   b) Set the environment variable `OPENAI_AGENTS_DISABLE_TRACING=1`  
   c) Use `enable_verbose_stdout_logging()`  
   d) Call `set_tracing_enabled(False)`  
   **Answer**: b) Set the environment variable `OPENAI_AGENTS_DISABLE_TRACING=1`  

3. **Which of the following is a valid way to disable tracing for a single run?**  
   a) Set `agents.run.RunConfig.tracing_disabled = True`  
   b) Use `disable_tracing()` function  
   c) Set `OPENAI_AGENTS_DISABLE_TRACING=0`  
   d) Wrap the run in a `no_trace()` context  
   **Answer**: a) Set `agents.run.RunConfig.tracing_disabled = True`  

4. **What does a Trace represent in the Agents SDK?**  
   a) A single function call  
   b) An end-to-end operation of a workflow composed of Spans  
   c) A log of errors during agent execution  
   d) A collection of unrelated spans  
   **Answer**: b) An end-to-end operation of a workflow composed of Spans  

5. **Which property of a Trace is used to link multiple traces from the same conversation?**  
   a) `workflow_name`  
   b) `trace_id`  
   c) `group_id`  
   d) `span_id`  
   **Answer**: c) `group_id`  

6. **What is the purpose of the `span_data` attribute in a Span?**  
   a) To store the start and end timestamps  
   b) To hold information specific to the Span, such as Agent or LLM generation details  
   c) To link the Span to its parent Trace  
   d) To disable the Span from being recorded  
   **Answer**: b) To hold information specific to the Span, such as Agent or LLM generation details  

7. **Which of the following is NOT wrapped by default in the Agents SDK tracing?**  
   a) LLM generations  
   b) Function tool calls  
   c) Database queries  
   d) Handoffs  
   **Answer**: c) Database queries  

8. **What is the default name of a trace in the Agents SDK?**  
   a) "Default Workflow"  
   b) "Agent Workflow"  
   c) "Tracing Workflow"  
   d) "Main Workflow"  
   **Answer**: b) "Agent Workflow"  

9. **How can you group multiple `Runner.run()` calls into a single trace?**  
   a) By setting `group_id` in `RunConfig`  
   b) By wrapping the calls in a `trace()` context  
   c) By using `set_tracing_disabled(False)`  
   d) By enabling verbose logging  
   **Answer**: b) By wrapping the calls in a `trace()` context  

10. **What is the purpose of the `LocalTraceProcessor` class in the provided code?**  
    a) To disable tracing for all runs  
    b) To store and print trace and span data locally  
    c) To integrate with external tracing processors  
    d) To modify the agent’s instructions  
    **Answer**: b) To store and print trace and span data locally  

11. **Which method in the `TracingProcessor` abstract class is called when a trace starts?**  
    a) `on_span_start`  
    b) `on_trace_start`  
    c) `force_flush`  
    d) `shutdown`  
    **Answer**: b) `on_trace_start`  

12. **What happens when the `shutdown` method is called in the `LocalTraceProcessor` class?**  
    a) It deletes all collected traces  
    b) It prints all collected trace and span data  
    c) It disables tracing for the current session  
    d) It flushes the spans to an external database  
    **Answer**: b) It prints all collected trace and span data  

13. **Which of the following is an external tracing processor supported by the Agents SDK?**  
    a) TensorFlow  
    b) LangSmith  
    c) PyTorch  
    d) Flask  
    **Answer**: b) LangSmith  

14. **What is the key difference between local tracing and dashboard tracing?**  
    a) Local tracing allows customization during a run, while dashboard tracing does not  
    b) Dashboard tracing stores data locally, while local tracing sends data to the cloud  
    c) Local tracing is disabled by default, while dashboard tracing is enabled  
    d) Dashboard tracing allows real-time modification of spans  
    **Answer**: a) Local tracing allows customization during a run, while dashboard tracing does not  

15. **What is the format requirement for a `trace_id` in the Agents SDK?**  
    a) `trace_<16_alphanumeric>`  
    b) `trace_<32_alphanumeric>`  
    c) `id_<32_alphanumeric>`  
    d) `workflow_<32_alphanumeric>`  
    **Answer**: b) `trace_<32_alphanumeric>`