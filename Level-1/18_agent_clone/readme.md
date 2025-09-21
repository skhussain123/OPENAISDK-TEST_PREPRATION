

## Cloning/copying agents
Agent cloning OpenAI Agents SDK mein ek aisa process hai jismein aap ek existing agent ki copy banate hain aur uske kuch properties ko modify kar sakte hain, jabke original agent ki configuration wahi rehti hai. Ye clone() method se hota hai, jo ek naya agent instance return karta hai, jismein aap original agent ke base par changes kar sakte hain bina asal agent ko affect kiye.

* clone() method ek shallow copy banata hai, yani agent ki configuration (jaise name, instructions, model, tools, aur handoffs) copy hoti hai, lekin mutable cheezein (jaise tools ya handoffs ki list) share hoti hain jab tak aap nayi list na dein.
* Istemaal: Cloning se aap ek agent ke alag versions bana sakte hain, masalan different instructions ya model ke sath, testing ya specific tasks ke liye, bina original agent ko change kiye.

OpenAI Agents SDK mein clone() method shallow copy use karta hai. Yani agent ke mutable attributes (jaise tools ya handoffs ki lists) original aur cloned agent mein share hote hain.


```python
# Base agent
base_agent = Agent(
    name="BaseAssistant",
    instructions="You are a helpful assistant.",
)

# Clone with different instructions
creative_agent = base_agent.clone(
    name="CreativeAssistant",
    instructions="You are a creative writing assistant. Always respond with vivid, imaginative language.",
)
```

