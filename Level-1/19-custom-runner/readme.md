


# Custom Runner
Openai sdk me runner ki class me run, runsync,runstreamed ke methods hoty hain. jinka behaviour ko hum custom class bana 
kr waha chnage kr sakty hain.

Runner pr Click kro to mujhe waha 2 classes milti ha Runner, AgentRunner dono classes me run medthod hota ha jo same paeramters
lety hain.


```bash
import asyncio
import os
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel,set_tracing_disabled,RunContextWrapper,function_tool
from dotenv import load_dotenv
from pydantic import BaseModel
import rich


# Load API key
load_dotenv()
set_tracing_disabled(disabled=True)


gemini_api_key = os.getenv('GEMINI_API_KEY')
if not gemini_api_key:
    raise ValueError("API key is not loaded")

external_client = AsyncOpenAI(
    api_key=gemini_api_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)


myagent =  Agent(
    name="assistance",
    instructions='you are a helpfull Assistance',
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
)

query =  "how are you"

async def main():
    result = await Runner.run(starting_agent=myagent, input=query)
    rich.print(result)

asyncio.run(main())
```
* Run Humny RunResult ki class return krtaa hain. 
* Runner or AgentRunner ki Class RunResult return krty hai.
* jismy hum kisi ki property ko dot dot laga kr access kr sakty hain. jasy is tarha

```bash
    rich.print(result.raw_responses[0].output[0].content[0].text) # yaha runResult sy text ko nikala gaya to final_out me same response ata hain
```

```bash
RunResult(
    input='how are you',
    new_items=[
        MessageOutputItem(
            agent=Agent(
                name='assistance',       
                handoff_description=None,
                tools=[],
                mcp_servers=[],
                mcp_config={},
                instructions='you are a helpfull Assistance',
                prompt=None,
                handoffs=[],
                model=<agents.models.openai_chatcompletions.OpenAIChatCompletionsModel object at 0x000002126B77DED0>,                model_settings=ModelSettings(
                    temperature=None,
                    top_p=None,
                    frequency_penalty=None,
                    presence_penalty=None,
                    tool_choice=None,
                    parallel_tool_calls=None,
                    truncation=None,
                    max_tokens=None,
                    reasoning=None,
                    verbosity=None,
                    metadata=None,
                    store=None,
                    include_usage=None,
                    response_include=None,
                    top_logprobs=None,
                    extra_query=None,
                    extra_body=None,
                    extra_headers=None,
                    extra_args=None
                ),
                input_guardrails=[],
                output_guardrails=[],
                output_type=None,
                hooks=None,
                tool_use_behavior='run_llm_again',
                reset_tool_choice=True
            ),
            raw_item=ResponseOutputMessage(
                id='__fake_id__',
                content=[
                    ResponseOutputText(
                        annotations=[],
                        text='I am doing well, thank you for asking! How can I help you today?\n',
                        type='output_text',
                        logprobs=None
                    )
                ],
                role='assistant',
                status='completed',
                type='message'
            ),
            type='message_output_item'
        )
    ],
    raw_responses=[
        ModelResponse(
            output=[
                ResponseOutputMessage(
                    id='__fake_id__',
                    content=[
                        ResponseOutputText(
                            annotations=[],
                            text='I am doing well, thank you for asking! How can I help you today?\n',
                            type='output_text',
                            logprobs=None
                        )
                    ],
                    role='assistant',
                    status='completed',
                    type='message'
                )
            ],
            usage=Usage(
                requests=1,
                input_tokens=9,
                input_tokens_details=InputTokensDetails(cached_tokens=0),
                output_tokens=18,
                output_tokens_details=OutputTokensDetails(reasoning_tokens=0),
                total_tokens=27
            ),
            response_id=None
        )
    ],
    final_output='I am doing well, thank you for asking! How can I help you today?\n',
    input_guardrail_results=[],
    output_guardrail_results=[],
    context_wrapper=RunContextWrapper(
        context=None,
        usage=Usage(
            requests=1,
            input_tokens=9,
            input_tokens_details=InputTokensDetails(cached_tokens=0),
            output_tokens=18,
            output_tokens_details=OutputTokensDetails(reasoning_tokens=0),
            total_tokens=27
        )
    ),
    _last_agent=Agent(
        name='assistance',
        handoff_description=None,
        tools=[],
        mcp_servers=[],
        mcp_config={},
        instructions='you are a helpfull Assistance',
        prompt=None,
        handoffs=[],
        model=<agents.models.openai_chatcompletions.OpenAIChatCompletionsModel object at 0x000002126B77DED0>,        
        model_settings=ModelSettings(
            temperature=None,
            top_p=None,
            frequency_penalty=None,
            presence_penalty=None,
            tool_choice=None,
            parallel_tool_calls=None,
            truncation=None,
            max_tokens=None,
            reasoning=None,
            verbosity=None,
            metadata=None,
            store=None,
            include_usage=None,
            response_include=None,
            top_logprobs=None,
            extra_query=None,
            extra_body=None,
            extra_headers=None,
            extra_args=None
        ),
        input_guardrails=[],
        output_guardrails=[],
        output_type=None,
        hooks=None,
        tool_use_behavior='run_llm_again',
        reset_tool_choice=True
    )
)
```

## Customization
```bash
from agents.run import AgentRunner, set_default_agent_runner

class MyCustomRunner(AgentRunner):
    async def run(self, starting_agent, input, **kwargs):
        
        print(f"CustomAgentRunner.run() - Infrastructure Layer") 
        result = await super().run(starting_agent,input,**kwargs) # super keyword ka use is liye kia ha taky meri MyCustomRunner ka run function nh chaly balky AgentRunner me mojjod run function chaly.

        # is Example ko samajny ke liye alag python Example nechy 1.1

        return result


set_default_agent_runner(MyCustomRunner())

myagent =  Agent(
    name="assistance",
    instructions='you are a helpfull Assistance',
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
)

query =  "how are you"

async def main():
    result = await Runner.run(starting_agent=myagent, input=query)
    rich.print(result.final_output)

asyncio.run(main())
```

### 1.1 Python Example
```bash
class AgentRunner():
    def run(self):
        return "Hello AgentRunner"
        

class MyCustomRunner(AgentRunner):
    def run(self):
        res = super().run()
        return res


result = MyCustomRunner()
print(result.run())        
```

### Code Explaination
MyCustomRunner ki class ko AgentRunner sy extend kia gaya ha taky AgentRunner ki property or ko access kia ja saky.