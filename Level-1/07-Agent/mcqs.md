# 50 Multiple-Choice Questions on OpenAI Agents SDK

## Question 1
What is the primary purpose of the OpenAI Agents SDK?
- A) To create complex machine learning models
- B) To build agentic AI applications with minimal abstractions
- C) To manage databases for AI applications
- D) To provide a graphical user interface for AI
**Correct Answer**: B) To build agentic AI applications with minimal abstractions

## Question 2
What is one of the key primitives of the OpenAI Agents SDK?
- A) Databases
- B) Handoffs
- C) User interfaces
- D) Cloud storage
**Correct Answer**: B) Handoffs

## Question 3
What does the "Agent" class represent in the OpenAI Agents SDK?
- A) A database connection
- B) An intelligent AI actor with instructions and tools
- C) A user authentication module
- D) A hardware interface
**Correct Answer**: B) An intelligent AI actor with instructions and tools

## Question 4
What is the role of "Handoffs" in the Agents SDK?
- A) To store data persistently
- B) To allow agents to delegate tasks to other agents
- C) To manage user sessions
- D) To encrypt API keys
**Correct Answer**: B) To allow agents to delegate tasks to other agents

## Question 5
What is the purpose of "Guardrails" in the Agents SDK?
- A) To enhance model accuracy
- B) To validate agent inputs and outputs
- C) To manage network connections
- D) To generate visualizations
**Correct Answer**: B) To validate agent inputs and outputs

## Question 6
What does the "Sessions" primitive in the Agents SDK do?
- A) Manages API keys
- B) Automatically maintains conversation history
- C) Configures hardware settings
- D) Encrypts data
**Correct Answer**: B) Automatically maintains conversation history

## Question 7
What is a key feature of the Agents SDK that allows debugging?
- A) Cloud integration
- B) Built-in tracing
- C) Database management
- D) User authentication
**Correct Answer**: B) Built-in tracing

## Question 8
Why is the Agents SDK considered easy to learn?
- A) It has a large number of features
- B) It has few primitives and minimal abstractions
- C) It requires extensive coding knowledge
- D) It uses complex algorithms
**Correct Answer**: B) It has few primitives and minimal abstractions

## Question 9
What does the `Agent` class require as a minimum parameter?
- A) Tools
- B) Model
- C) Name
- D) Instructions
**Correct Answer**: C) Name

## Question 10
What does the `Runner` class do in the Agents SDK?
- A) Manages database queries
- B) Executes and manages the agent’s thinking loop
- C) Configures network settings
- D) Generates API keys
**Correct Answer**: B) Executes and manages the agent’s thinking loop

## Question 11
What is the purpose of the `OpenAIChatCompletionsModel` class?
- A) To manage user authentication
- B) To interface with OpenAI-compatible LLMs
- C) To store conversation history
- D) To generate visualizations
**Correct Answer**: B) To interface with OpenAI-compatible LLMs

## Question 12
What does the `set_tracing_disabled` function do?
- A) Enables API key encryption
- B) Disables the tracing mechanism
- C) Configures model settings
- D) Manages session history
**Correct Answer**: B) Disables the tracing mechanism

## Question 13
What is the role of the `AsyncOpenAI` class?
- A) To manage synchronous API calls
- B) To connect asynchronously to OpenAI-compatible APIs
- C) To store environment variables
- D) To generate Python code
**Correct Answer**: B) To connect asynchronously to OpenAI-compatible APIs

## Question 14
What does the `load_dotenv` function do?
- A) Loads Python modules
- B) Loads environment variables from a .env file
- C) Configures model parameters
- D) Manages API endpoints
**Correct Answer**: B) Loads environment variables from a .env file

## Question 15
What is a benefit of using the `load_dotenv` function?
- A) It generates API keys
- B) It avoids hard-coding sensitive information
- C) It configures hardware settings
- D) It manages user authentication
**Correct Answer**: B) It avoids hard-coding sensitive information

## Question 16
What is the purpose of the `RunConfig` class?
- A) To manage database connections
- B) To configure settings for running an agent
- C) To generate visualizations
- D) To encrypt API keys
**Correct Answer**: B) To configure settings for running an agent

