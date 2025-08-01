1-What type of object does the model_settings field expect?
A) dict
B) ModelSettings(correct)
C) str
D) BaseModel



2--Which field is used to describe an agent when it's used as a handoff target?
A) name
B) instructions
C) handoff_description  (correct)
D) description


3--What is the default model used by an Agent if no model is specified?

agent = Agent(name="Test")  # What model will this use?
A) "gpt-3.5-turbo"
B) "gpt-4"
C) "gpt-4o" (correct)
D) "gpt-4o-mini"


4--Which of the following is NOT a valid type for the instructions parameter?
A) str
B) Callable[[RunContextWrapper[TContext], Agent[TContext]], MaybeAwaitable[str]]
C) list[str]  (correct)
D) None


5--What is the default value for the instructions parameter in the Agent class?
A) "You are a helpful assistant"
B) None  (correct)
C) An empty string ""
D) A default system prompt


6--Which parameter is required when creating an Agent instance?

agent = Agent(
    # Options: name, instructions, model, handoffs
)
A) instructions
B) model
C) name (correct)
D) handoffs


7--You have an orchestrator agent that uses 5 specialist agents, if translation_agent hits a temporary API rate limit and fails, with instructions: “If any translation fails, try an alternative approach”? What happens to the orchestrators execution context.
A) Orchstratr receivs the exception as tool output,can handle it in its reasoning & continues with othr (correct)
B)Orchestratr immediately fails with the specialist's exception,n all pending tool calls are cancelled
C) All the specialist agents share the same execution context, so the failure affects all of them.
D) The failed specialist automatically retries 3 times before the orchestrator sees the failure.


8--Which of the following is a valid use of FunctionTool without decorators?
A) You must define a Pydantic schema, async function, and manually create the tool object (correct)
B) It only works for sync functions
C) You don’t need to validate input
D) You cannot use FunctionTool without @function_tool

