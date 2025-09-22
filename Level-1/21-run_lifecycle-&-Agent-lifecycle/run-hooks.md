

# Run Hooks
"RunHooks" OpenAI Agents SDK mein yani aik mechanism hai jise aap use kar ke agent execution ke global lifecycle events ko observe ya customize kar sakte hain. Ye aapko har step par callbacks execute karne ki facility deta hai—agent start, tool use, LLM calls, handoffs, final output, sab track ho sakta hai.

* Ye Runner.run() ya Runner.run_sync() methods mein hooks parameter ke through specify ki jaati hai, jisse aap har run ke global events pe custom logic execute kar sakte hain.
* RunHooks ek class hoti hai jo RunHooksBase se derive hoti hai aur agent runs ke dauran lifecycle events ke callbacks define karne ki permission deti hai.

### Key Lifecycle Callbacks
1. on_agent_start(self, ctx:RunContextWrapper, agent:Agent)
2. on_agent_end(self, context, agent, output: Any)
3. on_handoff(self, context, from_agent, to_agent)
4. on_tool_start(self, context, agent, tool)
5. on_tool_end(self, context, agent, tool, result)
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



### 1. Generic kya hai?
* Jadatar programming languages me, agar ek class ya function sirf ek ek hi type (jaise int, string, etc.) ke sath likhi ho, to agar doosre type ke sath use karna ho to baar-baar same code likhna padega.
* Generics allow karte hain ke aap ek function/class/etc define karo jis me type define na ho abhi, balki placeholder ya type variable ho. Phir jab use karna ho to specific type pass karo.
* Is se fayda ye hai ke code ek hi baar likhoge, phir alag alag types ke sath use ho sakta hai, aur compile-time pe type checking hoti hai, run-time errors kam hote hain.

---
* Type parameter / Type variable: Ye wo placeholder hai, jaise T, U, ContextType, etc.
* Type argument: Jahaan use karoge, placeholder ki jagah actual type specify karoge, jaise int, string, MyContext, etc.

### 2. Generics ke fayde
* Reusability: Ek hi code alag alag types ke sath chal sakta hai.
* Type safety: Compile time pe check hota hai ke sahi type use ho raha hai, galat type errors pehle hi catch hogayenge.
* Less duplication: Bar-bar similar code likhne ki zaroorat kam.
* Cleaner aur maintainable code.

```python
from typing import TypeVar, Generic

# TypeVar se ek type placeholder banate hain
T = TypeVar('T')

# Generic[T] ka matlab hai ke Box class kisi bhi type T ka content rakh sakti hai
class Box(Generic[T]):
    def __init__(self, content: T) -> None:
        self.content = content

    def get_content(self) -> T:
        return self.content

    def set_content(self, new_content: T) -> None:
        self.content = new_content

# Ab hum alag alag types ke saath Box use kar sakte hain
int_box = Box 
print(int_box.get_content())  # output: 123, type int

str_box = Box[str]("Hello")
print(str_box.get_content())  # output: Hello, type str

# Agar galti se wrong type daalte ho:
# str_box.set_content(456)  # Static type checker warning dega kyunki str_box content str hona chahiye
```

---

### 3. Generic Types aur TContext
* [TContext] Python me generics ka part hai. Yani aap ek class ya function ko is tarah define karte ho ke usme context ki type dynamic ho sakti hai; generic parameter TContext define karta hai ke kis type ka context pass hoga.
* Jab aap agent run karte ho, aap ek specific context object provide karte ho, jiska type TContext hoga. Isse SDK ko pata hai ke saari hooks / callbacks me context ka type kia hai.


### 4. RunContextWrapper[TContext]
Ye ek wrapper class hai jo aapke run ke local context ko carry karta hai. 
* RunContextWrapper ke andar ek property context hogi jisme actual context object hota hai, jiski type TContext hai. 
* Ye context object wo cheezein hoti hain jo aap run ke through chalayenge — jaise user info, dependencies (logger, database connector), etc. SDK use karta hai to pass that context through tools, agent lifecycle hooks etc.

### 5. Agent[TContext]
* Agent bhi generic hai is sense me ke wo janta hai ke uska context kis type ka hai. Yani agar aap Agent[SomeContextType] banoge, to is agent ka saara behavior/context tools, hooks, etc that type se related hoega. 
* Ye ensure karta hai type safety: aap wrong type ka context pass nahi karoge, ya tools/hook functions me mismatch nahi hoga.