## Question 17
Which method is used to execute an agent synchronously?
- A) `Runner.run`
- B) `Runner.run_sync`
- C) `Runner.run_streamed`
- D) `Runner.execute`
**Correct Answer**: B) `Runner.run_sync`

## Question 18
What does the `instructions` parameter in the `Agent` class define?
- A) The agent’s name
- B) The system prompt or agent persona
- C) The API key
- D) The model settings
**Correct Answer**: B) The system prompt or agent persona

## Question 19
What happens if the `gemini_api_key` is not loaded in the provided code?
- A) The program continues without errors
- B) A `ValueError` is raised
- C) The model defaults to a free API
- D) The agent uses a local model
**Correct Answer**: B) A `ValueError` is raised

## Question 20
What does the `model` parameter in the `Agent` class specify?
- A) The agent’s name
- B) The LLM to use
- C) The API key
- D) The tracing settings
**Correct Answer**: B) The LLM to use

## Question 21
What is the purpose of the `tools` parameter in the `Agent` class?
- A) To define the agent’s name
- B) To specify tasks the agent can perform
- C) To configure the API endpoint
- D) To manage session history
**Correct Answer**: B) To specify tasks the agent can perform

## Question 22
What does the `tracing_disabled=True` setting in `RunConfig` do?
- A) Enables tracing for debugging
- B) Disables tracing for external model integration
- C) Configures the model’s temperature
- D) Manages conversation history
**Correct Answer**: B) Disables tracing for external model integration

## Question 23
What is the role of the `external_client` in the provided code?
- A) To manage session history
- B) To connect to an external API endpoint
- C) To generate Python code
- D) To configure hardware settings
**Correct Answer**: B) To connect to an external API endpoint

## Question 24
Which library provides the `load_dotenv` function?
- A) OpenAI
- B) Agents
- C) Dotenv
- D) AsyncOpenAI
**Correct Answer**: C) Dotenv

## Question 25
What is the default behavior of the OpenAI SDK regarding API responses?
- A) It uses local models
- B) It uses the OpenAI API
- C) It disables tracing
- D) It stores responses in a database
**Correct Answer**: B) It uses the OpenAI API

## Question 26
What is the purpose of the `Runner.run_streamed` method?
- A) To execute an agent synchronously
- B) To stream the agent’s output
- C) To disable tracing
- D) To manage API keys
**Correct Answer**: B) To stream the agent’s output

## Question 27
What is the significance of the `name` parameter in the `Agent` class?
- A) It specifies the model to use
- B) It identifies the agent
- C) It configures the API endpoint
- D) It manages session history
**Correct Answer**: B) It identifies the agent

## Question 28
What does the `OpenAIChatCompletionsModel` class support?
- A) Database management
- B) Integration with OpenAI-compatible LLMs
- C) User authentication
- D) Hardware configuration
**Correct Answer**: B) Integration with OpenAI-compatible LLMs

## Question 29
What is a key feature of the Agents SDK’s function tools?
- A) Manual schema generation
- B) Automatic schema generation with Pydantic validation
- C) Database connectivity
- D) API key encryption
**Correct Answer**: B) Automatic schema generation with Pydantic validation

## Question 30
What happens if tracing is enabled with an external provider like Gemini?
- A) Tracing works seamlessly
- B) Tracing may fail
 “

**Correct Answer**: B) Tracing may fail

## Question 31
What is the purpose of the `model_provider` parameter in `RunConfig`?
- A) To specify the LLM to use
- B) To configure the API client for the model
- C) To manage session history
- D) To generate visualizations
**Correct Answer**: B) To configure the API client for the model

## Question 32
What does the `result.final_output` contain in the provided code?
- A) The agent’s configuration
- B) The final response from the agent
- C) The API key
- D) The session history
**Correct Answer**: B) The final response from the agent

## Question 33
What is the role of the `Agent` loop in the SDK?
- A) To manage database connections
- B) To handle tool calls and LLM responses
- C) To configure hardware settings
- D) To encrypt API keys
**Correct Answer**: B) To handle tool calls and LLM responses