### Shallow Copy Behavior
```python
# Original agent with tools
original_agent = Agent(
    name="Original",
    tools=[calculator, weather_tool],
    instructions="You are helpful."
)

# Clone the agent
cloned_agent = original_agent.clone(
    name="Cloned",
    instructions="You are creative."
)

# What happens:
# ✅ New agent object created
# ✅ New name and instructions
# ✅ Same tools list (shared reference)
# ✅ Same model settings (unless overridden)
```
#### Kya cheezein clone me change ho sakti hain:
1. name
2. instructions
3. model
4. tools (agar agent kisi tool set ke saath bana hai to tool set badal sakte ho)
5. model_settings (tool_choice, streaming settings, etc.


### Understanding Shared References
```python
# Tools are shared between original and clone
original_agent.tools.append(new_tool)
# This affects both original_agent AND cloned_agent!

# To avoid this, pass new tools list:
independent_clone = original_agent.clone(
    name="Independent",
    tools=[calculator, weather_tool, new_tool]  # New list
)
```

## 1. Basic Cloning
```python
# Base agent
base_agent = Agent(
    name="BaseAssistant",
    instructions="You are a helpful assistant.",
)

# Simple clone
friendly_agent = base_agent.clone(
    name="FriendlyAssistant",
    instructions="You are a very friendly and warm assistant."
)

query = "Hello, how are you?"

result_base = Runner.run_sync(base_agent, query, run_config=config)
result_friendly = Runner.run_sync(friendly_agent, query, run_config=config)

print("Base Agent:", result_base.final_output)
print("Friendly Agent:", result_friendly.final_output)
```

```python
    def clone(self, **kwargs: Any) -> Agent[TContext]:
        """Make a copy of the agent, with the given arguments changed.
        Notes:
            - Uses `dataclasses.replace`, which performs a **shallow copy**.
            - Mutable attributes like `tools` and `handoffs` are shallow-copied:
              new list objects are created only if overridden, but their contents
              (tool functions and handoff objects) are shared with the original.
            - To modify these independently, pass new lists when calling `clone()`.
        Example:
            ```python
            new_agent = agent.clone(instructions="New instructions")
            ```
        """
        return dataclasses.replace(self, **kwargs)
```        

## 2. Tools and handoff Example
```python
@function_tool
def weather_checker(input: str) -> str:
    return f"weather = {input} is suuny"


Mathagent = Agent(
    name="Math agent",
    tools=[weather_checker],
    instructions="You are helpful math assistant",
)


# Original agent with tools
original_agent = Agent(
    name="Original",
    tools=[weather_checker],
    instructions="You are helpful. if user asked weather related question you want to use weather_checker tool",
    handoffs=[
        Mathagent
    ]
)

# Clone the agent
cloned_agent = original_agent.clone(
    name="Cloned",
    instructions="You are helpful.you can use weather_tool and calculator base on user query."
)

result = Runner.run_sync(cloned_agent, input="what is the weather in karachi",run_config=config)
print(result.final_output)
print(result.last_agent)
```
- cloned_agent ke pass original agent ke tools, handoff, name, instructions, model settings, tool behaviour ayengy.









<!-- 
## 3. Cloning with Different Tools
```python
@function_tool
def calculate_area(length: float, width: float) -> str:
    return f"Area = {length * width} square units"


@function_tool
def get_weather(city: str) -> str:
    return f"Weather in {city}: Sunny, 72°F"


# Base agent with one tool
base_agent = Agent(
    name="BaseAssistant",
    tools=[calculate_area],
    instructions="You are a helpful assistant."
)

# Clone with additional tool
weather_agent = base_agent.clone(
    name="WeatherAssistant",
    tools=[calculate_area, get_weather],  # New tools list
    instructions="You are a weather and math assistant."
)

# Clone with different tools
math_agent = base_agent.clone(
    name="MathAssistant",
    tools=[calculate_area],  # Same tools
    instructions="You are a math specialist."
)

query = "Hello, how are you?"

math_base = Runner.run_sync(math_agent, query, run_config=config)
result_weather = Runner.run_sync(weather_agent, query, run_config=config)

print("Math Agent:", math_base.final_output)
print("Weather Agent:", result_weather.final_output)
```

---

# Advanced Examples

### 1. Multiple Clones from One Base
```python
# Create a base agent
base_agent = Agent(
    name="BaseAssistant",
    instructions="You are a helpful assistant.",
)

# Create multiple specialized variants
agents = {
    "Creative": base_agent.clone(
        name="CreativeWriter",
        instructions="You are a creative writer. Use vivid language.",
    ),
    "Precise": base_agent.clone(
        name="PreciseAssistant", 
        instructions="You are a precise assistant. Be accurate and concise.",
    ),
    "Friendly": base_agent.clone(
        name="FriendlyAssistant",
        instructions="You are a very friendly assistant. Be warm and encouraging."
    ),
    "Professional": base_agent.clone(
        name="ProfessionalAssistant",
        instructions="You are a professional assistant. Be formal and business-like."
    )
}

# Test all variants
query = "Tell me about artificial intelligence."

for name, agent in agents.items():
    result = Runner.run_sync(agent, query, run_config=config)
    print(f"\n{name} Agent:")
    print(result.final_output[:100] + "...")
```

#### Shallow Copy Behavior
| What's Copied | What's Shared | What's Independent |
|---------------|----------------|-------------------|
| **Agent object** | ✅ New object | ✅ Independent |
| **Name** | ✅ New value | ✅ Independent |
| **Instructions** | ✅ New value | ✅ Independent |
| **Model settings** | ✅ New object | ✅ Independent |
| **Tools list** | ❌ Shared reference | ⚠️ Careful! |
| **Handoffs** | ❌ Shared reference | ⚠️ Careful! |


#### Best Practices
```python
# ✅ Good: Pass new lists for mutable objects
independent_clone = base_agent.clone(
    name="Independent",
    tools=[tool1, tool2, tool3],  # New list
    handoffs=[handoff1, handoff2]  # New list
)

# ❌ Risky: Rely on shared references
shared_clone = base_agent.clone(
    name="Shared",
    # tools and handoffs are shared with original!
)
```

### Understand Shared References
```python
# Create base agent with tools
@function_tool
def tool1() -> str:
    return "Tool 1"

@function_tool  
def tool2() -> str:
    return "Tool 2"

base_agent = Agent(
    name="Base",
    tools=[tool1],
    instructions="You are helpful."
)

# Create clones
shared_clone = base_agent.clone(name="Shared")
independent_clone = base_agent.clone(
    name="Independent",
    tools=[tool1, tool2]  # New list
)

# Modify original
@function_tool
def tool3() -> str:
    return "Tool 3"

base_agent.tools.append(tool3)

# Check what happened
print("Base tools:", len(base_agent.tools))           # 2
print("Shared clone tools:", len(shared_clone.tools)) # 2 (shared!)
print("Independent clone tools:", len(independent_clone.tools)) # 2 (independent!)
```
* Agar aap chahte hain ke cloned agent ke tools ya handoffs independent hon, to hamesha nayi list provide karen:

```python
independent_clone = base_agent.clone(
    name="Independent",
    tools=[tool1, tool2, tool3],  # Nayi list
    handoffs=[handoff1, handoff2]  # Nayi list
)
```

* Shared References se Bacho: Agar aap tools ya handoffs ko explicitly nahi dete, to shared references ke wajah se unexpected changes ho sakte hain:
```python
shared_clone = base_agent.clone(name="Shared")  # Risky: tools aur handoffs shared hain
```












 -->
