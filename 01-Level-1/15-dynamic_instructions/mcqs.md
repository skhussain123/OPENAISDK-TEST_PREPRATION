
1. What is the purpose of the `instructions` parameter in the OpenAI SDK Agent?
   - A) To define the agent's name
   - B) To provide a system prompt or dynamically generate one
   - C) To configure the agent's tools
   - D) To store conversation history
   - **Correct Answer**: B

2. What types of values can the `instructions` parameter accept?
   - A) Only strings
   - B) Strings or functions that return strings
   - C) Only async functions
   - D) Only sync functions
   - **Correct Answer**: B

3. What parameters must a dynamic instructions function accept?
   - A) Only the agent
   - B) Only the context
   - C) Both RunContextWrapper and Agent
   - D) Neither is required
   - **Correct Answer**: C

4. What type of function can be used for dynamic instructions?
   - A) Only synchronous functions
   - B) Only asynchronous functions
   - C) Both synchronous and asynchronous functions
   - D) Only class-based functions
   - **Correct Answer**: C

5. In the example `dynamic_instructure(ctx: RunContextWrapper, agent: Agent) -> str`, what does the function return?
   - A) A dictionary
   - B) A string
   - C) An integer
   - D) A boolean
   - **Correct Answer**: B

6. How can you access the agent's name in a dynamic instructions function?
   - A) `ctx.name`
   - B) `agent.name`
   - C) `context.agent_name`
   - D) `RunContextWrapper.name`
   - **Correct Answer**: B

7. What is the purpose of the `RunContextWrapper` in dynamic instructions?
   - A) To store the agent's tools
   - B) To provide conversation history, user data, and run state
   - C) To define the agent's model
   - D) To manage API keys
   - **Correct Answer**: B

8. In the async example with `dynamic_instructure`, what is used to access the context data?
   - A) `ctx.context`
   - B) `agent.context`
   - C) `RunContextWrapper.data`
   - D) `context.user_data`
   - **Correct Answer**: A

9. What does the `StatefulInstructions` class in the example do?
   - A) Resets the interaction count
   - B) Tracks the number of interactions and adjusts instructions
   - C) Generates random instructions
   - D) Disables dynamic instructions
   - **Correct Answer**: B

10. What is included in the `context` parameter of a dynamic instructions function?
    - A) Only user data
    - B) Messages, user data, run state, and metadata
    - C) Only conversation history
    - D) Only metadata
    - **Correct Answer**: B

11. What is the role of `Runner.run_sync` in the provided examples?
    - A) To define the agent's model
    - B) To execute the agent with the given input and configuration
    - C) To create a new agent
    - D) To validate the context
    - **Correct Answer**: B

12. In the Pydantic example, how is the user name accessed in the instructions?
    - A) `ctx.user_name`
    - B) `ctx.context.user_name`
    - C) `agent.user_name`
    - D) `context.name`
    - **Correct Answer**: B

13. What is the purpose of the `agent.tools` property in the `explore_agent` example?
    - A) To store user data
    - B) To access the list of tools available to the agent
    - C) To define the agent's name
    - D) To manage run configuration
    - **Correct Answer**: B

14. What happens if the `instructions` parameter is set to `None`?
    - A) The agent uses a default prompt
    - B) The agent fails to initialize
    - C) The agent ignores the context
    - D) The agent uses the last instruction
    - **Correct Answer**: A

15. In the `StatefulInstructions` example, what happens after the third interaction?
    - A) The instructions reset
    - B) The instructions become more efficient
    - C) The agent stops responding
    - D) The interaction count resets
    - **Correct Answer**: B

16. What is the benefit of using dynamic instructions over a static string?
    - A) They are faster to execute
    - B) They allow for context-aware and adaptive prompts
    - C) They reduce memory usage
    - D) They simplify the agent's configuration
    - **Correct Answer**: B

17. Which of the following is NOT a component of the `agent` parameter in dynamic instructions?
    - A) Name
    - B) Tools
    - C) Settings
    - D) User input
    - **Correct Answer**: D