# 1. MCQs on Selecting Large Language Models (LLMs)
## Questions

**Q1. Which resource is recommended for evaluating LLMs based on crowdsourced human votes and Elo ratings?**  
a) Google Cloud’s Vertex AI metrics  
b) Chatbot Arena Leaderboard by LMSYS (correct)  
c) OpenAI’s official documentation  
d) X Platform user reviews  

**Explanation**: The Chatbot Arena Leaderboard by LMSYS is a trusted, community-backed resource for ranking LLMs based on real-world conversational performance.

---

**Q2. What is a key consideration when choosing an LLM to minimize agenda-driven filtering?**  
a) The model’s ability to generate structured outputs  
b) The philosophy behind the model’s development and response honesty (correct)  
c) The model’s latency performance  
d) The model’s multimodal capabilities  

**Explanation**: Minimizing agenda-driven filtering involves examining the model’s development philosophy and testing its responses to bold prompts to ensure unpolished, honest answers.

---

**Q3. Which LLM is noted for its massive context size of up to 1 million tokens, ideal for AI agents processing large datasets?**  
a) xAI’s Grok  
b) Google’s Gemini Flash (correct)  
c) Anthropic’s Claude Sonnet  
d) OpenAI’s ChatGPT  

**Explanation**: Gemini Flash supports up to 1M tokens, surpassing Claude (200k), ChatGPT (128k), and Grok (32k), making it ideal for memory-intensive agent tasks.

---

**Q4. For an AI agent requiring ultra-low latency (under 200ms), which LLM is the best choice?**  
a) Anthropic’s Claude Sonnet  
b) DeepSeek-R1  
c) Google’s Gemini Flash (correct)  
d) OpenAI’s ChatGPT  

**Explanation**: Gemini Flash is optimized for real-time use, offering sub-200ms latency, outperforming ChatGPT (200–500ms), Claude (300–600ms), and DeepSeek-R1 (variable, hardware-dependent).

---

**Q5. Which criterion is critical for AI agents that need to produce machine-readable responses like JSON for system integration?**  
a) Cost efficiency  
b) Structured output (correct)  
c) Reasoning ability  
d) Context size  

**Explanation**: Structured output (e.g., JSON, YAML) is essential for agents interfacing with systems that require consistent, parsable formats.

---

**Q6. Which LLM is the most cost-efficient due to its open-source nature, requiring only compute costs for self-hosting?**  
a) Anthropic’s Claude Sonnet  
b) DeepSeek-R1 (correct)  
c) OpenAI’s ChatGPT  
d) Google’s Gemini Flash  

**Explanation**: DeepSeek-R1’s open-source status eliminates API fees, with costs limited to self-hosting compute, making it far cheaper than proprietary models.

---

**Q7. Which LLM offers the most mature and widely adopted API ecosystem for production-ready AI agent deployment?**  
a) DeepSeek-R1  
b) xAI’s Grok  
c) OpenAI’s ChatGPT (correct)  
d) Anthropic’s Claude Sonnet  

**Explanation**: ChatGPT’s APIs (e.g., Chat Completion) and SDKs (Python, Node.js) are industry-leading, widely adopted, and developer-friendly, surpassing others in maturity.

---

**Q8. For an AI agent focused on complex reasoning tasks like research or strategic planning, which LLM excels?**  
a) Google’s Gemini Flash  
b) Anthropic’s Claude Sonnet (correct)  
c) xAI’s Grok  
d) DeepSeek-R1  

**Explanation**: Claude Sonnet is praised for its superior reasoning, often outperforming others on benchmarks like MMLU, ideal for deep analytical tasks.

---

**Q9. Which LLM is best for budget-conscious AI agents needing significant context size and customizable output?**  
a) OpenAI’s ChatGPT  
b) DeepSeek-R1 (correct)  
c) Anthropic’s Claude Sonnet  
d) Google’s Gemini Flash  

**Explanation**: DeepSeek-R1’s open-source flexibility, 128k-token context, and low cost make it ideal for budget-conscious agents with customizable output needs.

