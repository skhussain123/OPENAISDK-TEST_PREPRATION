



### 1. @pydantic.dataclasses.dataclass vs BaseModel
| Feature               | `BaseModel`                                          | `@pydantic.dataclasses.dataclass`                                             |
| --------------------- | ---------------------------------------------------- | ----------------------------------------------------------------------------- |
| **Origin**            | Pydantic ka core model                               | Python `dataclass` ko Pydantic ke validation ke sath wrap karta hai           |
| **Validation**        | Har assignment aur init pe hoti hai                  | Init pe hoti hai (runtime assignment pe nahi hoti by default)                 |
| **Schema Generation** | Full JSON schema support deta hai (OpenAPI friendly) | JSON schema support deta hai but kuch advanced features limited ho sakti hain |
| **Usage**             | Jab strict schema + validation + docs chahiye ho     | Jab lightweight dataclass feel chahiye ho lekin validation bhi chahiye ho     |
| **Performance**       | Thoda zyada overhead (kyunke extra features hain)    | Thoda fast aur lightweight                                                    |

1. Only dataclass + strict validation + no validation + data parsing 
2. BaseModel → Full schema + strict validation + API-ready.
3. dataclass → Simpler structure + thodi flexible + Pythonic.

### 1. dataclass Example
```python

from dataclasses import dataclass

@dataclass
class UserInfo:
    id: int
    name: str
    
user = UserInfo(id="1011",name="Hussain")
print(user.id)
print(type(user.id))    

# OUTPUT:
# 1011
# <class 'str'>
```
* Not Data Validation (no check user id int or string)
* Not Data Parsing (string to int convert)

### 2. Example with Pydantic
```python
from pydantic import BaseModel

class UserInfo(BaseModel):
    id: int
    name: str
    
user = UserInfo(id="1011", name="Hussain")
print(user.id)
print(type(user.id))

# OUTPUT:
# 1011
# <class 'int'>
```

### 4. Example with @pydantic.dataclasses.dataclass
```python
from pydantic.dataclasses import dataclass

@dataclass
class UserInfo:
    id: int
    name: str
    
user = UserInfo(id="1011", name="Hussain")
print(user.id)
print(type(user.id))

# OUTPUT:
# 1011
# <class 'int'>
```

### 5. Using Dataclasses as output_type in Agents
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





