

# Run Hooks
"RunHooks" OpenAI Agents SDK mein yani aik mechanism hai jise aap use kar ke agent execution ke global lifecycle events ko observe ya customize kar sakte hain. Ye aapko har step par callbacks execute karne ki facility deta hai—agent start, tool use, LLM calls, handoffs, final output, sab track ho sakta hai.

* Ye Runner.run() ya Runner.run_sync() methods mein hooks parameter ke through specify ki jaati hai, jisse aap har run ke global events pe custom logic execute kar sakte hain.
* RunHooks ek class hoti hai jo RunHooksBase se derive hoti hai aur agent runs ke dauran lifecycle events ke callbacks define karne ki permission deti hai.

### Key Lifecycle Callbacks
1. on_agent_start(ctx, agent)
2. on_agent_end(ctx, agent, output)
3. on_handoff(ctx, from_agent, to_agent)
4. on_tool_start(ctx, agent, tool)
5. on_tool_end(ctx, agent, tool, result)
6. on_llm_start(ctx, agent, system_prompt, input_items)
7. on_llm_end(ctx, agent, response)


### When to Use Run Hooks vs Agent Hooks

| Use Run Hooks When | Use Agent Hooks When |
|-------------------|---------------------|
| 🏢 Monitor entire system | 🏠 Monitor specific agent |
| 📊 System-wide analytics | 🔍 Debug one agent |
| 🤝 Track agent collaboration | 🎯 Agent-specific logic |
| 📈 Performance across all agents | 📝 Individual agent logs |
| 🔄 Understand handoff patterns | 🚨 Agent-specific alerts |



#### 1. on_agent_start
* Called before the agent is invoked. Called each time the current agent changes.

##### Arg
```bash
async def on_agent_start(
        self, context: RunContextWrapper[TContext], agent: Agent[TContext]
    ) -> None:
        """Called before the agent is invoked. Called each time the current agent changes."""
        pass
```
```bash
class MyRunHook(RunHooks):
    async def on_agent_start(self, ctx:RunContextWrapper, agent:Agent):
        print(f"[RUN] Agent `{agent.name}` End")

agent = Agent(
    name="assistance",
    instructions="You are a helpfull Assistance. if you asked weather realted question you want to handoff billing_check agent. you want to call weather_check tool for resolve user weather related query.",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
)
result = Runner.run_sync(starting_agent=agent, input='pay my bill',hooks=MyRunHook())
print(result.final_output)
```

#### 2. on_agent_end
* Called when the agent produces a final output.


##### Arg
```bash
async def on_agent_end(
        self,
        context: RunContextWrapper[TContext],
        agent: Agent[TContext],
        output: Any,
    ) -> None:
        """Called when the agent produces a final output."""
        pass
```        
```bash
from typing import Any

class MyRunHook(RunHooks):
    async def on_agent_end(self, context, agent, output: Any):
        print(f"[RUN] Agent `{agent.name}` End")

billing_check = Agent(
    name="assistance",
    instructions="You are a helpfull Assistance.",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
)
    
agent = Agent(
    name="assistance",
    instructions="You are a helpfull Assistance. if you asked weather realted question you want to handoff billing_check agent. you want to call weather_check tool for resolve user weather related query.",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
)

result = Runner.run_sync(starting_agent=agent, input='pay my bill',hooks=MyRunHook())
print(result.final_output)
```

#### 3. on_handoff
* Called when a handoff occurs.

##### Arg
```bash
async def on_handoff(
        self,
        context: RunContextWrapper[TContext],
        from_agent: Agent[TContext],
        to_agent: Agent[TContext],
    ) -> None:
        """Called when a handoff occurs."""
        pass
```

