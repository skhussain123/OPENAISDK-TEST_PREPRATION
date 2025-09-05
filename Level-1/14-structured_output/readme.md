
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

### Example 1
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

### Example 2 With Conditions
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

### Example 3
```python
# Define your data structure
class PersonInfo(BaseModel):
    name: str
    age: int
    occupation: str
    

# Create agent with structured output
triage_agent = Agent(
    name="InfoCollector",
    instructions="Extract person information from the user's message.",
    output_type=PersonInfo
)

result = Runner.run_sync(starting_agent=triage_agent, input="Hi, I'm Alice, I'm 25 years old and I work as a teacher.", run_config=config )

print("Type:", type(result.final_output))        # <class 'PersonInfo'>
print("Name:", result.final_output.name)         # "Alice"
print("Age:", result.final_output.age)           # 25
print("Job:", result.final_output.occupation)    # "teacher"
```

### 4. Different Data Types
```python
from pydantic import BaseModel
from typing import List, Optional


class ActionItem(BaseModel):
    task: str
    assignee: str
    due_date: Optional[str] = None
    priority: str = "medium"

class Decision(BaseModel):
    topic: str
    decision: str
    rationale: Optional[str] = None

class MeetingMinutes(BaseModel):
    meeting_title: str
    date: str
    attendees: List[str]
    agenda_items: List[str]
    key_decisions: List[Decision]
    action_items: List[ActionItem]
    next_meeting_date: Optional[str] = None
    meeting_duration_minutes: int

# Meeting minutes extractor
agent = Agent(
    name="MeetingSecretary",
    instructions="""Extract structured meeting minutes from meeting transcripts.
    Identify all key decisions, action items, and important details.""",
    output_type=MeetingMinutes
)


meeting_transcript = """
Marketing Strategy Meeting - January 15, 2024
Attendees: Sarah (Marketing Manager), John (Product Manager), Lisa (Designer), Mike (Developer)
Duration: 90 minutes

Agenda:
1. Q1 Campaign Review
2. New Product Launch Strategy  
3. Budget Allocation
4. Social Media Strategy

Key Decisions:
- Approved $50K budget for Q1 digital campaigns based on strong ROI data
- Decided to launch new product in March instead of February for better market timing
- Will focus social media efforts on Instagram and TikTok for younger demographics

Action Items:
- Sarah to create campaign timeline by January 20th (high priority)
- John to finalize product features by January 25th
- Lisa to design landing page mockups by January 22nd
- Mike to review technical requirements by January 30th

Next meeting: January 29, 2024
"""

result = Runner.run_sync(
    starting_agent=agent,
    input=meeting_transcript,
    run_config=config
)

print("=== Meeting Minutes ===")
print(result.final_output)
```