## Question 34
What does the `Python-first` feature of the Agents SDK mean?
- A) It requires advanced Python knowledge
- B) It uses Python’s built-in features for orchestration
- C) It only supports Python models
- D) It disables other programming languages
**Correct Answer**: B) It uses Python’s built-in features for orchestration

## Question 35
What is the benefit of automatic conversation history management?
- A) It reduces the need for manual state handling
- B) It encrypts conversation data
- C) It generates API keys
- D) It configures model parameters
**Correct Answer**: A) It reduces the need for manual state handling

## Question 36
What does the `base_url` parameter in `AsyncOpenAI` specify?
- A) The model to use
- B) The API endpoint for external models
- C) The session history
- D) The tracing settings
**Correct Answer**: B) The API endpoint for external models

## Question 37
What is the purpose of the `tools` parameter in the `Agent` configuration?
- A) To define the agent’s name
- B) To specify functions the agent can use
- C) To configure the API key
- D) To manage session history
**Correct Answer**: B) To specify functions the agent can use

## Question 38
What is the role of the `Runner.run` method?
- A) To execute an agent asynchronously
- B) To generate API keys
- C) To manage session history
- D) To configure hardware settings
**Correct Answer**: A) To execute an agent asynchronously

## Question 39
What is a key benefit of the Agents SDK’s tracing feature?
- A) It encrypts API keys
- B) It allows visualization and debugging of workflows
- C) It manages database connections
- D) It generates Python code
**Correct Answer**: B) It allows visualization and debugging of workflows

## Question 40
What does the `model_settings` parameter in the `Agent` class configure?
- A) The agent’s name
- B) Model tuning parameters like temperature
- C) The API endpoint
- D) The session history
**Correct Answer**: B) Model tuning parameters like temperature

## Question 41
What is the purpose of the `os.getenv` function in the provided code?
- A) To generate an API key
- B) To retrieve environment variables
- C) To configure the model
- D) To manage session history
**Correct Answer**: B) To retrieve environment variables

## Question 42
What happens if you do not provide a `RunConfig` object when running an agent?
- A) The agent uses default settings
- B) The agent fails to run
- C) The agent generates a new API key
- D) The agent uses a local model
**Correct Answer**: A) The agent uses default settings

## Question 43
What is the role of the `get_weather` tool in the provided `Agent` configuration?
- A) To manage session history
- B) To perform a specific task for the agent
- C) To configure the API endpoint
- D) To generate visualizations
**Correct Answer**: B) To perform a specific task for the agent

## Question 44
What is the purpose of the `Runner` class in the Agents SDK?
- A) To manage API keys
- B) To execute and manage agent workflows
- C) To configure hardware settings
- D) To generate Python code
**Correct Answer**: B) To execute and manage agent workflows

## Question 45
What does the `OpenAIChatCompletionsModel` class use to create a model object?
- A) A database connection
- B) An OpenAI-compatible API client
- C) A local model file
- D) A user authentication module
**Correct Answer**: B) An OpenAI-compatible API client

## Question 46
What is a key feature of the Agents SDK’s guardrails?
- A) They run in parallel to validate inputs and outputs
- B) They manage session history
- C) They generate API keys
- D) They configure hardware settings
**Correct Answer**: A) They run in parallel to validate inputs and outputs

## Question 47
What does the `starting_agent` parameter in `Runner.run_sync` specify?
- A) The API endpoint
- B) The agent to execute
- C) The session history
- D) The model settings
**Correct Answer**: B) The agent to execute

## Question 48
What is the purpose of the `input` parameter in `Runner.run_sync`?
- A) To specify the model to use
- B) To provide the task or query for the agent
- C) To configure the API endpoint
- D) To manage session history
**Correct Answer**: B) To provide the task or query for the agent

## Question 49
What is the benefit of using Pydantic-powered validation in function tools?
- A) It reduces API calls
- B) It ensures accurate schema generation
- C) It manages session history
- D) It encrypts API keys
**Correct Answer**: B) It ensures accurate schema generation

## Question 50
What is the purpose of the `haiku` instruction in the provided `Agent` configuration?
- A) To configure the model
- B) To define the agent’s response format
- C) To manage session history
- D) To generate visualizations
**Correct Answer**: B) To define the agent’s response format