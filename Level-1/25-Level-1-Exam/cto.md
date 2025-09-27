

```python
import os
from agents import Agent, Runner, OpenAIChatCompletionsModel,AsyncOpenAI,ModelSettings, function_tool
from agents.run import RunConfig
from dotenv import load_dotenv
from agents.extensions.handoff_prompt import RECOMMENDED_PROMPT_PREFIX

load_dotenv()

gemini_key = os.getenv('GEMINI_API_KEY')


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

@function_tool
def weather_check(input:str) -> str:
    return f"the weather {input} is sunny"


python_agent = Agent(
    name="Python_Assistant",
    instructions="You are a help full python assistant"
)

nextjs_agent = Agent(
    name="nextjs_Assistant",
    instructions="You are a help full nextjs assistant"
)

manager = Agent(
    name="Assistance",
    instructions=RECOMMENDED_PROMPT_PREFIX + """
You are a manager. Read the user's question(s) and decide whether to answer or hand off.
- If about Python, invoke the handoff tool for python_assistant (transfer_to_python_assistant).
- If about Next.js, invoke the handoff tool for nextjs_assistant.
- If multiple independent questions are present, invoke each relevant handoff in order.
Think step by step before choosing.
""",
    handoffs=[python_agent, nextjs_agent] 
)

# Run (sync)
result = Runner.run_sync(manager, "what is python? what is Nextjs", run_config=config)
print(result.final_output)
```

