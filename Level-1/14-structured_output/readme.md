
# Structured Output with Pydantic
Structured outputs are crucial when you need your AI agents to provide data in a predictable and usable format. Instead of free-form text, you can enforce a specific structure, making it easier for your applications to parse and utilize the information. The OpenAI Agents SDK provides mechanisms to achieve this

--- 

The type of the output object. If not provided, the output will be `str`. In most cases,
* you should pass a regular Python type (e.g. a dataclass, Pydantic model, TypedDict, etc).
* You can customize this in two ways:
1. If you want non-strict schemas, pass `AgentOutputSchema(MyClass, strict_json_schema=False)`.
2. If you want to use a custom JSON schema (i.e. without using the SDK's automatic schema) creation, subclass and pass an `AgentOutputSchemaBase` subclass.


### Why Use Structured Outputs?

* Data Parsing: Easier to extract specific information without complex text parsing(convert).
* Integration: Seamless integration with other systems that expect structured data (e.g., databases, APIs).
* Reliability: Reduces ambiguity and ensures consistent data formatting.
* Automation: Automate workflows that rely on specific data points.

## Structured Outputs vs. JSON Mode:
It's important to differentiate between "Structured Outputs" and the simpler "JSON mode." "JSON mode" ensures that the output is valid JSON, but it doesn't guarantee that it conforms to a specific schema. "Structured Outputs" goes further, guaranteeing schema adherence. This is a very important distinction.

```python
from dotenv import load_dotenv
from pydantic import BaseModel, Field


class StuctureOur(BaseModel):
    is_name : bool = Field(description="if user name is available it value will be True othetwise it will be False")
    user_name : str  = Field(description="usre name if available, other wise value will be None")
    age : int  = Field(description="usre age will e in this field, if age is less then 16 so insert 0")


triage_agent = Agent(
    name="Assistant",
    instructions="You are a helpfull assistant",
    output_type=StuctureOur
)

result = Runner.run_sync(starting_agent=triage_agent, input="Hi i am hussain, How are you, i am 1 year old", run_config=config )
print("Final Output:", result.final_output)
```

### With Conditions
```python
from dotenv import load_dotenv
from pydantic import BaseModel, Field

class StuctureOur(BaseModel):
    is_name : bool = Field(description="if user name is available it value will be True othetwise it will be False")
    user_name : str  = Field(default=None, description="usre name if available, other wise value will be None")
    age : int  = Field(default=1, description="usre age will e in this field, if age is less then 16 so insert 0")


triage_agent = Agent(
    name="Assistant",
    instructions="You are a helpfull assistant",
    output_type=StuctureOur
)

result = Runner.run_sync(starting_agent=triage_agent, input="Hi i am hussain, i am 18 year old", run_config=config )

if result.final_output.is_name:
    
    if result.final_output.user_name:
        print(f"User name is: {result.final_output.user_name}")

    if result.final_output.age > 0:
        print(f"User age is: {result.final_output.age}")

```