---

**Q10. What is a key advantage of Google’s Gemini Flash for AI agents requiring multimodal capabilities?**  
a) Its unmatched reasoning depth  
b) Its ability to handle text and video inputs effectively (correct)  
c) Its open-source availability  
d) Its minimal context size  

**Explanation**: Gemini Flash excels in multimodal tasks, effectively processing text and video, which is valuable for versatile agent applications.

---

**Q11. Which LLM is described as having a unique “outsider’s view” for inventive problem-solving?**  
a) OpenAI’s ChatGPT  
b) xAI’s Grok (correct)  
c) Anthropic’s Claude Sonnet  
d) Google’s Gemini Flash  

**Explanation**: Grok is designed to reason from scratch with an outsider’s perspective, making it stand out for creative problem-solving.

---

**Q12. For an AI agent requiring high accuracy in critical operations, which LLM is a top choice?**  
a) Google’s Gemini Flash  
b) xAI’s Grok  
c) Anthropic’s Claude Sonnet (correct)  
d) DeepSeek-R1  

**Explanation**: Claude Sonnet’s focus on clarity and low hallucination rates makes it highly accurate, ideal for critical applications.

---

**Q13. Which LLM’s API ecosystem is backed by Google Cloud’s Vertex AI, offering enterprise-grade reliability?**  
a) Anthropic’s Claude Sonnet  
b) OpenAI’s ChatGPT  
c) Google’s Gemini Flash (correct)  
d) xAI’s Grok  

**Explanation**: Gemini Flash’s APIs via Vertex AI provide mature, reliable, and multimodal support, making it a strong choice for enterprise-grade agent deployment.

---

**Q14. Which LLM is noted for its generous free tier, making it ideal for prototyping AI agents?**  
a) DeepSeek-R1  
b) OpenAI’s ChatGPT  
c) Google’s Gemini Flash (correct)  
d) Anthropic’s Claude Sonnet  

**Explanation**: Gemini Flash’s free tier (e.g., 15 RPM, 1M tokens) is highly developer-friendly, perfect for prototyping and cost-sensitive projects.

---

**Q15. What is a key limitation of xAI’s Grok compared to other LLMs for AI agent development?**  
a) Its high latency  
b) Its limited context size of 32k tokens (correct)  
c) Its lack of tool-calling capabilities  
d) Its expensive pricing model  

**Explanation**: Grok’s 32k-token context is smaller than competitors like Gemini Flash (1M) or Claude (200k), limiting its use for memory-intensive tasks.

---

**Q16. Which LLM is best for AI agents requiring seamless integration with frameworks like LangChain or AutoGen?**  
a) Google’s Gemini Flash  
b) OpenAI’s ChatGPT (correct)  
c) xAI’s Grok  
d) DeepSeek-R1  

**Explanation**: ChatGPT’s mature APIs and extensive support in frameworks like LangChain and AutoGen make it the top choice for seamless tool integration.

---

**Q17. For an AI agent processing long histories or large datasets, which LLM offers the largest context size?**  
a) Anthropic’s Claude Sonnet (200k tokens)  
b) OpenAI’s ChatGPT (128k tokens)  
c) Google’s Gemini Flash (1M tokens) (correct)  
d) DeepSeek-R1 (128k tokens)  

**Explanation**: Gemini Flash’s 1M-token context dwarfs Claude (200k), ChatGPT (128k), and DeepSeek-R1 (128k), making it ideal for large-scale data processing.

---

**Q18. Which LLM’s open-source nature allows for customizable tool-calling and structured output, though it requires self-hosting?**  
a) Google’s Gemini Flash  
b) DeepSeek-R1 (correct)  
c) Anthropic’s Claude Sonnet  
d) OpenAI’s ChatGPT  

**Explanation**: DeepSeek-R1’s open-source flexibility allows customization of tool-calling and output, but it requires self-hosting, unlike proprietary models.

---

