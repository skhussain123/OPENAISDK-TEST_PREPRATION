
---

### General Context Management
1. What is the primary purpose of context management in the OpenAI Agents SDK?
   - A) To manage the agent's memory allocation
   - B) To handle additional data during an agent’s execution
   - C) To optimize the LLM’s response time
   - D) To store the agent’s model configuration
   - **Answer**: B

2. How many main forms of context are defined in the OpenAI Agents SDK?
   - A) One
   - B) Two
   - C) Three
   - D) Four
   - **Answer**: B

3. Which of the following is NOT a type of context in the OpenAI Agents SDK?
   - A) Local Context
   - B) Agent/LLM Context
   - C) Global Context
   - D) None of the above
   - **Answer**: C

### Local Context
4. What is Local Context in the OpenAI Agents SDK?
   - A) Data sent to the LLM to guide its responses
   - B) Data or dependencies passed to the agent’s run, used internally
   - C) The conversation history of the agent
   - D) External data fetched via web search
   - **Answer**: B

5. Local Context is primarily used for:
   - A) Guiding the LLM’s response generation
   - B) Backend logic and operations
   - C) Storing the agent’s model configuration
   - D) Managing API keys
   - **Answer**: B

6. Which of the following is NOT stored in Local Context?
   - A) User details like username or ID
   - B) Logger dependencies
   - C) Conversation history
   - D) Helper functions
   - **Answer**: C

7. How is Local Context passed to an agent in the OpenAI Agents SDK?
   - A) Through the `instructions` parameter
   - B) Via the `context` parameter in the `Runner.run()` method
   - C) By embedding it in the system prompt
   - D) Using the `tools` parameter
   - **Answer**: B

8. What wraps the Local Context object in the OpenAI Agents SDK?
   - A) `AgentWrapper`
   - B) `RunContextWrapper`
   - C) `ContextManager`
   - D) `LLMContext`
   - **Answer**: B

9. What ensures consistency in Local Context during a single agent run?
   - A) All parts of the run share the same type of context
   - B) The LLM validates the context
   - C) The context is sent to the LLM
   - D) The context is stored in a database
   - **Answer**: A

10. Which Python constructs are commonly used to create Local Context?
    - A) Lists and dictionaries
    - B) Dataclasses or Pydantic models
    - C) Strings and integers
    - D) Loops and conditionals
    - **Answer**: B

11. What happens to Local Context during an agent’s run?
    - A) It is sent to the LLM
    - B) It is accessible to tools, lifecycle hooks, and callbacks
    - C) It is stored in the conversation history
    - D) It is discarded after the run
    - **Answer**: B

12. In the provided code, what is the purpose of the `UserInfo` class?
    - A) To define the structure of Local Context
    - B) To store the LLM’s conversation history
    - C) To configure the agent’s model
    - D) To fetch external data
    - **Answer**: A

13. In the Local Context example, what does the `check_info` function do?
    - A) Fetches data from an external API
    - B) Retrieves user information from `RunContextWrapper`
    - C) Sends data to the LLM
    - D) Validates the agent’s model
    - **Answer**: B

14. What is the output of the `check_info` function in the Local Context example?
    - A) A JSON object
    - B) A formatted string with user details
    - C) A Pydantic model
    - D) A list of user attributes
    - **Answer**: B

15. Why is Local Context not exposed to the LLM?
    - A) To reduce computation time
    - B) To keep it private for backend logic
    - C) To avoid overloading the LLM
    - D) To prevent data validation
    - **Answer**: B

### Agent/LLM Context
16. What is Agent/LLM Context in the OpenAI Agents SDK?
    - A) Data used internally by tools and callbacks
    - B) Information the LLM sees when generating responses
    - C) The agent’s model configuration
    - D) Data stored in a database
    - **Answer**: B

