
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
```bash
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel,RunContextWrapper,

def dynamic_instructure(ctx: RunContextWrapper, agent: Agent) ->str:
    return "You are a helpful assistant."

agent = Agent(
    name="Assistance",
    instructions=dynamic_instructure,
    model=model,
)
```

### 2. Other Example With Context
```bash
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


### 3. Same Example With Pydentic Class
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

### 4. Same Example With Python Class 
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

### 5. Async Dynamic Instructions
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

### 6. Time-Based Instructions 
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