**Q19. Which LLM is noted for balancing cost and capability, with a context size of 200k tokens?**  
a) xAI’s Grok  
b) Anthropic’s Claude Sonnet (correct)  
c) OpenAI’s ChatGPT  
d) Google’s Gemini Flash  

**Explanation**: Claude Sonnet offers a 200k-token context and competitive pricing, striking a balance between cost and high performance.

---

**Q20. What is a recommended method to test an LLM’s suitability for an AI agent’s specific needs?**  
a) Reviewing its training dataset  
b) Throwing a challenging, task-specific prompt at the model (correct)  
c) Checking its hardware compatibility  
d) Analyzing its developer community size  

**Explanation**: Testing an LLM with a challenging, task-specific prompt (e.g., multi-tool task with long input and JSON output) directly assesses its performance for the agent’s goals.

-------------------------------------------------------------------------------------------------------------------------------------

# 2. Additional MCQs on AI Agent Frameworks and OpenAI Agents SDK
## Questions

**Q1. What makes OpenAI Agents SDK the top choice for most agentic development projects?**  
a) Its integration with Kubernetes for distributed systems  
b) Its high simplicity, low learning curve, and high control (correct)  
c) Its focus on conversational agents with human-in-the-loop  
d) Its extensive graph-based workflow capabilities  

**Explanation**: OpenAI Agents SDK’s high simplicity, low learning curve, and high control make it highly accessible and flexible for a wide range of agentic development needs.

---

**Q2. Which framework has a "Low" learning curve, making it ideal for beginners in agentic development?**  
a) LangGraph  
b) Dapr Agents  
c) OpenAI Agents SDK (correct)  
d) Google ADK  

**Explanation**: OpenAI Agents SDK’s "Low" learning curve, as per the comparison table, makes it ideal for beginners, unlike LangGraph’s "Very High" or Google ADK and Dapr Agents’ "Medium" learning curves.

---

**Q3. What is a key benefit of OpenAI Agents SDK’s minimal abstraction level?**  
a) It provides pre-built templates for role-based collaboration  
b) It allows direct control over agent primitives for customization (correct)  
c) It includes 50+ data connectors for enterprise integration  
d) It automates complex multi-agent hierarchies  

**Explanation**: The minimal abstraction level of OpenAI Agents SDK enables developers to directly manipulate agent primitives, offering high customization without restrictive abstractions.

---

**Q4. Which framework is least suited for projects requiring rapid prototyping due to its complexity?**  
a) OpenAI Agents SDK  
b) CrewAI  
c) LangGraph (correct)  
d) AutoGen  

**Explanation**: LangGraph’s "Very High" learning curve and "Low" simplicity make it complex and less suitable for rapid prototyping compared to OpenAI Agents SDK’s simplicity.

---

**Q5. For a project prioritizing ease of use and quick iteration, which framework is the best fit?**  
a) Google ADK  
b) OpenAI Agents SDK (correct)  
c) Dapr Agents  
d) LangGraph  

**Explanation**: OpenAI Agents SDK’s "High" simplicity and "Low" learning curve make it ideal for projects needing ease of use and quick iteration.

---

**Q6. Which framework is designed specifically for conversational agents with flexible human-in-the-loop support?**  
a) OpenAI Agents SDK  
b) AutoGen (correct)  
c) LangGraph  
d) Dapr Agents  

**Explanation**: AutoGen’s "High" abstraction and focus on conversational agents with human-in-the-loop support make it ideal for such use cases.

---

**Q7. What is a limitation of OpenAI Agents SDK for large-scale enterprise deployments?**  
a) Its lack of support for agent collaboration  
b) Its limited built-in scalability features like Kubernetes integration (correct)  
c) Its high abstraction level reducing flexibility  
d) Its inability to handle multi-agent workflows  

**Explanation**: OpenAI Agents SDK may lack advanced scalability features like Kubernetes integration, which frameworks like Dapr Agents provide for enterprise-scale systems.

---

**Q8. Which framework offers the highest control for developers needing fine-grained workflow customization?**  
a) OpenAI Agents SDK  
b) LangGraph (correct)  
c) CrewAI  
d) Google ADK  