17. How can Agent/LLM Context be provided to the LLM?
    - A) Through the `context` parameter in `Runner.run()`
    - B) By embedding it in the agent’s instructions or input messages
    - C) Using the `RunContextWrapper`
    - D) Via a Pydantic model
    - **Answer**: B

18. Which of the following is part of Agent/LLM Context?
    - A) Logger dependencies
    - B) Conversation history
    - C) Helper functions
    - D) User IDs
    - **Answer**: B

19. How can function tools contribute to Agent/LLM Context?
    - A) By fetching on-demand data for the LLM
    - B) By validating Local Context
    - C) By storing data in a database
    - D) By configuring the agent
    - **Answer**: A

20. What is the purpose of retrieval/web search in Agent/LLM Context?
    - A) To validate Local Context
    - B) To ground the LLM’s responses in external data
    - C) To store conversation history
    - D) To manage API keys
    - **Answer**: B

21. In the provided Agent/LLM Context code, what does the `user_information` function do?
    - A) Validates the user’s input
    - B) Fetches the user’s roll number from `RunContextWrapper`
    - C) Configures the LLM model
    - D) Sends the conversation history to the LLM
    - **Answer**: B

22. What is the role of the `@function_tool` decorator in the Agent/LLM Context example?
    - A) To validate the Pydantic model
    - B) To mark a function as a tool for the LLM
    - C) To initialize the `RunContextWrapper`
    - D) To load the API key
    - **Answer**: B

23. In the Agent/LLM Context example, what information does the LLM receive?
    - A) The entire `UserInfo` object
    - B) Only the roll number via the `user_information` tool
    - C) The Local Context directly
    - D) The API key
    - **Answer**: B

24. What is the key difference between Local Context and Agent/LLM Context?
    - A) Local Context is sent to the LLM, while Agent/LLM Context is internal
    - B) Agent/LLM Context is sent to the LLM, while Local Context is internal
    - C) Both are sent to the LLM
    - D) Both are internal to the backend
    - **Answer**: B

25. In the Agent/LLM Context example, what does the `instructions` parameter in the `Agent` class do?
    - A) Defines the structure of Local Context
    - B) Provides guidance to the LLM on how to use tools
    - C) Configures the API key
    - D) Validates the input query
    - **Answer**: B

### Pydantic
26. What is Pydantic primarily used for in Python?
    - A) Data validation and parsing
    - B) API key management
    - C) LLM response generation
    - D) Web scraping
    - **Answer**: A

27. What is the basis of Pydantic’s design?
    - A) Python’s type annotations
    - B) JSON schemas
    - C) Database queries
    - D) Regular expressions
    - **Answer**: A

28. In the provided code, what is the `UserInfo` class an example of?
    - A) A Pydantic model
    - B) A database schema
    - C) A function tool
    - D) A system prompt
    - **Answer**: A

29. How does Pydantic ensure data correctness in the `UserInfo` class?
    - A) By validating input data against defined types
    - B) By sending data to the LLM
    - C) By storing data in a database
    - D) By using regular expressions
    - **Answer**: A

30. Which of the following is a valid field in the `UserInfo` Pydantic model?
    - A) `logger`
    - B) `roll_num`
    - C) `api_key`
    - D) `instructions`
    - **Answer**: B

31. Why is Pydantic popular for creating Local Context?
    - A) It simplifies API key management
    - B) It ensures type safety and data validation
    - C) It generates LLM responses
    - D) It handles web searches
    - **Answer**: B

32. What happens if the input data for the `UserInfo` class does not match the defined types?
    - A) The data is automatically corrected
    - B) A validation error is raised
    - C) The data is sent to the LLM
    - D) The data is ignored
    - **Answer**: B

### RunContextWrapper
33. What is the purpose of the `RunContextWrapper` class?
    - A) To send context to the LLM
    - B) To wrap the context object passed to `Runner.run()`
    - C) To validate the agent’s model
    - D) To manage API keys
    - **Answer**: B

