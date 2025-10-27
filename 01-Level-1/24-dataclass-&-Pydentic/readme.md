
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
---

#### @pydantic.dataclasses.dataclass vs BaseModel
BaseModel ek special class hai jo tum inherit karte ho. Ye tumhe full Pydantic power deta hai:
* Type validation + automatic conversion (string "101" ko int 101 bana dega).
* Methods jaise .dict(), .json(), .model_dump() ready-made milte hain.
* Zyada config options (strict mode, allow extra fields, etc.).
* API frameworks jaise FastAPI isko heavily use karte hain, kyunki request/response easily serialize ho jate hain


#### @pydantic.dataclasses.dataclass
Ye asal me ek Python dataclass hai, bas Pydantic ka wrapper lagta hai.
* Matlab tumhe Python ka dataclass style milta hai, lekin andar validation bhi hoti hai.
* Ye lightweight hai, itna heavy nahi jitna BaseModel.
* Serialization methods (.dict(), .json()) by default nahi hote, bas dataclasses.asdict() use karna padta hai.
* Agar tum sirf data store + validation chahte ho without full API features, to ye best hai.

1. BaseModel = Full Pydantic features, API/serialization ke liye best.
2. @dataclass = Pythonic style + validation, lekin simple aur lightweight.


