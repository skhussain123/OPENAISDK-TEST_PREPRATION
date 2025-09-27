
# Structured Output with Pydantic
Structured outputs are crucial when you need your AI agents to provide data in a predictable and usable format. Instead of free-form text, you can enforce a specific structure, making it easier for your applications to parse and utilize the information. The OpenAI Agents SDK provides mechanisms to achieve this

--- 
The type of the output object. If not provided, the output will be str. In most cases, you should pass a regular Python type (e.g. a dataclass, Pydantic model, TypedDict, etc). You can customize this in two ways:

#### Take Perameters
```bash
output_type: type[Any] | AgentOutputSchemaBase | None = None,
```
1. If you want non-strict schemas, pass `AgentOutputSchema(MyClass, strict_json_schema=False)`.
2. If you want to use a custom JSON schema (i.e. without using the SDK's automatic schema)
creation, subclass and pass an `AgentOutputSchemaBase` subclass.


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


## Non-Strict Schema (Flexible Validation)
```python
from agents import Agent, Runner, OpenAIChatCompletionsModel, AsyncOpenAI, AgentOutputSchema
from dotenv import load_dotenv
from agents.run import RunConfig
import os
from pydantic import BaseModel

load_dotenv()

gemini_api_key = os.getenv('GEMINI_API_KEY')

if not gemini_api_key:
    raise ValueError("API key is not loaded")

# External client setup
external_client = AsyncOpenAI(
    api_key=gemini_api_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

# Model setup
model = OpenAIChatCompletionsModel(
    model="gemini-2.0-flash",
    openai_client=external_client
)

# Run configuration
config = RunConfig(
    model=model,
    model_provider=external_client,
    tracing_disabled=True
)

# Pydantic model for structured output
class UserInfo(BaseModel):
    name: str
    age: int


# Non-strict schema so thoda flexible rahega
output_schema = AgentOutputSchema(UserInfo, strict_json_schema=False)

# Agent setup
triage_agent = Agent(
    name="Triage Agent",
    instructions="Agar user escalation ka reason bataye, to escalate karo.",
    output_type=output_schema
)

# Runner
result = Runner.run_sync(
    starting_agent=triage_agent,
    input="user name hussain and age 22",
    run_config=config
)

print("Final Output:", result.final_output)
```

### Schema Strictness / non-strict JSON schema
```python
import os
from typing import Any
from agents import Agent, RunContextWrapper, Runner, OpenAIChatCompletionsModel,AsyncOpenAI, function_tool,AgentOutputSchema
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

# --- 1. Define a schema for output -- using Pydantic model ---
class PersonInfo(BaseModel):
    name: str
    age: int

# --- 2. Tool to provide info, if needed ---
@function_tool
def get_person_info(wrapper: RunContextWrapper[None]) -> PersonInfo:
    # Just a dummy— return a PersonInfo object
    return PersonInfo(name="Hussain", age=22)

# --- 3a. Agent with strict JSON schema output_type ---
agent_strict = Agent[None](
    name="AgentStrict",
    instructions="Return a PersonInfo as JSON",
    tools=[get_person_info],
    output_type=AgentOutputSchema(PersonInfo, strict_json_schema=True)
)

# --- 3b. Agent with non-strict JSON schema (strict off) ---
agent_non_strict = Agent[None](
    name="AgentNonStrict",
    instructions="Return a PersonInfo as JSON",
    tools=[get_person_info],
    output_type=AgentOutputSchema(PersonInfo, strict_json_schema=False)
)

# --- 4. Run both agents and see output ---
def run_examples():
    result_strict = Runner.run_sync(starting_agent=agent_strict, input="Who is the person?", context=None)
    print("Strict agent final:", result_strict.final_output)
    
    result_non = Runner.run_sync(starting_agent=agent_non_strict, input="Who is the person?", context=None)
    print("Non-strict agent final:", result_non.final_output)

if __name__ == "__main__":
    run_examples()
```

### Example 1 (default Pydantic-based schema)
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


### Using Dataclasses as output_type in Agents
```python
from pydantic.dataclasses import dataclass

@dataclass
class UserInfo:
    name: str
    age: int
    
    
# Agent setup
triage_agent = Agent(
    name="Triage Agent",
    instructions="Agar user escalation ka reason bataye, to escalate karo.",
    output_type=UserInfo
)

# Runner
result = Runner.run_sync(
    starting_agent=triage_agent,
     input="My name is Hussain and I am 22 years old",
    run_config=config
)
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

### 4. Meeting Minutes Extractor
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

### 5. Different Data Types
```python
from typing import Optional, List
from datetime import datetime

class ProductInfo(BaseModel):
    name: str                           # Text
    price: float                        # Decimal number
    in_stock: bool                      # True/False
    categories: List[str]               # List of text items
    discount_percent: Optional[int] = 0 # Optional number, default 0
    reviews_count: int                  # Whole number

# Create product info extractor
agent = Agent(
    name="ProductExtractor",
    instructions="Extract product information from product descriptions.",
    output_type=ProductInfo
)

# Test with product description
result = Runner.run_sync(
    agent,
    "The iPhone 15 Pro costs $999.99, it's available in electronics and smartphones categories, currently in stock with 1,247 reviews."
)

print("Product:", result.final_output.name)         # "iPhone 15 Pro"
print("Price:", result.final_output.price)          # 999.99
print("In Stock:", result.final_output.in_stock)    # True
print("Categories:", result.final_output.categories) # ["electronics", "smartphones"]
print("Reviews:", result.final_output.reviews_count) # 1247
```

## Exercise 1: Build a Resume Parser
```python
from typing import List, Optional

class Education(BaseModel):
    degree: str
    institution: str
    graduation_year: int
    gpa: Optional[float] = None

class Experience(BaseModel):
    position: str
    company: str
    start_year: int
    end_year: Optional[int] = None  # None if current job
    responsibilities: List[str]

class Resume(BaseModel):
    full_name: str
    email: str
    phone: str
    summary: str
    education: List[Education]
    experience: List[Experience]
    skills: List[str]
    languages: List[str]

# Create resume parser
resume_parser = Agent(
    name="ResumeParser",
    instructions="Extract structured information from resume text.",
    output_type=Resume
)

# Test with sample resume
sample_resume = """
John Smith
Email: john.smith@email.com, Phone: (555) 123-4567

Professional Summary:
Experienced software developer with 5 years in web development and team leadership.

Education:
- Bachelor of Computer Science, MIT, 2018, GPA: 3.8
- Master of Software Engineering, Stanford, 2020

Experience:
- Senior Developer at Google (2020-present): Led team of 5 developers, implemented microservices architecture
- Junior Developer at Startup Inc (2018-2020): Built React applications, maintained CI/CD pipelines

Skills: Python, JavaScript, React, Docker, Kubernetes
Languages: English (native), Spanish (conversational), French (basic)
"""

result = Runner.run_sync(resume_parser, sample_resume)

print("=== Parsed Resume ===")
print(f"Name: {result.final_output.full_name}")
print(f"Email: {result.final_output.email}")
print(f"Phone: {result.final_output.phone}")
print(f"Summary: {result.final_output.summary}")

print("\nEducation:")
for edu in result.final_output.education:
    gpa_str = f", GPA: {edu.gpa}" if edu.gpa else ""
    print(f"  • {edu.degree} from {edu.institution} ({edu.graduation_year}){gpa_str}")

print("\nExperience:")
for exp in result.final_output.experience:
    end_year = exp.end_year if exp.end_year else "present"
    print(f"  • {exp.position} at {exp.company} ({exp.start_year}-{end_year})")
    for resp in exp.responsibilities:
        print(f"    - {resp}")

print(f"\nSkills: {', '.join(result.final_output.skills)}")
print(f"Languages: {', '.join(result.final_output.languages)}")
```

## Exercise 2: Create a Recipe Analyzer
```python
from typing import List, Optional

class Ingredient(BaseModel):
    name: str
    amount: str
    unit: str
    notes: Optional[str] = None

class NutritionInfo(BaseModel):
    calories_per_serving: Optional[int] = None
    prep_time_minutes: int
    cook_time_minutes: int
    difficulty_level: str = Field(..., regex=r'^(easy|medium|hard)$')

class Recipe(BaseModel):
    title: str
    description: str
    servings: int
    ingredients: List[Ingredient]
    instructions: List[str]
    nutrition: NutritionInfo
    cuisine_type: str
    dietary_tags: List[str]  # vegetarian, vegan, gluten-free, etc.

# Create recipe analyzer
recipe_analyzer = Agent(
    name="RecipeAnalyzer",
    instructions="Extract detailed recipe information from recipe text.",
    output_type=Recipe
)

# Test with recipe
recipe_text = """
Spaghetti Carbonara
A classic Italian pasta dish with eggs, cheese, and pancetta.
Serves 4 people. Prep time: 15 minutes, Cook time: 20 minutes. Medium difficulty.

Ingredients:
- 400g spaghetti pasta
- 150g pancetta, diced
- 3 large eggs
- 100g Parmesan cheese, grated
- 2 cloves garlic, minced
- Black pepper to taste
- Salt for pasta water

Instructions:
1. Boil salted water and cook spaghetti according to package directions
2. Fry pancetta in a large pan until crispy
3. Beat eggs with Parmesan cheese in a bowl
4. Drain pasta and add to pancetta pan
5. Remove from heat and quickly mix in egg mixture
6. Serve immediately with extra Parmesan

Cuisine: Italian
Dietary notes: Contains gluten, dairy, and eggs
Approximate calories: 650 per serving
"""

result = Runner.run_sync(recipe_analyzer, recipe_text)

print("=== Recipe Analysis ===")
print(f"Title: {result.final_output.title}")
print(f"Description: {result.final_output.description}")
print(f"Servings: {result.final_output.servings}")
print(f"Cuisine: {result.final_output.cuisine_type}")
print(f"Difficulty: {result.final_output.nutrition.difficulty_level}")
print(f"Total Time: {result.final_output.nutrition.prep_time_minutes + result.final_output.nutrition.cook_time_minutes} minutes")

print("\nIngredients:")
for ing in result.final_output.ingredients:
    notes_str = f" ({ing.notes})" if ing.notes else ""
    print(f"  • {ing.amount} {ing.unit} {ing.name}{notes_str}")

print("\nInstructions:")
for i, step in enumerate(result.final_output.instructions, 1):
    print(f"  {i}. {step}")

print(f"\nDietary Tags: {', '.join(result.final_output.dietary_tags)}")
if result.final_output.nutrition.calories_per_serving:
    print(f"Calories per serving: {result.final_output.nutrition.calories_per_serving}")
```