**Explanation**: LangGraph’s "Very High" control makes it ideal for fine-grained workflow customization, though its complexity is a trade-off compared to OpenAI Agents SDK.

---

**Q9. Which framework provides built-in resiliency and 50+ data connectors for distributed agent systems?**  
a) OpenAI Agents SDK  
b) Dapr Agents (correct)  
c) AutoGen  
d) CrewAI  

**Explanation**: Dapr Agents’ features, including 50+ data connectors and built-in resiliency, make it suited for distributed agent systems.

---

**Q10. Why is OpenAI Agents SDK preferred over CrewAI for most agentic development?**  
a) It offers better support for distributed systems  
b) It provides higher simplicity and control with minimal abstraction (correct)  
c) It includes advanced graph-based workflow tools  
d) It has a higher learning curve for complex projects  

**Explanation**: OpenAI Agents SDK’s high simplicity, high control, and minimal abstraction make it more versatile than CrewAI’s moderate abstraction and role-based focus.

---

**Q11. Which framework’s "Moderate" abstraction level is best for role-based agent collaboration?**  
a) OpenAI Agents SDK  
b) LangGraph  
c) CrewAI (correct)  
d) AutoGen  

**Explanation**: CrewAI’s "Moderate" abstraction and focus on role-based agents and crews make it ideal for collaborative agent systems.

---

**Q12. Which framework integrates seamlessly with Google Cloud’s ecosystem for multi-agent hierarchies?**  
a) OpenAI Agents SDK  
b) Google ADK (correct)  
c) Dapr Agents  
d) LangGraph  

**Explanation**: Google ADK’s "Moderate" abstraction and integration with Google Cloud (e.g., Vertex AI) make it ideal for multi-agent hierarchies in the Google ecosystem.

---

**Q13. What is a key trade-off of using LangGraph for agentic development?**  
a) Its limited control over agent behavior  
b) Its very high learning curve and low simplicity (correct)  
c) Its lack of support for multi-agent systems  
d) Its high abstraction level reducing flexibility  

**Explanation**: LangGraph’s "Very High" learning curve and "Low" simplicity make it complex, despite its high control, posing a trade-off for most projects.

---

**Q14. Which framework is best for developers needing bidirectional streaming for real-time agent interactions?**  
a) OpenAI Agents SDK  
b) CrewAI  
c) Google ADK (correct)  
d) AutoGen  

**Explanation**: Google ADK’s support for bidirectional streaming makes it ideal for real-time agent interactions, a feature not highlighted in OpenAI Agents SDK.

---

**Q15. Why might OpenAI Agents SDK be less ideal for highly complex, distributed systems?**  
a) It lacks support for agent primitives  
b) It has limited enterprise-grade features like data connectors (correct)  
c) It has a high learning curve  
d) It cannot handle structured outputs  

**Explanation**: OpenAI Agents SDK lacks advanced enterprise features like Dapr Agents’ 50+ data connectors, making it less ideal for complex distributed systems.

---

**Q16. Which framework’s "High" abstraction level simplifies conversational agent development but reduces control?**  
a) LangGraph  
b) AutoGen (correct)  
c) OpenAI Agents SDK  
d) Dapr Agents  

**Explanation**: AutoGen’s "High" abstraction simplifies conversational agent development but reduces control compared to OpenAI Agents SDK’s minimal abstraction.

---

**Q17. For a project requiring minimal setup time, which framework is the most accessible?**  
a) LangGraph  
b) Dapr Agents  
c) OpenAI Agents SDK (correct)  
d) Google ADK  

**Explanation**: OpenAI Agents SDK’s "Low" learning curve and "High" simplicity make it the most accessible for minimal setup time.

---

**Q18. Which framework’s event-driven, stateful virtual actors are ideal for distributed multi-agent workflows?**  
a) OpenAI Agents SDK  
b) Dapr Agents (correct)  
c) CrewAI  
d) AutoGen  