```bash
class MyRunHook(RunHooks):
    async def on_handoff(self, context, from_agent, to_agent):
        print(f"[RUN] on handoff `{from_agent.name}` Running")

billing_check = Agent(
    name="assistance",
    instructions="You are a helpfull Assistance.",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
)
    
agent = Agent(
    name="assistance",
    instructions="You are a helpfull Assistance. if you asked weather realted question you want to handoff billing_check agent. you want to call weather_check tool for resolve user weather related query.",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    handoffs=[billing_check]
)

result = Runner.run_sync(starting_agent=agent, input='pay my bill',hooks=MyRunHook())
print(result.final_output)
```

#### 4. on_tool_start
* Called before a tool is invoked.

##### Arg
```bash
async def on_tool_start(
        self,
        context: RunContextWrapper[TContext],
        agent: Agent[TContext],
        tool: Tool,
    ) -> None:
        """Called before a tool is invoked."""
        pass
```
```bash
class MyRunHook(RunHooks):
    async def on_tool_start(self, context, agent, tool):
        print(f"🔨 Tool os starting: {agent.name}")

@function_tool
def weather_check(input:str) ->str:
    return f"{input}weather is summy"

agent = Agent(
    name="assistance",
    instructions="You are a helpfull Assistance. if you asked weather realted question you want to handoff billing_check agent. you want to call weather_check tool for resolve user weather related query.",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    tools=[weather_check]
)

result = Runner.run_sync(starting_agent=agent, input='weather in karachi',hooks=MyRunHook())
print(result.final_output)
```

#### 5. on_tool_end
* Called after a tool is invoked.

##### Arg
```bash
async def on_tool_end(
        self,
        context: RunContextWrapper[TContext],
        agent: Agent[TContext],
        tool: Tool,
        result: str,
    ) -> None:
        """Called after a tool is invoked."""
        pass
```    
```bash
class MyRunHook(RunHooks):
    async def on_tool_end(self, context, agent, tool, result):
        print(f"🔨 Tool os end: {agent.name}")

@function_tool
def weather_check(input:str) ->str:
    return f"{input}weather is summy"

agent = Agent(
    name="assistance",
    instructions="You are a helpfull Assistance. if you asked weather realted question you want to handoff billing_check agent. you want to call weather_check tool for resolve user weather related query.",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    handoffs=[billing_check],
    tools=[weather_check]
)

result = Runner.run_sync(starting_agent=agent, input='weather in karachi',hooks=MyRunHook())
print(result.final_output)
```


#### 6. on_llm_start
* same a agenthooks
#### 7. on_llm_end
* same a agenthooks



