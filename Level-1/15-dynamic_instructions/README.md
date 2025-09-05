
## Dynamic instructions
In most cases, you can provide instructions when you create the agent. However, you can also provide dynamic instructions via a function. The function will receive the agent and context, and must return the prompt. Both regular and async functions are accepted.

#### instructions Perameters
```bash
instructions: (
        str
        | Callable[
            [RunContextWrapper[TContext], Agent[TContext]],
            MaybeAwaitable[str],
        ]
        | None
    ) = None
    """The instructions for the agent. Will be used as the "system prompt" when this agent is
    invoked. Describes what the agent should do, and how it responds.

    Can either be a string, or a function that dynamically generates instructions for the agent. If
    you provide a function, it will be called with the context and the agent instance. It must
    return a string.
    """
```
* instructions peramters me first pr str le sakta ha.
* second me eik function bhi le sakta ha jo str return kry. or wo function async or sync dono ho sakty hai. or us function ke peramter
me RunContextWrapper[TContext] or Agent[TContext] dena zarori ha


### 1. Simple sync function

```python
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel,RunContextWrapper,

def dynamic_instructure(ctx: RunContextWrapper, agent: Agent) ->str:
    return "You are a helpful assistant."

agent = Agent(
    name="Assistance",
    instructions=dynamic_instructure,
    model=model,
)
```

### 2. Get Agent Name
```python
def dynamic_instructions(context: RunContextWrapper, agent: Agent) -> str:
    return f"You are {agent.name}. Adapt to the user's needs."

agent = Agent(
    name="Smart Assistant",
    instructions=dynamic_instructions 
)

result = Runner.run_sync(starting_agent=agent, input="", run_config=config)
print(result.final_output)
```

### 3. Other Example With Context

```python
async def dynamic_instructure(ctx: RunContextWrapper, agent: Agent) ->str:
    return f"i am {ctx.context} how are"

agent = Agent(
    name="Assistance",
    instructions=dynamic_instructure,
    model=model,
)
result = Runner.run_sync(starting_agent=agent,input='hi how are you',run_config=config,context="hussain")
print("Final Output:", result.final_output)
```
* async or sync dono function use kr sakty ha run, rync  run_stream ke sath 


### 4. Same Example With Pydentic Class
```bash
from pydentic import BaseModel

class UserInfo(BaseModel):
    user_name: str
    
users_info_obj  = UserInfo(user_name="hussain")  

async def dynamic_instructure(ctx: RunContextWrapper[UserInfo], agent: Agent) ->str:
    return f"i am {ctx.context.user_name} how are"

agent = Agent(
    name="Assistant",
    instructions=dynamic_instructure,
    model=model,
)
```

### 5. Same Example With Python Class 
```bash
class Dynamic_Class():
    def __init__(self):
        pass
    
    def __call__(self,ctx:RunContextWrapper,agent:Agent) ->str:
        return "you are English teacher"

dynamic_obj = Dynamic_Class()

agent = Agent(
    name="Assistant",
    instructions=dynamic_obj,
    model=model,
)

result = Runner.run_sync(starting_agent=agent,input='how are you?',run_config=config)
print(result.final_output)
```

### 6. Async Dynamic Instructions
```bash
import asyncio

async def async_instructions(context: RunContextWrapper, agent: Agent) -> str:
    # Simulate fetching data from database
    await asyncio.sleep(0.1)
    current_time = datetime.datetime.now()
    
    return f"""You are {agent.name}, an AI assistant with real-time capabilities.
    Current time: {current_time.strftime('%H:%M')}
    Provide helpful and timely responses."""

agent = Agent(
    name="Async Agent",
    instructions=async_instructions
)
```

### 7. Time-Based Instructions 
```bash
import datetime

def time_based(context: RunContextWrapper, agent: Agent) -> str:
    current_hour = datetime.datetime.now().hour
    
    if 6 <= current_hour < 12:
       # print(current_hour)
        return f"You are {agent.name}. Good morning! Be energetic and positive."
    elif 12 <= current_hour < 17:
       # print(current_hour)
        return f"You are {agent.name}. Good afternoon! Be focused and productive."
    else:
       # print(current_hour)
        return f"You are {agent.name}. Good evening! Be calm and helpful."

agent = Agent(
    name="Assistant",
    instructions=time_based,
    model=model,
)
```
#### Context Parameter

The context contains:
* Messages: Conversation history
* User data: Custom user information
* Run state: Current execution state
* Metadata: Additional information

### 8. Stateful Instructions (Remembers Interactions)
```python

class StatefulInstructions:
    def __init__(self):
        self.interaction_count = 0
    
    def __call__(self, context: RunContextWrapper, agent: Agent) -> str:
        self.interaction_count += 1
        
        if self.interaction_count == 1:
            return "You are a learning assistant. This is our first interaction - be welcoming!"
        elif self.interaction_count <= 3:
            return f"You are a learning assistant. This is interaction #{self.interaction_count} - build on our conversation."
        else:
            return f"You are an experienced assistant. We've had {self.interaction_count} interactions - be efficient."

instruction_gen = StatefulInstructions()

agent = Agent(
    name="Smart Assistant",
    instructions=instruction_gen 
)

query =  input("Enter Query : ")

result = Runner.run_sync(starting_agent=agent, input=query, run_config=config)
print(result.final_output)
```

### Agent Parameter
The agent contains:
* Name: Agent's identity
* Tools: Available tools
* Settings: Model settings
* Configuration: Agent configuration


### 
```python
def explore_agent(context: RunContextWrapper, agent: Agent) -> str:
    # Access agent properties
    agent_name = agent.name
    tool_count = len(agent.tools)
    
    return f"You are {agent_name} with {tool_count} tools. Be helpful!"
```    