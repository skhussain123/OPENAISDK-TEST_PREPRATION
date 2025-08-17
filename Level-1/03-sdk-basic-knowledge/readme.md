## OpenAI Agents SDK
The OpenAI Agents SDK enables you to build agentic AI apps in a lightweight, easy-to-use package with very few abstractions. It's a production-ready upgrade of our previous experimentation for agents, Swarm. The Agents SDK has a very small set of primitives:


1. Agents, which are LLMs equipped with instructions and tools
2. Handoffs, which allow agents to delegate to other agents for specific tasks
3. Guardrails, which enable the inputs to agents to be validated
4. Sessions, which automatically maintains conversation history across agent runs

In combination with Python, these primitives are powerful enough to express complex relationships between tools and agents, and allow you to build real-world applications without a steep learning curve. In addition, the SDK comes with built-in tracing that lets you visualize and debug your agentic flows, as well as evaluate them and even fine-tune models for your application

### Why use the Agents SDK

* Enough features to be worth using, but few enough primitives to make it quick to learn.
* Works great out of the box, but you can customize exactly what happens.

1. Agent loop: Built-in agent loop that handles calling tools, sending results to the LLM, and looping until the LLM is done.
2. Python-first: Use built-in language features to orchestrate and chain agents, rather than needing to learn new abstractions.
3. Handoffs: A powerful feature to coordinate and delegate between multiple agents.
4. Guardrails: Run input validations and checks in parallel to your agents, breaking early if the checks fail.
5. Sessions: Automatic conversation history management across agent runs, eliminating manual state handling.
6. Function tools: Turn any Python function into a tool, with automatic schema generation and Pydantic-powered validation
7. Tracing: Built-in tracing that lets you visualize, debug and monitor your workflows, as well as use the OpenAI suite of evaluation, fine-tuning and distillation tools.



# OpenAI Agents SDK: Provides a Foundational Layer For Building AI Agents

The OpenAI Agents SDK is an open‐source, lightweight framework that lets developers build and orchestrate “agentic” AI applications—systems where multiple AI “agents” work together to perform complex, multi-step tasks autonomously. 


## Questions to Start Thinking

OpenAI Agents SDK is designed very well, I have some questions so that you start thinking about the code:

1. The Agent class has been defined as a dataclass why?

Check the source code of Agent: https://openai.github.io/openai-agents-python/ref/agent/

2a. The system prompt is contained in the Agent class as instructions? Why you can also set it as callable?

2b. But the user prompt is passed as parameter in the run method of Runner and the method is a classmethod

Check this out: https://openai.github.io/openai-agents-python/ref/run/

3. What is the purpose of the Runner class?

4. What are generics in Python? Why we use it for TContext?


Note: Check out the source code to understand.



Here are the key details:

---

### Core Concepts : The Power of Simplicity in Design

What truly sets the Agents SDK apart is its thoughtful balance of simplicity and power. The SDK is built around four core primitives:

- **Agents:**  
  These are language models (LLMs) that are preconfigured with specific instructions, access to tools (like web search or file retrieval), and even safety guardrails. Agents can generate responses and decide which tool to call based on the context.  
 

- **Handoffs:**  
  One of the SDK’s powerful features is the ability to delegate tasks between agents. If one agent encounters a problem or a step outside its domain, it can “hand off” the task to another, specialized agent.  
 

- **Guardrails:**  
  These are built-in safety checks that validate inputs and outputs, ensuring that the agents operate within defined parameters and reducing risks associated with automation.  
  

- **Tracing & Observability:**  
  The SDK includes integrated tracing capabilities that allow developers to visualize and debug the flow of an agent’s actions. This is particularly useful for monitoring complex workflows and optimizing performance.

This minimalist approach makes the SDK approachable for newcomers while providing enough flexibility for experienced developers to build sophisticated systems. The built-in tracing capabilities further enhance the development experience by making it easy to visualize, debug, and evaluate agent workflows.
  

---

### Key Features

- **Python-First Design:**  
  The SDK is designed to integrate naturally with Python. Developers can quickly set up agents, define the tools they can use (even converting Python functions into callable tools), and chain together workflows without needing a steep learning curve.

- **Built-in Agent Loop:**  
  When you run an agent with the SDK, it automatically enters a loop where it:
  1. Sends a prompt to the LLM.
  2. Checks if any tools need to be invoked.
  3. Handles handoffs between agents.
  4. Repeats until a final output is produced.
  