### Advanced Example - Multi-Agent Analytics
```bash
import time
from datetime import datetime

class MultiAgentAnalytics(RunHooksBase):
    def __init__(self):
        self.start_time = None
        self.agent_stats = {}
        self.system_stats = {
            'total_llm_calls': 0,
            'total_tool_calls': 0,
            'total_handoffs': 0
        }
    
    def _init_agent_stats(self, agent_name):
        if agent_name not in self.agent_stats:
            self.agent_stats[agent_name] = {
                'start_time': None,
                'total_time': 0,
                'llm_calls': 0,
                'tool_calls': 0
            }
    
    async def on_agent_start(self, context, agent):
        if self.start_time is None:
            self.start_time = time.time()
        
        self._init_agent_stats(agent.name)
        self.agent_stats[agent.name]['start_time'] = time.time()
        
        timestamp = datetime.now().strftime("%H:%M:%S")
        print(f"🌅 [{timestamp}] SYSTEM: {agent.name} started working")
    
    async def on_llm_start(self, context, agent, system_prompt, input_items):
        self._init_agent_stats(agent.name)
        self.agent_stats[agent.name]['llm_calls'] += 1
        self.system_stats['total_llm_calls'] += 1
        
        print(f"📞 SYSTEM: {agent.name} LLM call #{self.agent_stats[agent.name]['llm_calls']}")
    
    async def on_llm_end(self, context, agent, response):
        print(f"🧠✨ SYSTEM: {agent.name} got LLM response")
    
    async def on_tool_start(self, context, agent, tool):
        self._init_agent_stats(agent.name)
        self.agent_stats[agent.name]['tool_calls'] += 1
        self.system_stats['total_tool_calls'] += 1
        
        print(f"🔨 SYSTEM: {agent.name} tool call #{self.agent_stats[agent.name]['tool_calls']} ({tool.name})")
    
    async def on_tool_end(self, context, agent, tool, result):
        print(f"✅🔨 SYSTEM: {agent.name} finished {tool.name}")
        print(f"   Result length: {len(str(result))} characters")
    
    async def on_handoff(self, context, from_agent, to_agent):
        self.system_stats['total_handoffs'] += 1
        print(f"🏃‍♂️➡️🏃‍♀️ HANDOFF #{self.system_stats['total_handoffs']}: {from_agent.name} → {to_agent.name}")
    
    async def on_agent_end(self, context, agent, output):
        if agent.name in self.agent_stats and self.agent_stats[agent.name]['start_time']:
            duration = time.time() - self.agent_stats[agent.name]['start_time']
            self.agent_stats[agent.name]['total_time'] = duration
        
        print(f"✅ SYSTEM: {agent.name} finished")
        print(f"   Duration: {duration:.2f}s")
        print(f"   LLM calls: {self.agent_stats[agent.name]['llm_calls']}")
        print(f"   Tool calls: {self.agent_stats[agent.name]['tool_calls']}")
        
        # Print system summary
        total_time = time.time() - self.start_time if self.start_time else 0
        print(f"\n📊 SYSTEM STATS:")
        print(f"   Total runtime: {total_time:.2f}s")
        print(f"   Total LLM calls: {self.system_stats['total_llm_calls']}")
        print(f"   Total tool calls: {self.system_stats['total_tool_calls']}")
        print(f"   Total handoffs: {self.system_stats['total_handoffs']}")
        print(f"   Agents used: {list(self.agent_stats.keys())}")
```        


### 1. System Performance Monitoring
```bash
class PerformanceMonitor(RunHooksBase):
    async def on_agent_start(self, context, agent):
        print(f"⚡ Performance: {agent.name} started")
    
    async def on_llm_start(self, context, agent, system_prompt, input_items):
        print(f"🧠 Performance: LLM call initiated by {agent.name}")
    
    async def on_tool_start(self, context, agent, tool):
        print(f"🔧 Performance: {tool.name} tool started by {agent.name}")
```


### 2. Audit Trail & Compliance 
```bash
class AuditTrail(RunHooksBase):
    def __init__(self):
        self.audit_log = []
    
    async def on_agent_start(self, context, agent):
        self.audit_log.append(f"AGENT_START: {agent.name} at {datetime.now()}")
    
    async def on_handoff(self, context, from_agent, to_agent):
        self.audit_log.append(f"HANDOFF: {from_agent.name} → {to_agent.name} at {datetime.now()}")
    
    async def on_tool_start(self, context, agent, tool):
        self.audit_log.append(f"TOOL_USE: {agent.name} used {tool.name} at {datetime.now()}")
```

### 3. User Experience Updates
```bash
class UserExperienceTracker(RunHooksBase):
    async def on_agent_start(self, context, agent):
        if agent.name == "CustomerService":
            print("👋 Our customer service team is helping you...")
        elif agent.name == "TechnicalSupport":
            print("🔧 Connecting you with technical support...")
        elif agent.name == "BillingManager":  
            print("💰 Our billing specialist is handling your request...")
    
    async def on_handoff(self, context, from_agent, to_agent):
        print(f"🔄 Transferring you from {from_agent.name} to {to_agent.name}")
    
    async def on_tool_start(self, context, agent, tool):
        if tool.name == "database_lookup":
            print("🔍 Looking up your account information...")
        elif tool.name == "process_refund":
            print("💳 Processing your refund...")
```

#### ❌ Don't Do This:
```bash
# Confusing run hooks with agent hooks
agent.hooks = RunHooksBase()  # Wrong! Use AgentHooksBase for agents

# Forgetting to pass run_hooks to run()
result = run(agents=agent1)  # No monitoring!
```
