



### 1. @pydantic.dataclasses.dataclass vs BaseModel
| Feature               | `BaseModel`                                          | `@pydantic.dataclasses.dataclass`                                             |
| --------------------- | ---------------------------------------------------- | ----------------------------------------------------------------------------- |
| **Origin**            | Pydantic ka core model                               | Python `dataclass` ko Pydantic ke validation ke sath wrap karta hai           |
| **Validation**        | Har assignment aur init pe hoti hai                  | Init pe hoti hai (runtime assignment pe nahi hoti by default)                 |
| **Schema Generation** | Full JSON schema support deta hai (OpenAPI friendly) | JSON schema support deta hai but kuch advanced features limited ho sakti hain |
| **Usage**             | Jab strict schema + validation + docs chahiye ho     | Jab lightweight dataclass feel chahiye ho lekin validation bhi chahiye ho     |
| **Performance**       | Thoda zyada overhead (kyunke extra features hain)    | Thoda fast aur lightweight                                                    |

* BaseModel → Full schema + strict validation + API-ready.
* dataclass → Simpler structure + thodi flexible + Pythonic.


## 2. Type Hints for Validation and Schema Definition
Dono (BaseModel aur pydantic.dataclasses.dataclass) type hints ko use karte hain taake:

* Runtime validation ho
* Automatic JSON schema generate ho

#### Example with BaseModel:
```python
from pydantic import BaseModel

class User(BaseModel):
    name: str
    age: int
```

#### Example with Pydantic dataclass
```python
from pydantic.dataclasses import dataclass

@dataclass
class User:
    name: str
    age: int
```
* Dono ka output LLM ke agent schema ke liye JSON structure banata hai.


### 3. Using Dataclasses as output_type in Agents
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


## Example 1: Using BaseModel
```python
from agents import Agent, Runner
from pydantic import BaseModel
from agents.run import RunConfig

# ✅ Strict schema with BaseModel
class UserInfoModel(BaseModel):
    name: str
    age: int

triage_agent_model = Agent(
    name="Assistant with BaseModel",
    instructions="Extract user info from user input.",
    output_type=UserInfoModel
)

result_model = Runner.run_sync(
    starting_agent=triage_agent_model,
    input="Hi, my name is Hussain and I am 22 years old.",
    run_config=config
)

print("BaseModel Output:", result_model.final_output)
```
#### BaseModel Output:
* Strictly validated object
* Extra features like .dict() and .json() available
```python
name='Hussain' age=22
```

## Example 2: Using @pydantic.dataclasses.dataclass
```python
from pydantic.dataclasses import dataclass

# ✅ Lightweight dataclass schema
@dataclass
class UserInfoDataClass:
    name: str
    age: int

triage_agent_dataclass = Agent(
    name="Assistant with Dataclass",
    instructions="Extract user info from user input.",
    output_type=UserInfoDataClass
)

result_dataclass = Runner.run_sync(
    starting_agent=triage_agent_dataclass,
    input="Hello, I am Hussain and my age is 22.",
    run_config=config
)

print("Dataclass Output:", result_dataclass.final_output)
```
#### Dataclass Output:
* Python native dataclass instance
* Lighter but fewer helper methods

```python
UserInfoDataClass(name='Hussain', age=22)
```



