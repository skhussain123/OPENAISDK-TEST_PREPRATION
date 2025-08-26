# 50 MCQs on Context Management in OpenAI Agents SDK

1. **What is the primary purpose of context management in the OpenAI Agents SDK?**  
   a) To handle the agent's user interface  
   b) To manage additional data used during an agent’s execution  
   c) To train the LLM model  
   d) To store API keys securely  
   **Answer**: b) To manage additional data used during an agent’s execution  

2. **How many main forms of context are described in the OpenAI Agents SDK?**  
   a) One  
   b) Two  
   c) Three  
   d) Four  
   **Answer**: b) Two  

3. **Which of the following is NOT a type of context in the OpenAI Agents SDK?**  
   a) Local Context  
   b) Agent/LLM Context  
   c) Global Context  
   d) None of the above  
   **Answer**: c) Global Context  

4. **What is the key difference between Local Context and Agent/LLM Context?**  
   a) Local Context is sent to the LLM, while Agent/LLM Context is not  
   b) Local Context is internal and not sent to the LLM, while Agent/LLM Context is exposed to the LLM  
   c) Both are sent to the LLM  
   d) Both are internal and not sent to the LLM  
   **Answer**: b) Local Context is internal and not sent to the LLM, while Agent/LLM Context is exposed to the LLM  

5. **Which component of the OpenAI Agents SDK wraps the context object passed to `Runner.run()`?**  
   a) AgentWrapper  
   b) RunContextWrapper  
   c) ContextManager  
   d) PydanticWrapper  
   **Answer**: b) RunContextWrapper  

## Local Context Questions

6. **What is Local Context in the OpenAI Agents SDK?**  
   a) Data sent to the LLM to generate responses  
   b) Data or dependencies passed to the agent's run, used internally by tools and hooks  
   c) A global configuration for the agent  
   d) A database connection for the agent  
   **Answer**: b) Data or dependencies passed to the agent's run, used internally by tools and hooks  

7. **Which of the following is a common way to create a Local Context?**  
   a) Using a Python dictionary  
   b) Using a Pydantic model or dataclass  
   c) Using a JSON file  
   d) Using a text file  
   **Answer**: b) Using a Pydantic model or dataclass  

8. **How is Local Context passed to an agent’s run?**  
   a) Through the `context` parameter in `Runner.run()`  
   b) Through the `instructions` parameter  
   c) Through the `tools` parameter  
   d) Through the `model` parameter  
   **Answer**: a) Through the `context` parameter in `Runner.run()`  

9. **What happens to the Local Context after it is passed to `Runner.run()`?**  
   a) It is sent to the LLM  
   b) It is wrapped in a `RunContextWrapper` and made available to tools and hooks  
   c) It is stored in a database  
   d) It is discarded after the run  
   **Answer**: b) It is wrapped in a `RunContextWrapper` and made available to tools and hooks  

10. **Which of the following is NOT a use case for Local Context?**  
    a) Storing user details like username or ID  
    b) Injecting a logger for debugging  
    c) Providing helper functions for the run  
    d) Sending conversation history to the LLM  
    **Answer**: d) Sending conversation history to the LLM  

11. **What ensures consistency in a single agent run regarding Local Context?**  
    a) All parts of the run must use the same type of context  
    b) The context is validated by the LLM  
    c) The context is stored in a global variable  
    d) The context is reset after each run  
    **Answer**: a) All parts of the run must use the same type of context  

12. **In the provided code, what is the purpose of the `UserInfo` class?**  
    a) To define the structure of Local Context using a Pydantic model  
    b) To store the agent’s instructions  
    c) To configure the LLM model  
    d) To handle API key management  
    **Answer**: a) To define the structure of Local Context using a Pydantic model  

13. **What does the `check_info` function do in the Local Context example?**  
    a) Sends user information to the LLM  
    b) Fetches and formats user information from the `RunContextWrapper`  
    c) Validates the API key  
    d) Configures the agent’s tools  
    **Answer**: b) Fetches and formats user information from the `RunContextWrapper`  

14. **In the Local Context example, what is the role of `my_info`?**  
    a) It is the input query for the agent  
    b) It is an instance of the `UserInfo` class passed as context  
    c) It is the agent’s configuration  
    d) It is the LLM model  
    **Answer**: b) It is an instance of the `UserInfo` class passed as context  

15. **Which of the following is true about Local Context?**  
    a) It is exposed to the LLM for response generation  
    b) It is only used for frontend logic  
    c) It is used for backend logic and operations  
    d) It is stored permanently in the SDK  
    **Answer**: c) It is used for backend logic and operations  

## Agent/LLM Context Questions

16. **What is Agent/LLM Context in the OpenAI Agents SDK?**  
    a) Internal data used by tools and hooks  
    b) Information the LLM sees to generate responses, like conversation history  
    c) A configuration file for the agent  
    d) A database for storing user inputs  
    **Answer**: b) Information the LLM sees to generate responses, like conversation history  

