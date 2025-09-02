


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
from agents import Agent, Runner, AsyncOpenAI,OpenAIChatCompletionsModel,AgentHooks,set_tracing_disabled,RunContextWrapper,function_tool
from dotenv import load_dotenv
from typing import Any
import os

class MyAgentHook(AgentHooks):
     async def on_start(self, context:RunContextWrapper, agent)->None:
       print(f"✅ {agent.name} Starting using {agent.name}")
        
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
        print(f"✅ {agent.name} Starting using {agent.name}")
            
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
        print(f"✅ {source.name} Starting using {agent.name}")
            
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
    async def on_tool_start(self, context:RunContextWrapper, agent:Agent, tool)->None:
        print(f"✅ {agent.name} Starting using {tool.name}")
 

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

### on_llm_start aur on_llm_end kya hain?

Ye methods AgentHooks ke part hain jo aap hooks parameter ke zariye agent mein attach karte hain. Ye lifecycle hooks hain jo agent ke run ke dauran specific events ko monitor karte hain 
OpenAI GitHub
.

---
#### 1. on_llm_start(...)
##### Arg
```bash
(method) async def on_llm_start(
    self: Self@MyAgentHook,
    context: Any,
    agent: Any,
    system_prompt: Any,
    input_items: Any
) -> None
```

* Jab agent LLM (jaise Gemini ya GPT) se response lene waala hota hai, tab ye method chalti hai.
* Ye aapko notify karti hai ke “agent AI se madad maang raha hai”, ya similar message console ya log mein show kar sakte hain.
```bash
class MyAgentHook(AgentHooks):
    async def on_llm_start(self, context, agent, system_prompt, input_items):
        print(f"📞 {agent.name} AI se madad maang raha hai")

agent = Agent(
    name="assistance",
    instructions="You are a helpfull Assistance. if you asked weather realted question you want to call weather_check tool",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    hooks=MyAgentHook(),
)
result = Runner.run_sync(starting_agent=agent, input='hi')
print(result.final_output)
```

#### 2. on_llm_end(...)

* Jab LLM se response agent ko mil jaata hai, tab ye method trigger hoti hai.
* Iska purpose hai inform karna ke “agent ko AI ka jawab mil gaya” — ek tarah se aap execution ke transition ko trace karte hain.

##### Arg
```bash
(method) async def on_llm_end(
    self: Self@MyAgentHook,
    context: Any,
    agent: Any,
    response: Any
) -> None
```


```bash
class MyAgentHook(AgentHooks):
    async def on_llm_end(self, context, agent, response):
        print(f"🧠✨ {agent.name} ko AI ka jawab mil gaya")

agent = Agent(
    name="assistance",
    instructions="You are a helpfull Assistance. if you asked weather realted question you want to call weather_check tool",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    hooks=MyAgentHook(),
)
result = Runner.run_sync(starting_agent=agent, input='hi')
print(result.final_output)
```

#### ❌ Don't Do This:
```bash
# Forgetting async
def on_start(self, context, agent):  # Missing 'async'!
    print("Started")

# Trying to return values from hooks
async def on_tool_end(self, context, agent, tool, result):
    return "modified result"  # Hooks don't return values!
```

### Complete Code Example
```bash
from agents import Agent, Runner, AsyncOpenAI,OpenAIChatCompletionsModel,AgentHooks,set_tracing_disabled,RunContextWrapper,function_tool
from dotenv import load_dotenv
import time
from datetime import datetime
import os

load_dotenv()
set_tracing_disabled(disabled=False)

gemini_api_key = os.getenv('GEMINI_API_KEY')
if not gemini_api_key:
    raise ValueError("API key is not loaded")

external_client = AsyncOpenAI(
    api_key=gemini_api_key,
     base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

class MyAgentHook(AgentHooks):
    def __init__(self):
        self.start_time = None
        self.llm_calls = 0
        self.tool_calls = 0
    
    async def on_start(self, context, agent):
        self.start_time = time.time()
        self.llm_calls = 0
        self.tool_calls = 0
        timestamp = datetime.now().strftime("%H:%M:%S")
        print(f"🕘 [{timestamp}] {agent.name} became active")
    
    async def on_llm_start(self, context, agent, system_prompt, input_items):
        self.llm_calls += 1
        print(f"📞 LLM Call #{self.llm_calls}: {agent.name} asking AI for guidance")
        print(f"   Input: {len(input_items)} items to think about")
    
    async def on_llm_end(self, context, agent, response):
        print(f"🧠✨ LLM Call #{self.llm_calls} completed")
        print(f"   AI response length: {len(str(response))} characters")
    
    async def on_tool_start(self, context, agent, tool):
        self.tool_calls += 1
        print(f"🔨 Tool #{self.tool_calls}: {agent.name} using {tool.name}")
    
    async def on_tool_end(self, context, agent, tool, result):
        print(f"✅🔨 Tool #{self.tool_calls} completed")
        print(f"   Result preview: {str(result)[:50]}...")
    
    async def on_handoff(self, context, agent, source):
        print(f"🏃‍♂️➡️🏃‍♀️ {agent.name} received work from {source.name}")
        print(f"   Work is being transferred due to specialization")
    
    async def on_end(self, context, agent, output):
        duration = time.time() - self.start_time if self.start_time else 0
        print(f"✅ {agent.name} FINISHED in {duration:.2f} seconds")
        print(f"📊 Total: {self.llm_calls} AI calls, {self.tool_calls} tool uses")
        print(f"🎯 Final result: {str(output)[:100]}...")


billing_check = Agent(
    name="billing_check",
    instructions="Yor are a billing assistance",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
)

@function_tool
def weather_check(input:str) ->str:
    return "f{input}weather is sunny"

agent = Agent(
    name="assistance",
    instructions="You are a helpfull Assistance. if you asked weather realted question you want to handoff billing_check agent. you want to call weather_check tool for resolve user weather related query.",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    hooks=MyAgentHook(),
    tools=[weather_check],
    handoffs=[billing_check]
)

result = Runner.run_sync(starting_agent=agent, input='pay my bill')
print(result.final_output)
```