**Explanation**: Dapr Agents’ stateful virtual actors and event-driven design make it ideal for distributed multi-agent workflows.

---

**Q19. What makes OpenAI Agents SDK versatile for a wide range of agentic use cases?**  
a) Its focus on graph-based workflows  
b) Its balance of simplicity, control, and minimal abstraction (correct)  
c) Its integration with 50+ data connectors  
d) Its high abstraction for conversational agents  

**Explanation**: OpenAI Agents SDK’s balance of high simplicity, high control, and minimal abstraction makes it versatile for various agentic development scenarios.

---

**Q20. Which framework is least practical for most developers due to its complexity and steep learning curve?**  
a) OpenAI Agents SDK  
b) CrewAI  
c) LangGraph (correct)  
d) Google ADK  

**Explanation**: LangGraph’s "Very High" learning curve and "Low" simplicity make it the least practical for most developers compared to simpler frameworks like OpenAI Agents SDK.


-------------------------------------------------------------------------------------------------------------------------------------
3. # MCQs on Prompt Engineering for Agentic AI Developers
## Questions

**Q1. Why is prompt engineering a critical skill for agentic AI developers?**  
a) It simplifies the agent's hardware requirements  
b) It shapes the agent’s ability to reason, use tools, and achieve goals (correct)  
c) It reduces the need for structured output formats  
d) It eliminates the need for iterative refinement  

**Explanation**: Prompt engineering guides the agent’s reasoning, tool use, and goal achievement, making it essential for effective agentic AI performance.

---

**Q2. What is a key principle of effective prompting for agentic AI?**  
a) Using complex idioms to enhance creativity  
b) Providing clear and specific instructions (correct)  
c) Avoiding structured output formats  
d) Limiting context to reduce processing time  

**Explanation**: Clarity and specificity are foundational principles to ensure the agent understands and executes tasks accurately, avoiding ambiguity.

---

**Q3. Which factor is NOT one of the five critical factors for agentic AI performance?**  
a) Reasoning ability  
b) Tool-calling proficiency  
c) Image generation capability (correct)  
d) Structured output  

**Explanation**: The five critical factors for agentic AI are reasoning ability, tool-calling proficiency, accuracy, cost efficiency, and context size, not image generation.

---

**Q4. What is a benefit of starting with simple prompts for non-native English speakers?**  
a) It increases the complexity of responses  
b) It builds confidence and expertise gradually (correct)  
c) It requires advanced grammar knowledge  
d) It reduces the need for context  

**Explanation**: Simple prompts help non-native speakers build confidence and expertise by focusing on clarity and avoiding complex language challenges.

---

**Q5. How does specifying the audience in a prompt improve its effectiveness?**  
a) It reduces the agent’s processing time  
b) It tailors the response to the appropriate complexity level (correct)  
c) It eliminates the need for structured output  
d) It increases the use of idioms  

**Explanation**: Specifying the audience (e.g., a 10-year-old) ensures the response is tailored to the right complexity, improving clarity for non-native speakers.

---

**Q6. What technique is used in the prompt: "Give me five synonyms for 'happy.' For example, 'joyful' and 'content'”?**  
a) Role assignment  
b) Providing examples (correct)  
c) Step-by-step reasoning  
d) Output priming  

**Explanation**: Providing examples (few-shot prompting) guides the agent to produce the desired output format, enhancing clarity for non-native speakers.

---

**Q7. Which prompt is most effective for a formal email to a colleague?**  
a) "Write an email about a meeting."  
b) "Write a formal email to my colleague inviting them to a meeting next Tuesday at 10 AM." (correct)  
c) "Tell my colleague about a meeting."  
d) "Send an email to my colleague."  

**Explanation**: Specifying "formal" and details like date and time ensures a professional, targeted response, critical for non-native speakers.

---

**Q8. Why is assigning a role like “programming instructor” useful in a prompt?**  
a) It reduces the context size needed  
b) It provides context for authoritative and relevant responses (correct)  
c) It simplifies the output format  
d) It eliminates the need for tools  

