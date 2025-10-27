
---

### 1. What type of object does the `model_settings` field expect?  
A) dict  
B) **ModelSettings (correct)**  
C) str  
D) BaseModel  

---

### 2. Which field is used to describe an agent when it's used as a handoff target?  
A) name  
B) instructions  
C) **handoff_description (correct)**  
D) description  

---

### 3. What is the default model used by an Agent if no model is specified?  
```python
agent = Agent(name="Test")  # What model will this use?
```  
A) "gpt-3.5-turbo"  
B) "gpt-4"  
C) **"gpt-4o" (correct)**  
D) "gpt-4o-mini"  

---

### 4. Which of the following is NOT a valid type for the `instructions` parameter?  
A) str  
B) Callable[[RunContextWrapper[TContext], Agent[TContext]], MaybeAwaitable[str]]  
C) **list[str] (correct)**  
D) None  

---

### 5. What is the default value for the `instructions` parameter in the Agent class?  
A) "You are a helpful assistant"  
B) **None (correct)**  
C) An empty string ""  
D) A default system prompt  

---

### 6. Which parameter is required when creating an Agent instance?  
```python
agent = Agent(
    # Options: name, instructions, model, handoffs
)
```  
A) instructions  
B) model  
C) **name (correct)**  
D) handoffs  

---

### 7. You have an orchestrator agent that uses 5 specialist agents. If `translation_agent` hits a temporary API rate limit and fails, with instructions:  
> “If any translation fails, try an alternative approach”  

What happens to the orchestrator's execution context?  
A) **Orchestrator receives the exception as tool output, can handle it in its reasoning & continues with others (correct)**  
B) Orchestrator immediately fails with the specialist's exception, and all pending tool calls are cancelled  
C) All the specialist agents share the same execution context, so the failure affects all of them  
D) The failed specialist automatically retries 3 times before the orchestrator sees the failure  

---

### 8. Which of the following is a valid use of `FunctionTool` without decorators?  
A) **You must define a Pydantic schema, async function, and manually create the tool object (correct)**  
B) It only works for sync functions  
C) You don’t need to validate input  
D) You cannot use FunctionTool without `@function_tool`  

---

### 9. Which field is used to describe an agent when it's used as a handoff target?  
A) name  
B) instructions  
C) **handoff_description (correct)**  
D) description  

---

### 10. What type of object does the `model_settings` field expect?  
A) dict  
B) **ModelSettings (correct)**  
C) str  
D) BaseModel  

---

### 11. Which parameter controls the agent's output format to return structured data instead of plain text?  
A) return_type  
B) output_format  
C) **output_type (correct)**  
D) response_format  

---

### 12. What is the default factory for the `tools` field?  
```python
@dataclass
class Agent:
    tools: list[Tool] = field(default_factory=?)
```  
A) []  
B) **list (correct)**  
C) list()  
D) lambda: []  

---

### 13. The `on_tool_end` hook is useful for:  
a) Starting a new agent  
b) **Tracking the completion of a tool's execution (correct)**  
c) Skipping tool usage  
d) Deleting the agent  

---

### 14. Which stage is associated with finalizing logs or cleanup tasks?  
a) Initialization  
b) Execution  
c) **Completion/Termination (correct)**  
d) Handoff  

---

### 15. What happens during the `on_handoff` hook?  
a) The agent deletes its logs  
b) **The agent transfers control to another agent (correct)**  
c) The agent restarts its task  
d) The agent terminates immediately  

---

### 16. During which lifecycle stage would you typically perform initial logging?  
a) **Execution/Processing (correct)**  
b) Initialization/Activation  
c) Handoff  
d) Termination  

---

### 17. Which hook allows you to monitor when an agent begins using an external tool?  
a) on_end  
b) **on_tool_start (correct)**  
c) on_handoff  
d) on_start  

---

### 18. Which hook is triggered when an agent is first activated?  
a) on_tool_start  
b) on_handoff  
c) **on_start (correct)**  
d) on_end  

---

### 19. What is the primary purpose of an agent's lifecycle?  
a) To limit the agent's functionality  
b) **To provide a structured sequence of stages from activation to task completion (correct)**  
c) To reduce the agent's interaction with tools  
d) To delete the agent after execution  

---