17. **How can Agent/LLM Context be provided to the LLM?**  
    a) By embedding it in the agent’s instructions or system prompts  
    b) By storing it in a database  
    c) By passing it through the `context` parameter in `Runner.run()`  
    d) By configuring the `RunContextWrapper`  
    **Answer**: a) By embedding it in the agent’s instructions or system prompts  

18. **Which of the following is a method to include Agent/LLM Context?**  
    a) Passing context in the input message to `Runner.run()`  
    b) Storing context in a Pydantic model  
    c) Using a dataclass for conversation history  
    d) Injecting context into the LLM’s weights  
    **Answer**: a) Passing context in the input message to `Runner.run()`  

19. **What role do function tools play in Agent/LLM Context?**  
    a) They validate the Local Context  
    b) They fetch on-demand data for the LLM  
    c) They configure the agent’s model  
    d) They store conversation history  
    **Answer**: b) They fetch on-demand data for the LLM  

20. **How can external data be incorporated into Agent/LLM Context?**  
    a) Using retrieval or web search tools  
    b) Using a Pydantic model  
    c) Using the `RunContextWrapper`  
    d) Using a database connection  
    **Answer**: a) Using retrieval or web search tools  

21. **In the Agent/LLM Context example, what does the `user_information` function do?**  
    a) Fetches the user’s roll number and shares it with the LLM  
    b) Validates the user’s API key  
    c) Configures the agent’s instructions  
    d) Stores the user’s data in a database  
    **Answer**: a) Fetches the user’s roll number and shares it with the LLM  

22. **What is the purpose of the `@function_tool` decorator in the Agent/LLM Context example?**  
    a) To validate the Pydantic model  
    b) To mark a function as a tool that the LLM can invoke  
    c) To configure the agent’s model  
    d) To disable tracing  
    **Answer**: b) To mark a function as a tool that the LLM can invoke  

23. **In the Agent/LLM Context example, how is the `user_information` function used?**  
    a) It is called directly by the agent  
    b) It is invoked by the LLM when needed to fetch the roll number  
    c) It is used to initialize the `UserInfo` class  
    d) It is used to validate the input query  
    **Answer**: b) It is invoked by the LLM when needed to fetch the roll number  

24. **Which of the following is NOT a way to provide Agent/LLM Context?**  
    a) Embedding context in system prompts  
    b) Passing context in the input message  
    c) Using function tools to fetch data  
    d) Storing context in the `RunContextWrapper`  
    **Answer**: d) Storing context in the `RunContextWrapper`  

25. **What is the main purpose of Agent/LLM Context?**  
    a) To manage backend dependencies  
    b) To guide the LLM’s response generation  
    c) To store user data permanently  
    d) To configure the agent’s API key  
    **Answer**: b) To guide the LLM’s response generation  

## Pydantic Questions

26. **What is Pydantic in the context of the OpenAI Agents SDK?**  
    a) A database management library  
    b) A Python library for data validation and parsing  
    c) A tool for configuring LLMs  
    d) A library for API key management  
    **Answer**: b) A Python library for data validation and parsing  

27. **What is the basis of Pydantic’s design?**  
    a) Python type annotations  
    b) JSON schemas  
    c) XML parsing  
    d) Database queries  
    **Answer**: a) Python type annotations  

28. **How does Pydantic ensure data validity?**  
    a) By checking data against predefined Python classes  
    b) By querying a database  
    c) By sending data to the LLM  
    d) By using regular expressions  
    **Answer**: a) By checking data against predefined Python classes  

29. **In the provided code, how is Pydantic used?**  
    a) To define the `UserInfo` class for structuring Local Context  
    b) To configure the agent’s instructions  
    c) To validate the LLM’s responses  
    d) To manage API keys  
    **Answer**: a) To define the `UserInfo` class for structuring Local Context  

30. **Which of the following is a benefit of using Pydantic for Local Context?**  
    a) It automatically sends data to the LLM  
    b) It ensures data conforms to the defined structure  
    c) It configures the agent’s model  
    d) It stores data in a database  
    **Answer**: b) It ensures data conforms to the defined structure  

## RunContextWrapper Questions

31. **What is the `RunContextWrapper` class in the OpenAI Agents SDK?**  
    a) A class that wraps the context object passed to `Runner.run()`  
    b) A class that configures the LLM model  
    c) A class that stores conversation history  
    d) A class that validates API keys  
    **Answer**: a) A class that wraps the context object passed to `Runner.run()`  

32. **What does the `context` attribute of `RunContextWrapper` contain?**  
    a) The LLM’s conversation history  
    b) The context object passed to `Runner.run()`  
    c) The agent’s instructions  
    d) The API key  
    **Answer**: b) The context object passed to `Runner.run()`  

33. **What is the `usage` attribute in `RunContextWrapper` used for?**  
    a) To track the agent’s run usage, such as tokens consumed  
    b) To store the user’s input query  
    c) To configure the agent’s tools  
    d) To validate the context object  
    **Answer**: a) To track the agent’s run usage, such as tokens consumed  

34. **When does the `usage` attribute in `RunContextWrapper` become stale?**  
    a) During streamed responses, until the last chunk is processed  
    b) After the agent’s run is complete  
    c) When the context object is updated  
    d) When the LLM generates a response  
    **Answer**: a) During streamed responses, until the last chunk is processed  