- **Interoperability:**  
  Although built to work seamlessly with OpenAI’s own models and the new Responses API, the Agents SDK is flexible enough to work with any model provider that supports the Chat Completions API format.

- **Simplified Multi-Agent Workflows:**  
  It allows the creation of complex systems where, for example, one agent might perform research while another handles customer support tasks—each agent working in tandem to achieve a common goal.  
  

---


- **Real-World Applications:**  
  Enterprises use the SDK to build AI-powered assistants that can, for instance, pull real-time data via web search, access internal documents using file search, and even interact with computer interfaces. This is making AI agents practical for industries like customer support, legal research, finance, and more.  
 

---

### Why It Matters

By abstracting much of the orchestration logic that was previously handled manually or through ad-hoc integrations, the Agents SDK simplifies the development process, allowing you to focus on building the core functionalities of your application. With fewer abstractions and a Python-centric approach, it’s easier to maintain, extend, and debug complex agent workflows.

In summary, the OpenAI Agents SDK provides the building blocks for creating autonomous, multi-agent systems that can tackle complex tasks by coordinating the strengths of different agents—an essential step forward in making AI truly action-oriented and production-ready.

---

## Early Reviews

Developers are giving the OpenAI Agents SDK high marks for its simplicity and power. Here’s a snapshot of the feedback from the community:

- **Ease of Use & Python-First Approach:**  
  Many developers appreciate that the SDK has very few abstractions and is designed for Python. This means you can quickly set up agents, define tools, and orchestrate workflows without an overwhelming learning curve. Tutorials and beginner guides praise how the framework turns complex multi-agent setups into something that “just works.”  
 

- **Streamlined Multi-Agent Workflows:**  
  Developers are excited about the built-in handoffs and tracing features. The ability to pass tasks seamlessly between specialized agents and then visually track and debug these interactions is seen as a game-changer compared to the previous, more manual approaches.  
  

- **Community and Open-Source Adoption:**  
  The GitHub repository already has nearly 2,000 stars and numerous forks, indicating robust community interest and contribution. Users are actively sharing examples, reporting issues, and suggesting enhancements—an encouraging sign that the SDK is both useful and evolving based on real-world needs.  
 

- **Real-World Impact:**  
  Beyond individual projects, enterprise-level reviews (for example, from companies like Box) suggest that when combined with other tools (like web and file search), the SDK makes it easier to integrate internal data with real-time external information. This holistic approach is being viewed as pivotal for building truly autonomous AI systems.  
 

Overall, developers and early adopters are very positive about the SDK, praising it for reducing manual prompt engineering, enabling more autonomous agents, and providing clear, actionable feedback through its tracing tools. The enthusiasm from the community and growing enterprise interest signal that this framework could become a cornerstone for future AI applications.


### Summary
OpenAI ka Swarm ek experimental framework tha jo multi-agent systems ko simple aur lightweight tareeqe se manage karne ke liye banaya gaya. Isme do main concepts thay.Swarm ka goal yeh tha ke multiple agents mil kar ek complex objective solve kar saken.

* Agents → chhote AI units jo apna specific kaam karte hain (jaise billing ka agent, support ka agent).
* Handoffs → ek agent se doosre agent ko kaam transfer karne ka system.

Ab OpenAI ne Agents SDK release kiya hai jo Swarm ka advanced aur production-ready version hai. Isme aur zyada powerful features hain jisse developers asaan tareeqe se multiple AI agents ko coordinate kar saken.

Is SDK ka design Anthropic ke kuch design patterns se bhi match karta hai, jaise:

1. Prompt Chaining – complex task ko chhote steps mein todna.
2. Routing – kaam ko sahi agent tak pohchana.
3. Parallelization – ek saath multiple tasks chalana.
4. Orchestrator-Workers – ek leader agent tasks ko tod kar worker agents ko assign karta hai.
5. Evaluator-Optimizer – feedback system jo agents ke performance ko improve karta hai.

Simple lafzon mein: Swarm ne basic foundation banayi thi multi-agent systems ke liye, aur Agents SDK uska upgraded version hai jisme advanced features aur proven design patterns use hote hain.


#### Some Free Model
1. gpt 4o
2. gemini 1.5 flash
3. gemini 2.0 flash
4. grmini 2.5 flash