**Explanation**: Role assignment gives the agent a specific perspective, improving the relevance and authority of its responses for agentic tasks.

---

**Q9. What is the purpose of specifying gender-neutral language in a prompt?**  
a) To increase response length  
b) To avoid biases and promote inclusivity (correct)  
c) To simplify the agent’s reasoning process  
d) To reduce context size  

**Explanation**: Specifying gender-neutral language prevents biases, ensuring inclusive and ethical responses, important for non-native speakers.

---

**Q10. Which prompt encourages step-by-step reasoning for a logic puzzle?**  
a) "Solve this puzzle: [puzzle description]."  
b) "Solve this puzzle step by step: [puzzle description]." (correct)  
c) "Give me the answer to this puzzle."  
d) "Explain this puzzle quickly."  

**Explanation**: Requesting step-by-step reasoning ensures the agent breaks down the problem logically, improving accuracy and clarity.

---

**Q11. What technique is used in the prompt: "Write a haiku about autumn. Start with 'Leaves falling gently'"?**  
a) Role assignment  
b) Output priming (correct)  
c) Task decomposition  
d) Context management  

**Explanation**: Output priming guides the agent’s response style by providing part of the desired output, enhancing creative control.

---

**Q12. Why is the prompt “Provide a detailed analysis of climate change impacts” effective for agentic AI?**  
a) It minimizes context size  
b) It requests comprehensive reasoning and detailed output (correct)  
c) It avoids specifying tools  
d) It uses complex idioms  

**Explanation**: Requesting a detailed analysis ensures thorough reasoning and comprehensive output, critical for complex agentic tasks.

---

**Q13. How does correcting a prompt like “Please can you telling me what is the capital of France?” improve its effectiveness?**  
a) It adds unnecessary complexity  
b) It simplifies grammar and improves clarity (correct)  
c) It increases context size  
d) It adds role assignment  

**Explanation**: Simplifying grammar (e.g., to “What is the capital of France?”) improves clarity, especially for non-native speakers.

---

**Q14. Why is “What is the current population of Tokyo, Japan?” better than “Tokyo population”?**  
a) It uses more complex language  
b) It is more specific and reduces ambiguity (correct)  
c) It avoids structured output  
d) It requires less reasoning  

**Explanation**: The more specific prompt reduces ambiguity, ensuring an accurate and relevant response, critical for agentic AI.

---

**Q15. What is a key factor for agentic AI prompt engineering?**  
a) Using idioms to enhance creativity  
b) Specifying available tools and their usage (correct)  
c) Avoiding output formatting  
d) Limiting step-by-step reasoning  

**Explanation**: Specifying tools and their usage ensures the agent uses them effectively, optimizing tool-calling proficiency and accuracy.

---

**Q16. Which prompt optimizes cost efficiency for a brief response?**  
a) "Respond to: 'What are AI ethics concerns?' in a concise, professional tone, limit to 50 words." (correct)  
b) "Explain AI ethics in detail."  
c) "Write about AI ethics."  
d) "Discuss AI ethics comprehensively."  

**Explanation**: The word limit and tone specification ensure a concise, cost-efficient response while maintaining accuracy.

---

**Q17. What is the benefit of structuring output as a table in a prompt?**  
a) It increases context size  
b) It enhances clarity and parsability for downstream tasks (correct)  
c) It reduces reasoning ability  
d) It eliminates tool usage  

**Explanation**: Structured output (e.g., a table) improves clarity and makes responses easier to parse, critical for agentic systems.

---

**Q18. Which prompt best tests an agent’s tool-calling proficiency?**  
a) "Get the weather for London."  
b) "Use the weather API tool to get the current weather in London, UK. Return the temperature and condition." (correct)  
c) "Tell me about London’s weather."  
d) "Find weather information."  

**Explanation**: Explicitly naming the tool and specifying output ensures effective tool use and accurate results.

---

