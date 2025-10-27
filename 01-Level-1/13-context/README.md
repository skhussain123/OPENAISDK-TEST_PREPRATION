

[OpenAi to Study Context management](https://openai.github.io/openai-agents-python/context/)

# Context Management
Context management in the OpenAI Agents SDK refers to handling additional data that your code can use during an agent’s execution. This “context” comes in two main forms:

## 1. Local Context
What It Is:
Local context is any data or dependencies you pass to your agent's run that your code (tools, lifecycle hooks, etc.) can use. It’s entirely internal and never sent to the LLM.

### How It Works:

#### Creating Context:
You create a Python object—often using a dataclass or a Pydantic model—to encapsulate data like a username, user ID, logger, or helper functions.

#### Passing Context:
You pass this object to the run method (e.g., Runner.run(..., context=your_context)). The SDK wraps your object in a RunContextWrapper, making it available to every tool function, lifecycle hook, or callback during that run via wrapper.context.

#### Key Point:
All parts of a single agent run must share the same type of context, ensuring consistency.


### Example Use Cases:

* Storing user details (e.g., a username or ID) that your tools might need.
* Injecting dependencies such as loggers or data fetchers.
* Providing helper functions accessible throughout the run.

Note: This local context is not exposed to the LLM. It’s solely for your backend logic and operations.

## 2. Agent/LLM Context
What It Is:
Agent/LLM context refers to the information the LLM sees when it generates responses. This is essentially the conversation history or messages (like system prompts, instructions, and user inputs) that guide its output.

### How to Use It:
#### Embedding in Instructions:
Include important context (like the user’s name, current date, or specific guidelines) directly in the agent’s instructions or system prompts.

#### Passing in Inputs:
You can also add context to the input message when calling Runner.run(), ensuring that this data is part of the conversation that the LLM processes.

#### Function Tools:
The LLM may also invoke function tools to fetch on-demand data that wasn’t initially part of its conversation history.

#### Retrieval/Web Search:
Use specialized tools to pull in relevant external data, thereby grounding the LLM’s responses in up-to-date or detailed information.

### Key Difference:
While the local context is internal and never sent to the LLM, the agent/LLM context is deliberately exposed as part of the conversation to influence and guide the LLM’s response generation.

### what is pydantic
Ye Python ke sabse mashhoor libraries mein se ek hai jo data validation aur parsing ke liye use hoti hai

* Pydantic ek Python library hai jo data validation aur settings management ke liye use hoti hai, aur kaafi popular hai. 
*  Iska design Python ke type annotations par based hai — matlab aap data ke structure ko Python classes ke zariye define karte ho, aur Pydantic khud ensure karta hai ke input data un types ke mutabiq ho


### (class) RunContextWrapper
```bash
@dataclass
class RunContextWrapper(Generic[TContext]):
    """This wraps the context object that you passed to `Runner.run()`. It also contains
    information about the usage of the agent run so far.

    NOTE: Contexts are not passed to the LLM. They're a way to pass dependencies and data to code
    you implement, like tool functions, callbacks, hooks, etc.
    """

    context: TContext
    """The context object (or None), passed by you to `Runner.run()`"""

    usage: Usage = field(default_factory=Usage)
    """The usage of the agent run so far. For streamed responses, the usage will be stale until the
    last chunk of the stream is processed.
    """
```

---
## Local Context
```bash
import os
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel,set_tracing_disabled,RunContextWrapper
from dotenv import load_dotenv
from pydantic import BaseModel

class UserInfo(BaseModel):
    name: str
    age: int
    city: str
    roll_num: str
    
    
my_info  = UserInfo(name="hussain",age=22,city="Karachi",roll_num="343432")  
 
# this is a python custom function for fetch user info with RunContextWrapper
def check_info(wrapper: RunContextWrapper[UserInfo],agent:Agent):
    return f"the user name is {wrapper.context.name}, the user age is {wrapper.context.age} the user city is {wrapper.context.city}the user roll_num is {wrapper.context.roll_num}"

myagent =  Agent[UserInfo](
    name="assistance",
    instructions="you are a helpfull assistant",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client)
)

result = Runner.run_sync(starting_agent=myagent, input='what is the age of hussain',context=my_info)
print(result.final_output)
```

---
* check_info simple python function ha jo RunContextWrapper sy user ki info nikal kr agent ko de raha hoga.

## Local or LLm Context Example one
```python
import os
from typing import Any
from agents import Agent, RunContextWrapper, Runner, OpenAIChatCompletionsModel,AsyncOpenAI,handoff, function_tool,enable_verbose_stdout_logging
from agents.run import RunConfig
from dotenv import load_dotenv
from pydantic import BaseModel


load_dotenv()

gemini_key = os.getenv('GEMINI_API_KEY')
# enable_verbose_stdout_logging()

if not gemini_key:
    raise ValueError("API KEY is NOT Laoded")


external_client = AsyncOpenAI(
    api_key=gemini_key,
     base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

model = OpenAIChatCompletionsModel(
    model='gemini-2.0-flash',
    openai_client=external_client
)

config = RunConfig(
    model=model,
    model_provider=external_client,
    tracing_disabled=True    
)

class UserInfo(BaseModel):
    name: str
    age: int
    city: str
    roll_num: str
    
    
my_info  = UserInfo(name="hussain",age=22,city="Karachi",roll_num="343432")  
 
# this is a python custom function for fetch user info with RunContextWrapper
def check_info(wrapper: RunContextWrapper[UserInfo],agent:Agent):
    return f"the user name is {wrapper.context.name}, the user age is {wrapper.context.age} the user city is {wrapper.context.city}the user roll_num is {wrapper.context.roll_num}"

myagent =  Agent[UserInfo](
    name="assistance",
    instructions=check_info,
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client)
)

result = Runner.run_sync(starting_agent=myagent, input='what is the age of hussain',context=my_info)
print(result.final_output)
```

---
## Local or Agent/LLM context Example 2
```bash
import os
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel,set_tracing_disabled,RunContextWrapper,function_tool,enable_verbose_stdout_logging
from dotenv import load_dotenv
from pydantic import BaseModel


# Load API key
load_dotenv()
set_tracing_disabled(disabled=True)
# enable_verbose_stdout_logging()

gemini_api_key = os.getenv('GEMINI_API_KEY')
if not gemini_api_key:
    raise ValueError("API key is not loaded")

external_client = AsyncOpenAI(
    api_key=gemini_api_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

class UserInfo(BaseModel):
    user_id : int
    user_name : str
    user_father : str


user_check = UserInfo(user_id=1354280,user_name="Hussain",user_father="Faheem")

# Local Context Data Get in Tool
@function_tool
def students_data(wrapper: RunContextWrapper[UserInfo], query_type: str, name: str = None):
    """Fetches student data based on the query type and optional name filter."""
    if name and wrapper.context.user_name.lower() != name.lower():
        return f"No student found with name {name}"
    if query_type == "father_name":
        return f"The father name of {wrapper.context.user_name} is {wrapper.context.user_father}"
    elif query_type == "user_id":
        return f"The user ID of {wrapper.context.user_name} is {wrapper.context.user_id}"
    else:
        return f"The user name is {wrapper.context.user_name}, the user ID is {wrapper.context.user_id}, the father name is {wrapper.context.user_father}"
    

myagent = Agent[UserInfo](
    name="students data management system",
    instructions="For student-related queries, use the students_data tool. Pass 'father_name' as query_type for father name queries, and include the student's name if specified in the query.",
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash', openai_client=external_client),
    tools=[students_data],
)

query =  "what is father name of hussain?"

result = Runner.run_sync(starting_agent=myagent, input=query,context=user_check)
print(result.final_output)
```

