


### What Is AgentHooks?
* AgentHooks is a class that each Agent instance can optionally use.
* It functions as an event emitter, emitting lifecycle events such as when the agent starts, ends, calls a tool, or receives a handoff.
* It is scoped per-agent, meaning it's only active for the agent it's attached to—not global across all agents.

#### Key Capabilities
* on_start / on_end: Triggered when the agent begins or finishes execution.
* on_tool_start / on_tool_end: Called when a tool invocation starts or completes.
* on_handoff: Fires when the agent hands off to another sub-agent.

---

#### 1. on_start
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

#### 2. on_end
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

#### 3. on_handoff
* Called when the agent is being handed off to. The `source` is the agent that is handing
off to this agent.
* on_handoff Bydefault return None

##### Arg
```bash
(method) async def on_handoff(
    self: Self@MyAgentHook,
    context: RunContextWrapper[Any],
    agent: Agent[Any],
    source: Agent[Any]
) -> None
```

```bash
class MyAgentHook(AgentHooks):

    async def on_handoff(self, context:RunContextWrapper, agent:Agent, source:Agent)->None:
        print("Handoff is start")
            
second_agent = Agent(
    name="second_agent",
    instructions="You are a Assistance",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
)
 
agent = Agent(
    name="assistance",
    instructions="You are a helpfull Assistance",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    hooks=MyAgentHook(),
    handoffs=[second_agent]
)
result = Runner.run_sync(starting_agent=agent, input='call second_agent')
print(result.final_output)
```

#### 4. on_tool_start
* Called before a tool is invoked."""
* on_tool_start Bydefault return None

##### Arg
```bash
(method) async def on_tool_start(
    self: Self@MyAgentHook,
    context: RunContextWrapper[Any],
    agent: Agent[Any],
    source: Agent[Any]
) -> None
```

```bash
class MyAgentHook(AgentHooks):
    async def on_tool_start(self, context:RunContextWrapper, agent:Agent, source:Agent)->None:
        print("Tool calling is Start...")
 

@function_tool
def weather_check(input:str) -> str:
    return f"{input} weather is sunny"
                   
agent = Agent(
    name="assistance",
    instructions="You are a helpfull Assistance. if you asked weather realted question you want to call weather_check tool",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    hooks=MyAgentHook(),
    tools=[weather_check]
)
result = Runner.run_sync(starting_agent=agent, input='what is weather in karachi')
print(result.final_output)
```


#### 5. on_tool_end
* Called after a tool is invoked.
* on_tool_end Bydefault return None

##### Arg
```bash
(method) async def on_tool_end(
    self: Self@AgentHooks[TContext@AgentHooks],
    context: RunContextWrapper[TContext@AgentHooks],
    agent: Agent[TContext@AgentHooks],
    tool: Tool,
    result: str
) -> None
```

```bash
class MyAgentHook(AgentHooks):  
    async def on_tool_end(self, context:RunContextWrapper, agent:Agent, tool, resultr)->None:
          print(f"✅ {agent.name} finished using {tool.name}")
 

@function_tool
def weather_check(input:str) -> str:
    return f"{input} weather is sunny"
                   
agent = Agent(
    name="assistance",
    instructions="You are a helpfull Assistance. if you asked weather realted question you want to call weather_check tool",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    hooks=MyAgentHook(),
    tools=[weather_check]
)
result = Runner.run_sync(starting_agent=agent, input='what is weather in karachi')
print(result.final_output)
```
