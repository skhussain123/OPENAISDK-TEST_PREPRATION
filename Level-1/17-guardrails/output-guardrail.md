

### Ouput guardrails Code (Agent ke under output_guardrails pr click kro)

* OuputGuardrail me bydeafault empty list hoti ha. (ye empty list create kryga--> field(default_factory=list))
```bash
output_guardrails: list[OutputGuardrail[TContext]] = field(default_factory=list)
```

* @output_guardrail decorator pr Click kro ye methods OutputGuardrail return kr raha ha..
```bash
@overload
def output_guardrail(
    func: _OutputGuardrailFuncSync[TContext_co],
) -> OutputGuardrail[TContext_co]: ...
```

* Guardrail ko craete krny ke liye ye structure fllow krna hoga (click @input_guardrail decorator and click InputGuardrail you will see
```bash
guardrail_function: Callable[
        [RunContextWrapper[TContext], Agent[Any], Any],
        MaybeAwaitable[GuardrailFunctionOutput],
    ]
    """A function that receives the final agent, its output, and the context, and returns a
     `GuardrailResult`. The result marks whether the tripwire was triggered, and can optionally
     include information about the guardrail's output.
    """
```

* 
```bash
@output_guardrail
async def weather_check(ctx: RunContextWrapper, agent:Agent,output:Any) -> GuardrailFunctionOutput:

    return GuardrailFunctionOutput(
        output_info=""
        tripwire_triggered=""
    )

myagent =  Agent(
    name="assistance",
    instructions='you are a helpfull Assistance',
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    output_guardrails=[weather_check]
)
```
##### Create
* humny eik input_guardrail create kia ha structure ke according
```bash
@output_guardrail
async def weather_check(ctx: RunContextWrapper, agent:Agent,output:Any) -> GuardrailFunctionOutput:

    return GuardrailFunctionOutput()
```

* return jo ho raha ha GuardrailFunctionOutput() 
* ye function ha jo 2 perameters le raha ha
```bash
class GuardrailFunctionOutput(
    output_info: Any,
    tripwire_triggered: bool
)
```
**OutputGuardrail Class me (Jaha Guardrail create waha Structure mojjod ha)**
* waha eik run ka function ha jo guardrail jo run kryga or InputGuardrailResult ki class return kryga us Class ka structure
```bash
 async def run(
        self, context: RunContextWrapper[TContext], agent: Agent[Any], agent_output: Any
    ) -> OutputGuardrailResult:
        if not callable(self.guardrail_function):
            raise UserError(f"Guardrail function must be callable, got {self.guardrail_function}")

        output = self.guardrail_function(context, agent, agent_output)
        if inspect.isawaitable(output):
            return OutputGuardrailResult(
                guardrail=self,
                agent=agent,
                agent_output=agent_output,
                output=await output,
            )

        return OutputGuardrailResult(
            guardrail=self,
            agent=agent,
            agent_output=agent_output,
            output=output,
        )
```   
* run function call krty wqt agent,input or context required ha pass krna.

---

#### code Output Guardrail With Exception Handling
```bash
import asyncio
import os
from agents import (
    Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel, output_guardrail, GuardrailFunctionOutput,
    RunContextWrapper, OutputGuardrailTripwireTriggered,enable_verbose_stdout_logging
)
from dotenv import load_dotenv
from pydantic import BaseModel,Field
from typing import Any


load_dotenv()
enable_verbose_stdout_logging()

gemini_api_key = os.getenv('GEMINI_API_KEY')

if not gemini_api_key:
    raise ValueError("API key is not loaded")


external_client = AsyncOpenAI(
    api_key=gemini_api_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

class weather_check_type(BaseModel):
    is_check_weather: bool = Field(description="if your is acking anything about weather discussion the True in this field")
    

guardrail_agent =  Agent(
    name="guardrail_agent",
    instructions='you check if the user is acking about weather or not',
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    output_type=weather_check_type
)

@output_guardrail
async def weather_check(ctx: RunContextWrapper, agent:Agent, output:Any) -> GuardrailFunctionOutput:
    
    guardrail_result = await Runner.run(starting_agent= guardrail_agent, input= output, context=Any)
    
    return GuardrailFunctionOutput(
        output_info=guardrail_result.final_output,
        tripwire_triggered=guardrail_result.final_output.is_check_weather # Ture / False
    )

myagent =  Agent(
    name="assistance",
    instructions='you are a helpfull Assistance',
    model=OpenAIChatCompletionsModel(model='gemini-2.0-flash',openai_client=external_client),
    output_guardrails=[weather_check]
)
 
async def main():
  
    try:
        result = await Runner.run(starting_agent=myagent, input="what is the weather in karachi")
        print(result.final_output)
        
    except OutputGuardrailTripwireTriggered as e:
        print(e)    
        
asyncio.run(main())
```
* jasy tripwire_triggered True hoga to OutputGuardrailTripwireTriggered ki class sy (Guardrail OutputGuardrail triggered tripwire) ka error ayega
* TResponseInputItem ka mtlb ha input is format he ho sakta ha
```bash
user = {"role" : "user" , "content" : "hi how are you"}
```