35. **What is the purpose of the `RunContextWrapper` in the provided code?**  
    a) To send user data to the LLM  
    b) To make the `UserInfo` object available to tools and hooks  
    c) To configure the agent’s model  
    d) To validate the input query  
    **Answer**: b) To make the `UserInfo` object available to tools and hooks  

## Code-Based Questions

36. **In the Local Context example, what is the role of the `myagent` variable?**  
    a) It defines the input query  
    b) It creates an instance of the `Agent` class with `UserInfo` context  
    c) It configures the API key  
    d) It stores the conversation history  
    **Answer**: b) It creates an instance of the `Agent` class with `UserInfo` context  

37. **What does the `instructions` parameter in the `Agent` constructor do in the Local Context example?**  
    a) It defines the LLM’s system prompts  
    b) It specifies the `check_info` function for processing context  
    c) It configures the agent’s model  
    d) It validates the `UserInfo` class  
    **Answer**: b) It specifies the `check_info` function for processing context  

38. **In the Agent/LLM Context example, what is the purpose of the `tools` parameter in the `Agent` constructor?**  
    a) To define the `user_information` function as a tool for the LLM  
    b) To configure the API key  
    c) To store the conversation history  
    d) To validate the input query  
    **Answer**: a) To define the `user_information` function as a tool for the LLM  

39. **What is the output of the `Runner.run_sync` call in the Agent/LLM Context example for the query "What is the name of user and the age of his and roll number"?**  
    a) The user’s name, age, and roll number  
    b) The API key  
    c) The agent’s configuration  
    d) The conversation history  
    **Answer**: a) The user’s name, age, and roll number  

40. **In the provided code, what is the purpose of the `load_dotenv()` function?**  
    a) To load the agent’s instructions  
    b) To load environment variables, including the API key  
    c) To configure the Pydantic model  
    d) To initialize the LLM model  
    **Answer**: b) To load environment variables, including the API key  

## Miscellaneous Questions

41. **Which library is used to disable tracing in the provided code?**  
    a) `os`  
    b) `dotenv`  
    c) `agents`  
    d) `pydantic`  
    **Answer**: c) `agents`  

42. **What is the purpose of the `set_tracing_disabled` function in the code?**  
    a) To disable debugging logs for the agent’s run  
    b) To disable the LLM’s response generation  
    c) To disable API key validation  
    d) To disable the Pydantic model  
    **Answer**: a) To disable debugging logs for the agent’s run  

43. **What is the role of the `external_client` variable in the provided code?**  
    a) It configures the Pydantic model  
    b) It creates an `AsyncOpenAI` client for interacting with the LLM  
    c) It stores the user’s input query  
    d) It validates the context object  
    **Answer**: b) It creates an `AsyncOpenAI` client for interacting with the LLM  

44. **Which model is used in the provided code examples?**  
    a) `gpt-3.5-turbo`  
    b) `gemini-2.0-flash`  
    c) `bert-base`  
    d) `llama-2`  
    **Answer**: b) `gemini-2.0-flash`  

45. **What is the purpose of the `OpenAIChatCompletionsModel` in the code?**  
    a) To define the structure of the Local Context  
    b) To configure the LLM model used by the agent  
    c) To validate the input query  
    d) To store the conversation history  
    **Answer**: b) To configure the LLM model used by the agent  

46. **In the Agent/LLM Context example, how does the LLM access the user’s roll number?**  
    a) Through the `check_info` function  
    b) By invoking the `user_information` tool  
    c) Through the `UserInfo` class directly  
    d) Through the `RunContextWrapper` context attribute  
    **Answer**: b) By invoking the `user_information` tool  

47. **What is the significance of the `base_url` in the `AsyncOpenAI` client configuration?**  
    a) It specifies the endpoint for the LLM API  
    b) It defines the agent’s instructions  
    c) It configures the Pydantic model  
    d) It stores the user’s context  
    **Answer**: a) It specifies the endpoint for the LLM API  

48. **Which of the following is a valid use case for Local Context in a real-world application?**  
    a) Passing a database connection to fetch user data during a run  
    b) Sending a user’s preferences to the LLM  
    c) Configuring the LLM’s hyperparameters  
    d) Storing the agent’s responses permanently  
    **Answer**: a) Passing a database connection to fetch user data during a run  

49. **What happens if the `GEMINI_API_KEY` is not found in the environment variables?**  
    a) The code continues without an API key  
    b) A `ValueError` is raised  
    c) The agent uses a default API key  
    d) The LLM generates an error message  
    **Answer**: b) A `ValueError` is raised  

50. **Which of the following best describes the relationship between Local Context and Agent/LLM Context?**  
    a) They serve the same purpose and are interchangeable  
    b) Local Context is for backend logic, while Agent/LLM Context guides LLM responses  
    c) Both are sent to the LLM for processing  
    d) Both are stored in the `RunContextWrapper` for validation  
    **Answer**: b) Local Context is for backend logic, while Agent/LLM Context guides LLM responses  

---
