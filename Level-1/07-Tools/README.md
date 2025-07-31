
### Tools
Tools let agents take actions: things like fetching data, running code, calling external APIs, and even using a computer. There are three classes of tools in the Agent SDK:

* Hosted tools: these run on LLM servers alongside the AI models. OpenAI offers retrieval, web search and computer use as hosted tools.
* Function calling: these allow you to use any Python function as a tool.
* Agents as tools: this allows you to use an agent as a tool, allowing Agents to call other agents without handing off to them.


### Hosted tools
1. The WebSearchTool lets an agent search the web.
2. The FileSearchTool allows retrieving information from your OpenAI Vector Stores.
3. The ComputerTool allows automating computer use tasks.
4. The CodeInterpreterTool lets the LLM execute code in a sandboxed environment.
5. The HostedMCPTool exposes a remote MCP server's tools to the model.
6. The ImageGenerationTool generates images from a prompt.
7. The LocalShellTool runs shell commands on your machine.


### Tools Class
```bash
(variable) tools: list[FunctionTool | FileSearchTool | WebSearchTool | ComputerTool | HostedMCPTool | LocalShellTool | ImageGenerationTool | CodeInterpreterTool]
```

### Function tools / Function calling
You can use any Python function as a tool. The Agents SDK will setup the tool automatically:

* The name of the tool will be the name of the Python function (or you can provide a name)
* Tool description will be taken from the docstring of the function (or you can provide a description)
* The schema for the function inputs is automatically created from the function's arguments
* Descriptions for each input are taken from the docstring of the function, unless disabled

```bash
@function_tool
def javascript(topic: str) -> str:
    "Explains a JavaScript topic in simple terms."
    return f"You asked about JavaScript topic: {topic}. Here's a basic explanation..."


agent = Agent(
    name="You are helpful assistant",
    instructions=("You are a helpful assistant for programming."),
    model=model,
    tools=[javascript],
)
```

* agr me tool me doc string nh dunga to tool me jab bhi proper work kryga.

#### async Tool
```bash
@function_tool
async def get_weather(city: str) -> str:
    return f"The weather in {city} is sunny."
```   

##### @function_tool Class
```bash
(function)
def function_tool(
    func: ToolFunction[...],
    *,
    name_override: str | None = None,
    description_override: str | None = None,
    docstring_style: DocstringStyle | None = None,
    use_docstring_info: bool = True,
    failure_error_function: ToolErrorFunction | None = None,
    strict_mode: bool = True,
    is_enabled: bool | ((RunContextWrapper[Any], Agent[Any]) -> MaybeAwaitable[bool]) = True
) -> FunctionTool: ...

def function_tool(
    *,
    name_override: str | None = None,
    description_override: str | None = None,
    docstring_style: DocstringStyle | None = None,
    use_docstring_info: bool = True,
    failure_error_function: ToolErrorFunction | None = None,
    strict_mode: bool = True,
    is_enabled: bool | ((RunContextWrapper[Any], Agent[Any]) -> MaybeAwaitable[bool]) = True
) -> ((ToolFunction[...]) -> FunctionTool): ...
```

## Agent as a Tool
```bash

# Define a support agent
poetry_agent = Agent(
    name="Poetry Writer Agent",
    instructions="Write a 3-stanza English poem on the given topic.",
    model=model
)

# Convert agents into tools
poetry_tool = poetry_agent.as_tool(
    tool_name="english_poetry_writer_tool",
    tool_description="Writes English poetry on the given topic."
)

triage_agent = Agent(
    name="Triage Agent",
    instructions="""
You are a smart assistant.
1. If the user asks for a poem or poetry, use 'english_poetry_writer_tool'.
2. Otherwise, use 'english_essay_writer_tool'.
Never write content yourself. Always call the right tool.
""",
    tools=[poetry_tool],
    model=model
)
```

### as_tools() Class
```bash
(method) def as_tool(
    tool_name: str | None,
    tool_description: str | None,
    custom_output_extractor: ((RunResult) -> Awaitable[str]) | None = None
) -> Tool
```

#### Customizing tool-agents
```bash
from agents import Agent, Runner, function_tool

@function_tool
async def run_my_agent(input: str) -> str:
    """Runs a sub-agent with custom config and input."""

    agent = Agent(
        name="My Agent",
        instructions="You help users by translating text to French."
    )

    result = await Runner.run(
        agent,
        input=input,
        max_turns=5 # max_turns = 5 ka matlab hai ke agent sirf 5 dafa LLM call karega ya tools use karega jab tak final output produce ho.
    )

    return str(result.final_output)
```    