**Q19. Why is “Act as a data analyst” effective in a prompt for agentic AI?**  
a) It reduces context size  
b) It enhances reasoning by providing a specific role (correct)  
c) It eliminates the need for structured output  
d) It avoids tool usage  

**Explanation**: Role assignment enhances reasoning by giving the agent a clear perspective, improving relevance and accuracy.

---

**Q20. What is a key consideration for non-native English speakers when writing prompts?**  
a) Using complex idioms to sound natural  
b) Avoiding idioms and using simple language (correct)  
c) Increasing context size unnecessarily  
d) Avoiding structured output  

**Explanation**: Simple language and avoiding idioms ensure clarity, making prompts accessible for non-native speakers.

---

**Q21. Which prompt encourages task decomposition for a marketing campaign?**  
a) "Plan a marketing campaign."  
b) "Create a marketing campaign plan, breaking it into audience, channels, messaging, timeline, and KPIs." (correct)  
c) "Write about marketing."  
d) "Plan a campaign quickly."  

**Explanation**: Task decomposition breaks the goal into manageable steps, improving reasoning and clarity for agentic AI.

---

**Q22. What is the purpose of specifying constraints in an agentic prompt?**  
a) To increase response length  
b) To set boundaries for the agent’s actions (correct)  
c) To reduce reasoning ability  
d) To eliminate context  

**Explanation**: Constraints (e.g., “use only peer-reviewed sources”) ensure the agent operates within defined boundaries, enhancing accuracy.

---

**Q23. Which prompt best ensures structured output for a product list?**  
a) "List some products."  
b) "List three products in a table with columns 'Name' and 'Description.' Example: | Name | Description |" (correct)  
c) "Tell me about products."  
d) "Describe products briefly."  

**Explanation**: Providing a table format and example ensures structured, parsable output, critical for agentic systems.

---

**Q24. Why is “Before using any tool, state your reasoning” effective in a prompt?**  
a) It reduces tool-calling proficiency  
b) It encourages transparent reasoning for debugging (correct)  
c) It increases context size unnecessarily  
d) It eliminates structured output  

**Explanation**: Requiring reasoning transparency aids debugging and ensures logical tool use, enhancing accuracy.

---

**Q25. Which prompt is best for a travel planning agent?**  
a) "Plan a trip to Paris."  
b) "As a travel planner, create a 3-day Paris itinerary for art and history, using map and museum tools, in Markdown." (correct)  
c) "Tell me about Paris travel."  
d) "Plan a Paris vacation."  

**Explanation**: Specifying the role, tools, and output format ensures a detailed, actionable itinerary, optimizing all five factors.

---

**Q26. What is a benefit of few-shot prompting in agentic AI?**  
a) It reduces the need for tools  
b) It guides the agent with example input-output pairs (correct)  
c) It eliminates the need for context  
d) It increases response length  

**Explanation**: Few-shot prompting provides examples to guide the agent’s output, improving accuracy and clarity.

---

**Q27. Which prompt corrects “Use tool get data about sales fast”?**  
a) "Use the sales data tool to retrieve sales figures for March 2025. Return results quickly in a list." (correct)  
b) "Get sales data quickly."  
c) "Use tool for sales."  
d) "Find sales information fast."  

**Explanation**: The corrected prompt specifies the tool, time period, and output format, improving clarity and tool-calling proficiency.

---

**Q28. Why is context size important in agentic AI prompts?**  
a) It reduces the need for reasoning  
b) It allows the agent to handle large datasets or histories (correct)  
c) It eliminates structured output  
d) It increases response latency  

**Explanation**: Large context size enables agents to process extensive data, critical for complex tasks like campaign planning.

---

**Q29. Which prompt best supports debugging a Python function?**  
a) "Fix this code: [code]."  
b) "Analyze this Python function for errors using a code analyzer tool, explain the bug, and provide corrected code." (correct)  
c) "Debug this code quickly."  
d) "Tell me about code errors."  

**Explanation**: Specifying the tool, error analysis, and corrected output ensures thorough debugging, enhancing accuracy.

---

