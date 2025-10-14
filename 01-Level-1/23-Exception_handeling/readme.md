### Some Exceptions
#### 1. ModelBehaviorError
* Bases: AgentsException <br>
* Jab LLM kuch unexpected kare — jaise malformed JSON output, ya tool call name jo exist na kare, ya output type mismatch — to ModelBehaviorError throw hoti hai. 
* Ye error indicate karti hai ke model ne kuch aisi cheez produce ki jo SDK expect nahin karta.


#### 2. UserError
- Bases: AgentsException <br>
* Jab SDK ka user (developer) kuch galat kar de — wrong configuration, invalid parameters, misuse of API — to UserError uthti hai.

#### 3. InputGuardrailTripwireTriggered
- Bases: AgentsException <br>
* InputGuardrailTripwireTriggered: agar input guardrail fails / violation

#### 4. OutputGuardrailTripwireTriggered
- Bases: AgentsException <br>
* OutputGuardrailTripwireTriggered: agar final output guardrail fails.

#### 5. MaxTurnsExceeded
* Ye exception tab uthti hai jab agent loop bahut zyada turns kar le — yaani max_turns limit cross ho jaati hai.

### How to Exception handling
* Aap try / except blocks use kar sakte ho jab aap Runner.run ya run_sync call karte ho. Aur based on exception type, alag behavior define kar sakte ho.
```python
from agents.exceptions import MaxTurnsExceeded, ModelBehaviorError, AgentsException

try:
    result = Runner.run_sync(starting_agent=myagent, input="some question", context=my_context)
    print("Final output:", result.final_output)
except MaxTurnsExceeded as e:
    print("Error: too many turns, giving best guess:", e)
    # fallback: maybe request final answer from last state
except ModelBehaviorError as e:
    print("Model misbehaved:", e)
    # fallback: fallback instructions, or simpler prompt
except AgentsException as e:
    # catch all agent SDK exceptions
    print("Agent error:", e)
    # maybe fallback or log details
except Exception as e:
    # other errors (network, etc.)
    print("Other error:", e)
```