34. What does the `context` attribute of `RunContextWrapper` contain?
    - A) The conversation history
    - B) The context object passed to `Runner.run()`
    - C) The LLM’s response
    - D) The agent’s instructions
    - **Answer**: B

35. What does the `usage` attribute of `RunContextWrapper` track?
    - A) The agent’s model configuration
    - B) The usage of the agent run so far
    - C) The API key usage
    - DThe conversation history
    - **Answer**: B

36. When is the `usage` attribute of `RunContextWrapper` considered stale?
    - A) For streamed responses, until the last chunk is processed
    - B) When the agent is initialized
    - C) When the API key is invalid
    - D) When the context is updated
    - **Answer**: A

37. In the provided code, how is `RunContextWrapper` used in the `check_info` function?
    - A) To fetch the API key
    - B) To access user information from the context
    - C) To send data to the LLM
    - D) To validate the input query
    - **Answer**: B

38. What is the generic type `TContext` in `RunContextWrapper[UserInfo]`?
    - A) The type of the LLM model
    - B) The type of the context object
    - C) The type of the conversation history
    - D) The type of the agent’s instructions
    - **Answer**: B

### Code-Based Questions
39. In the Local Context example, what is the value of `my_info.name`?
    - A) Karachi
    - B) 22
    - C) hussain
    - D) 343432
    - **Answer**: C

40. What model is used in the `OpenAIChatCompletionsModel` in the provided code?
    - A) gpt-4
    - B) gemini-2.0-flash
    - C) llama-3
    - D) bert-base
    - **Answer**: B

41. What is the purpose of the `load_dotenv()` function in the Agent/LLM Context example?
    - A) To load the agent’s instructions
    - B) To load environment variables like the API key
    - C) To initialize the Pydantic model
    - D) To configure the LLM
    - **Answer**: B

42. In the Agent/LLM Context example, what happens when the query asks for the user’s roll number?
    - A) The `check_info` function directly returns the roll number
    - B) The `user_information` tool is invoked to fetch the roll number
    - C) The LLM generates a random roll number
    - D) The query is ignored
    - **Answer**: B

43. What is the role of the `external_client` variable in the provided code?
    - A) To store the Local Context
    - B) To initialize the AsyncOpenAI client with the API key
    - C) To validate the Pydantic model
    - D) To fetch external data
    - **Answer**: B

44. In the provided code, what does the `tools` parameter in the `Agent` class contain?
    - A) A list of Pydantic models
    - B) A list of function tools like `user_information`
    - C) A list of system prompts
    - D) A list of API keys
    - **Answer**: B

45. What is the output format of the `user_information` function in the Agent/LLM Context example?
    - A) A Pydantic model
    - B) A formatted string
    - C) A JSON object
    - D) A list
    - **Answer**: B

46. In the Local Context example, what is the value of `my_info.city`?
    - A) hussain
    - B) 22
    - C) Karachi
    - D) 343432
    - **Answer**: C

47. What does the `set_tracing_disabled(disabled=True)` function do in the Agent/LLM Context example?
    - A) Disables API key validation
    - B) Disables tracing for the agent run
    - C) Disables the Pydantic model
    - D) Disables the LLM
    - **Answer**: B

48. In the Agent/LLM Context example, what is the query passed to `Runner.run_sync()`?
    - A) "What is the name of user"
    - B) "What is the name of user and the age of his and roll number"
    - C) "What is the roll number"
    - D) "What is the city of user"
    - **Answer**: B

49. Why is the `UserInfo` class used in the `Agent[UserInfo]` declaration?
    - A) To define the structure of the LLM’s responses
    - B) To specify the type of Local Context for the agent
    - C) To configure the API key
    - D) To store the conversation history
    - **Answer**: B

50. What is the final output of the Agent/LLM Context example based on the query?
    - A) A Pydantic model
    - B) A string containing the user’s name, age, and roll number
    - C) A JSON object
    - D) A list of user attributes
    - **Answer**: B

---