**Q30. What is a drawback of overly vague prompts in agentic AI?**  
a) They improve cost efficiency  
b) They risk ambiguous or inaccurate responses (correct)  
c) They reduce context size  
d) They enhance tool usage  

**Explanation**: Vague prompts lead to ambiguous responses, reducing accuracy and effectiveness in agentic tasks.

---

**Q31. Which prompt optimizes reasoning for a complex task?**  
a) "Solve this problem."  
b) "Solve this problem step by step, explaining your reasoning: [problem description]." (correct)  
c) "Give me the answer to this problem."  
d) "Explain this problem briefly."  

**Explanation**: Requiring step-by-step reasoning ensures logical processing, critical for complex agentic tasks.

---

**Q32. What is the role of guardrails in an agentic prompt?**  
a) To increase response complexity  
b) To define rules and limitations for the agent (correct)  
c) To reduce the need for tools  
d) To eliminate output formatting  

**Explanation**: Guardrails set boundaries (e.g., “avoid blog posts”) to ensure the agent operates within desired limits, improving accuracy.

---

**Q33. Which prompt ensures cost efficiency for a summary task?**  
a) "Summarize this article in 100 words: [article text]. Focus on key points only." (correct)  
b) "Summarize this article in detail."  
c) "Write about this article."  
d) "Provide a comprehensive article summary."  

**Explanation**: Limiting the summary to 100 words and focusing on key points ensures cost efficiency and accuracy.

---

**Q34. Why is JSON output useful for agentic AI?**  
a) It reduces reasoning ability  
b) It provides machine-readable, structured responses (correct)  
c) It increases context size unnecessarily  
d) It avoids tool usage  

**Explanation**: JSON output is structured and parsable, ideal for agentic systems integrating with other tools or systems.

---

**Q35. Which prompt best specifies tool usage for a weather task?**  
a) "Get the weather."  
b) "Use the weather API tool to get the current weather in London, UK. Return temperature and condition in JSON." (correct)  
c) "Tell me about the weather."  
d) "Find weather data."  

**Explanation**: Specifying the tool and JSON output ensures effective tool use and structured, accurate results.

---

**Q36. What is a benefit of self-correction prompts in agentic AI?**  
a) They reduce the need for context  
b) They encourage the agent to review and refine its work (correct)  
c) They eliminate structured output  
d) They increase response latency  

**Explanation**: Self-correction prompts improve accuracy by encouraging the agent to review its work for errors or inconsistencies.

---

**Q37. Which prompt is best for a non-native speaker to get a simple definition?**  
a) "What is machine learning?" (correct)  
b) "Please explain machine learning in detail."  
c) "Tell me about machine learning comprehensively."  
d) "Define machine learning with examples."  

**Explanation**: The simple, direct prompt avoids complexity, making it ideal for non-native speakers seeking clarity.

---

**Q38. Why is “Think step by step” effective for agentic AI prompts?**  
a) It reduces tool-calling proficiency  
b) It enhances reasoning transparency and accuracy (correct)  
c) It increases context size unnecessarily  
d) It avoids structured output  

**Explanation**: Step-by-step thinking improves reasoning transparency, helping debug and ensure accurate agentic performance.

---

**Q39. Which prompt best manages context size for a dataset analysis?**  
a) "Analyze this dataset: [dataset]."  
b) "Analyze trends in this dataset using the stats tool: [dataset]. Limit to top 3 trends in a table, keeping context under 500 tokens." (correct)  
c) "Tell me about dataset trends."  
d) "Find dataset insights."  

**Explanation**: Limiting trends and context size ensures efficient processing, optimizing reasoning, accuracy, and cost.

---

**Q40. What is a key tip for non-native English speakers writing agentic prompts?**  
a) Use complex sentence structures  
b) Double-check prompts for grammatical errors (correct)  
c) Include idioms for natural language  
d) Avoid specifying output formats  

**Explanation**: Double-checking grammar ensures clarity and effectiveness, critical for non-native speakers crafting agentic prompts.
