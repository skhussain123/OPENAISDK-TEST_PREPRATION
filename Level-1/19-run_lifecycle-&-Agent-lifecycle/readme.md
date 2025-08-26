


### What Is AgentHooks?
* AgentHooks is a class that each Agent instance can optionally use.
* It functions as an event emitter, emitting lifecycle events such as when the agent starts, ends, calls a tool, or receives a handoff.
* It is scoped per-agent, meaning it's only active for the agent it's attached to—not global across all agents.

#### Key Capabilities
* on_start / on_end: Triggered when the agent begins or finishes execution.
* on_tool_start / on_tool_end: Called when a tool invocation starts or completes.
* on_handoff: Fires when the agent hands off to another sub-agent.

---

#### on_start
* Called before the agent is invoked. Called each time the running agent is changed to this
agent.
* on_start Bydefault return None

##### Arg
```bash
(method) async def on_start(
    self: Self@MyAgentHook,
    context: RunContextWrapper[Any],
    agent: Agent[Any]
) -> None
```

```bash
class MyAgentHook(AgentHooks):
    async def on_start(self, context:RunContextWrapper, agent)->None:
        print("My Agent is Satrting...")
        
    
agent = Agent(
    name="assistance",
    instructions="You are a helpfull Assistance",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    hooks=MyAgentHook()
)

result = Runner.run_sync(starting_agent=agent, input='hi how are you')
print(result.final_output)
```

#### on_end
* Called when the agent produces a final output.
* on_end Bydefault return None

##### Arg
```bash
(method) async def on_end(
    self: Self@MyAgentHook,
    context: RunContextWrapper[Any],
    agent: Agent[Any],
    output: Any
) -> None
```
---
```bash
class MyAgentHook(AgentHooks):
  #  async def on_start(self, context:RunContextWrapper, agent)->None:
  #  print("My Agent is Satrting...")
        
    async def on_end(self, context:RunContextWrapper, agent,output:Any)->None:
        print("My Agent is Ending...")
            
agent = Agent(
    name="assistance",
    instructions="You are a helpfull Assistance",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    hooks=MyAgentHook()
)

result = Runner.run_sync(starting_agent=agent, input='hi how are you')
print(result.final_output)
```
