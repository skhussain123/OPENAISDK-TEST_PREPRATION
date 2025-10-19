# 300 MCQs on Prompt Engineering, Context Engineering, MoE, AI Image Generation (Theory & Practical)

Below is a comprehensive set of 300 multiple-choice questions (MCQs) based on the provided study material. The questions are categorized to cover all key sections: Fundamentals (1-40), Configuration Settings (41-70), Prompting Techniques (71-120), Best Practices & Pitfalls (121-160), Testing and Evaluation (161-190), Advanced Techniques (191-220), MoE & Prompting (221-260), Practical Applications (261-280), Context Engineering Integration (281-310), 6-Step Framework (311-340), and AI Image Generation (Nano Banana) (341-370). Note that the numbering is continuous from 1 to 300, but categories are labeled for reference. Each MCQ includes the question, options, correct answer, and a short explanation. Theory questions focus on concepts, while practical ones involve applying techniques or identifying examples.

## Fundamentals (MCQs 1-40)

### MCQ 1 (Theory)
**Question:** What is the primary goal of prompt engineering?  
A. Providing external data for grounding  
B. Crafting clear instructions for desired outputs  
C. Managing the context window  
D. Optimizing token budgets  

**Answer:** B  
**Short Explanation:** Prompt engineering focuses on crafting instructions to elicit specific outputs from LLMs.

### MCQ 2 (Theory)
**Question:** How do LLMs work as prediction engines?  
A. By understanding human intent  
B. By guessing next tokens based on patterns  
C. By storing complete datasets  
D. By reasoning like humans  

**Answer:** B  
**Short Explanation:** LLMs predict the next token based on learned patterns from training data.

### MCQ 3 (Practical)
**Question:** If an LLM generates fabricated information due to missing context, what failure mode is this?  
A. Messy outputs  
B. Hallucinations  
C. Context rot  
D. Routing instability  

**Answer:** B  
**Short Explanation:** Hallucinations occur when LLMs invent information due to insufficient context, as seen in vague prompts like "Tell me about future events."

### MCQ 4 (Theory)
**Question:** What is the recommended workflow for combining prompt and context engineering?  
A. Ground with context first, then prompt  
B. Prompt first, then ground with context  
C. Use only context  
D. Avoid prompts  

**Answer:** B  
**Short Explanation:** Start with a prompt to guide behavior, then add context for grounding, as in combining instructions with retrieved data.

### MCQ 5 (Theory)
**Question:** How are LLMs best viewed?  
A. As human-like understanding systems  
B. As sophisticated autocomplete systems  
C. As database retrieval engines  
D. As rule-based logic processors  

**Answer:** B  
**Short Explanation:** LLMs function as advanced autocomplete, predicting tokens based on patterns.

### MCQ 6 (Practical)
**Question:** In a prompt like "Write about AI," what failure mode is likely?  
A. Hallucinations from missing info  
B. Messy outputs from vague instructions  
C. Overloading constraints  
D. Ignoring token limits  

**Answer:** B  
**Short Explanation:** Vague prompts lead to disorganized or irrelevant outputs, as the AI lacks clear direction.

### MCQ 7 (Theory)
**Question:** What is the main difference between prompt engineering and context engineering?  
A. Prompt is more comprehensive  
B. Context is for conversational interactions  
C. Prompt crafts instructions, context provides grounding facts  
D. Context is only for agents  

**Answer:** C  
**Short Explanation:** Prompt engineering focuses on instructions for behavior, while context engineering supplies knowledge for accuracy.

### MCQ 8 (Theory)
**Question:** In the quick contrast table, what is the goal of prompt engineering?  
A. Give facts/examples to rely on  
B. Tell the model how to behave and what to produce  
C. Manage retrieval pipelines  
D. Optimize chunking  

**Answer:** B  
**Short Explanation:** Prompt engineering guides AI behavior and output production.

### MCQ 9 (Practical)
**Question:** For an invoice JSON extractor, what is an example of prompt engineering?  
A. Attach policy PDF  
B. “Extract fields {vendor, date, total}. Return JSON only”  
C. Use RAG over policy repo  
D. Feed tool responses back  

**Answer:** B  
**Short Explanation:** Prompt engineering defines the extraction instructions and output format.

### MCQ 10 (Theory)
**Question:** In the burger analogy for AI agents, what is the LLM?  
A. Bun  
B. Patty  
C. Vegetables  
D. CPU  

**Answer:** D  
**Short Explanation:** LLM is the CPU, processing the context window as RAM.

### MCQ 11 (Theory)
**Question:** What is context engineering's focus compared to prompt engineering?  
A. Single instructions  
B. Overall setup and info  
C. Conversational refinement  
D. Iterative questions  

**Answer:** B  
**Short Explanation:** Context engineering curates the entire setup, while prompt engineering is more focused on instructions.

### MCQ 12 (Practical)
**Question:** In the <Context> example for an AI email assistant, what is the model?  
A. gpt-5  
B. Gemini  
C. Claude  
D. Grok  

**Answer:** A  
**Short Explanation:** The example specifies "model: gpt-5" for the email agent.

### MCQ 13 (Theory)
**Question:** What is a failure mode of vague instructions?  
A. Accurate outputs  
B. Messy/incorrect format  
C. Hallucinations  
D. Overloaded context  

**Answer:** B  
**Short Explanation:** Vague instructions lead to messy outputs, as in the invoice extractor example.

### MCQ 14 (Theory)
**Question:** What is the goal of context engineering in the quick contrast table?  
A. Tell how to behave  
B. Give facts/examples to rely on  
C. Wording and structure  
D. Retrieval pipelines  

**Answer:** B  
**Short Explanation:** Context engineering supplies knowledge, while prompt engineering guides behavior.

### MCQ 15 (Practical)
**Question:** For a policy Q&A bot, what is an example of context engineering?  
A. “Be concise. Return JSON”  
B. RAG over policy repo with chunking  
C. Tool-use instructions  
D. Extract fields {vendor, date}  

**Answer:** B  
**Short Explanation:** Context engineering involves RAG with chunking, metadata filters, and freshness boosts.

### MCQ 16 (Theory)
**Question:** How do prompts and context work together?  
A. Prompts replace context  
B. Context guides behavior, prompts supply knowledge  
C. Prompts guide behavior, context supplies knowledge  
D. Both are the same  

**Answer:** C  
**Short Explanation:** Prompts control how the AI behaves, while context provides the facts for accurate responses.

### MCQ 17 (Practical)
**Question:** In an agentic workflow, what is prompt engineering?  
A. Feed tool responses back  
B. RAG over policy repo  
C. Tool-use instructions and function signatures  
D. Attach policy PDF  

**Answer:** C  
**Short Explanation:** Prompt engineering defines tool-use instructions, while context engineering feeds tool responses back.

### MCQ 18 (Theory)
**Question:** What is a practical tip for context optimization?  
A. Use vague instructions  
B. Keep prompts short and testable  
C. Avoid citations  
D. Ignore token budgets  

**Answer:** B  
**Short Explanation:** Short, specific prompts with output schemas are recommended.

### MCQ 19 (Practical)
**Question:** What is an example of combining prompts and context for an invoice extractor?  
A. “Answer using attached passages”  
B. Provide labeled examples and invoice spec via embeddings  
C. “Be concise”  
D. Use RAG over policy repo  

**Answer:** B  
**Short Explanation:** Context engineering attaches examples and specs, while prompt defines extraction.

### MCQ 20 (Theory)
**Question:** What is the one-liner for prompt vs. context engineering?  
A. Prompt is what you show; context is how you ask  
B. Prompt is how you ask; context is what you show  
C. Both are the same  
D. Prompt is for knowledge  

**Answer:** B  
**Short Explanation:** Prompt engineering is how you ask; context engineering is what you show for reliable apps.

### MCQ 21 (Theory)
**Question:** What is the core challenge in context engineering?  
A. Unlimited attention  
B. Limited attention and context rot  
C. Infinite token budgets  
D. No routing  

**Answer:** B  
**Short Explanation:** LLMs experience context rot as token count increases due to attention limits.

### MCQ 22 (Theory)
**Question:** What is the "Goldilocks zone" for system prompts?  
A. Overly complex  
B. Vague philosophy  
C. Specific but flexible heuristics  
D. No prompt  

**Answer:** C  
**Short Explanation:** System prompts should be specific enough to guide but flexible to avoid brittleness.

### MCQ 23 (Practical)
**Question:** For tool management in context engineering, what should tools use judiciously?  
A. Unlimited tokens  
B. Pagination and filtering  
C. Full documents  
D. No defaults  

**Answer:** B  
**Short Explanation:** Tools should use pagination, filtering, and truncation to minimize token consumption.

### MCQ 24 (Theory)
**Question:** What is strategic context curation's goal?  
A. Maximize tokens  
B. Smallest high-signal token set  
C. Vague inputs  
D. Full history  

**Answer:** B  
**Short Explanation:** Find the smallest set of high-signal tokens for desired outcomes.

### MCQ 25 (Practical)
**Question:** In retrieval for agents, what beats stuffing?  
A. Pre-inference RAG only  
B. Just-in-time retrieval via tools  
C. No retrieval  
D. Full document loading  

**Answer:** B  
**Short Explanation:** Keep lightweight references and load details at runtime for efficiency.

### MCQ 26 (Theory)
**Question:** What is context rot?  
A. Unlimited recall  
B. Degraded recall as tokens increase  
C. Infinite windows  
D. No attention issues  

**Answer:** B  
**Short Explanation:** Performance drops with more tokens due to attention scaling.

### MCQ 27 (Practical)
**Question:** For long-horizon work, what tactic is used for compaction?  
A. Keep all history  
B. Periodically summarize trace  
C. No pruning  
D. Increase tokens  

**Answer:** B  
**Short Explanation:** Summarize and restart with distilled state to manage context.

### MCQ 28 (Theory)
**Question:** What is agentic memory?  
A. No notes  
B. Structured note-taking outside context  
C. Full history  
D. No persistence  

**Answer:** B  
**Short Explanation:** Persist notes (e.g., TODOs) and re-inject later for long tasks.

### MCQ 29 (Practical)
**Question:** What do sub-agent architectures do?  
A. Mix all tasks  
B. Specialized workers return digests to coordinator  
C. No separation  
D. Increase latency  

**Answer:** B  
**Short Explanation:** Clean separation of concerns for deep dives in complex tasks.

### MCQ 30 (Theory)
**Question:** What is the operating principle for context?  
A. Use maximum tokens  
B. Do the simplest thing that works  
C. Complex logic always  
D. No management  

**Answer:** B  
**Short Explanation:** Treat context as precious and manage deliberately.

### MCQ 31 (Theory)
**Question:** In the Nano Banana core principles, what is specificity over generality?  
A. Vague prompts  
B. Detailed descriptions for better outputs  
C. Generic terms  
D. No hierarchy  

**Answer:** B  
**Short Explanation:** Specific prompts (e.g., "hyper-realistic portrait") lead to better matches than vague ones.

### MCQ 32 (Practical)
**Question:** What is the visual hierarchy in Nano Banana prompts?  
A. Lighting first  
B. Subject → environment → lighting → technical  
C. Mood first  
D. Style last  

**Answer:** B  
**Short Explanation:** Start with subject, add environment, lighting, then technical details for structured prompts.

### MCQ 33 (Theory)
**Question:** What is professional photography language in Nano Banana?  
A. Vague terms  
B. Camera terminology, lighting setups, styles  
C. No technical details  
D. Generic descriptions  

**Answer:** B  
**Short Explanation:** Use terms like "85mm lens, Rembrandt lighting" for realism.

### MCQ 34 (Practical)
**Question:** What is the first element in the anatomy of effective image prompts?  
A. Lighting  
B. Subject description  
C. Mood  
D. Technical specs  

**Answer:** B  
**Short Explanation:** Start with who/what the subject is, e.g., "confident man in suit."

### MCQ 35 (Theory)
**Question:** What does f/1.4 aperture do?  
A. Deep focus  
B. Shallow depth of field  
C. Wide angle  
D. High contrast  

**Answer:** B  
**Short Explanation:** f/1.4 creates shallow depth, blurring background for subject isolation.

### MCQ 36 (Practical)
**Question:** What is Rembrandt lighting?  
A. Flat light  
B. Small triangle of light on face  
C. Harsh direct light  
D. Backlight  

**Answer:** B  
**Short Explanation:** Rembrandt creates dramatic shadows with a triangle of light on the cheek.

### MCQ 37 (Theory)
**Question:** What is a best practice for Nano Banana prompts?  
A. Vague descriptions  
B. Anchor subject with "of the uploaded photo"  
C. No environment cues  
D. Conflicting styles  

**Answer:** B  
**Short Explanation:** Anchoring ensures consistency with uploaded images.

### MCQ 38 (Practical)
**Question:** What is corporate style in Nano Banana?  
A. Artistic and moody  
B. Executive portraits, headshots, LinkedIn profiles  
C. High fashion  
D. Authentic moments  

**Answer:** B  
**Short Explanation:** Corporate focuses on professional, clean headshots for business use.

### MCQ 39 (Theory)
**Question:** What is a common mistake in Nano Banana prompts?  
A. Specific lighting  
B. Being too vague  
C. Using examples  
D. Defining mood  

**Answer:** B  
**Short Explanation:** Vague prompts like "nice portrait" lead to generic outputs.

### MCQ 40 (Practical)
**Question:** What is in the quality control checklist for Nano Banana?  
A. Vague subject  
B. Lighting type and direction specified  
C. No technical specs  
D. Conflicting elements  

**Answer:** B  
**Short Explanation:** Checklist ensures lighting is specified for clear outputs.

## Configuration Settings (MCQs 41-70)

### MCQ 41 (Theory)
**Question:** What does temperature control in LLMs?  
A. Output length  
B. Randomness/creativity  
C. Token limit  
D. Model selection  

**Answer:** B  
**Short Explanation:** Low temperature (0-0.3) for consistency, high (0.8-1) for creativity.

### MCQ 42 (Practical)
**Question:** For math problems, what temperature is recommended?  
A. 0.9  
B. 0  
C. 0.7  
D. 1.0  

**Answer:** B  
**Short Explanation:** Temperature 0 ensures deterministic, consistent responses for factual tasks.

### MCQ 43 (Theory)
**Question:** What is top-K sampling?  
A. Cumulative probability threshold  
B. Limits to top likely tokens  
C. Output length control  
D. Context window size  

**Answer:** B  
**Short Explanation:** Top-K limits predictions to the top K most likely tokens.

### MCQ 44 (Practical)
**Question:** What is a balanced configuration starting point?  
A. Temp 0.1, Top-P 0.9, Top-K 20  
B. Temp 0.2, Top-P 0.95, Top-K 30  
C. Temp 0.9, Top-P 0.99, Top-K 40  
D. Temp 0, Top-P 1, Top-K 10  

**Answer:** B  
**Short Explanation:** Balanced for general tasks with creativity and consistency.

### MCQ 45 (Theory)
**Question:** What do output/token limits affect?  
A. Randomness  
B. Length and cost  
C. Expert selection  
D. Context rot  

**Answer:** B  
**Short Explanation:** Token limits control response length and computational cost.

### MCQ 46 (Practical)
**Question:** For creative writing, what configuration is best?  
A. Temp 0.1, Top-P 0.9, Top-K 20  
B. Temp 0.2, Top-P 0.95, Top-K 30  
C. Temp 0.9, Top-P 0.99, Top-K 40  
D. Temp 0, Top-P 0.9, Top-K 10  

**Answer:** C  
**Short Explanation:** High values encourage diverse, creative outputs.

### MCQ 47 (Theory)
**Question:** What is top-P (nucleus sampling)?  
A. Limits to top K tokens  
B. Cumulative probability threshold  
C. Temperature control  
D. Token budget  

**Answer:** B  
**Short Explanation:** Top-P includes tokens until cumulative probability reaches P.

### MCQ 48 (Practical)
**Question:** What configuration is conservative?  
A. Temp 0.9, Top-P 0.99, Top-K 40  
B. Temp 0.1, Top-P 0.9, Top-K 20  
C. Temp 0.7, Top-P 0.95, Top-K 30  
D. Temp 1.0, Top-P 1, Top-K 50  

**Answer:** B  
**Short Explanation:** Low values for focused, deterministic responses in factual tasks.

### MCQ 49 (Theory)
**Question:** When to use temperature 0.7?  
A. Math problems  
B. Factual questions  
C. Creative writing  
D. Code generation  

**Answer:** C  
**Short Explanation:** Medium temperature balances creativity and consistency for writing.

### MCQ 50 (Practical)
**Question:** If outputs are too random, what should you adjust?  
A. Increase temperature  
B. Decrease temperature  
C. Increase Top-K  
D. Decrease Top-P  

**Answer:** B  
**Short Explanation:** Lower temperature reduces randomness for more consistent outputs.

### MCQ 51 (Theory)
**Question:** What do top-K and top-P work with?  
A. Token limits  
B. Temperature to control randomness  
C. Context window  
D. Expert routing  

**Answer:** B  
**Short Explanation:** They combine with temperature to balance quality and diversity.

### MCQ 52 (Practical)
**Question:** For poetry, what temperature is recommended?  
A. 0  
B. 0.3  
C. 0.9  
D. 0.5  

**Answer:** C  
**Short Explanation:** High temperature 0.9 encourages creative, diverse outputs.

### MCQ 53 (Theory)
**Question:** What is a recommended starting point for balanced configs?  
A. Temp 0.1, Top-P 0.9, Top-K 20  
B. Temp 0.2, Top-P 0.95, Top-K 30  
C. Temp 0.9, Top-P 0.99, Top-K 40  
D. Temp 0, Top-P 1, Top-K 10  

**Answer:** B  
**Short Explanation:** Balanced for general tasks like brainstorming.

### MCQ 54 (Practical)
**Question:** If responses are cut off, what setting to adjust?  
A. Temperature  
B. Top-P  
C. Token limits  
D. Top-K  

**Answer:** C  
**Short Explanation:** Increase token limits to allow longer responses.

### MCQ 55 (Theory)
**Question:** What is temperature 0 for?  
A. Creative tasks  
B. Math and factual questions  
C. Storytelling  
D. Image generation  

**Answer:** B  
**Short Explanation:** Ensures deterministic, consistent responses.

### MCQ 56 (Practical)
**Question:** What configuration for experimental content?  
A. Temp 0.9  
B. Temp 0.1  
C. Temp 0.2  
D. Temp 0  

**Answer:** A  
**Short Explanation:** High temperature 0.9 for diverse, unpredictable outputs.

### MCQ 57 (Theory)
**Question:** What does high Top-K do?  
A. More focused outputs  
B. More diversity  
C. Reduce cost  
D. Increase accuracy  

**Answer:** B  
**Short Explanation:** Larger Top-K allows more token options for diversity.

### MCQ 58 (Practical)
**Question:** For focused responses, what Top-P value?  
A. 0.99  
B. 0.9  
C. 1.0  
D. 0.5  

**Answer:** B  
**Short Explanation:** Top-P 0.9 limits to likely tokens for focus.

### MCQ 59 (Theory)
**Question:** What affects computational cost?  
A. Temperature  
B. Higher token limits  
C. Top-K  
D. Top-P  

**Answer:** B  
**Short Explanation:** Larger limits increase processing and cost.

### MCQ 60 (Practical)
**Question:** What is a creative configuration?  
A. Temp 0.1, Top-P 0.9, Top-K 20  
B. Temp 0.9, Top-P 0.99, Top-K 40  
C. Temp 0.2, Top-P 0.95, Top-K 30  
D. Temp 0, Top-P 0.9, Top-K 10  

**Answer:** B  
**Short Explanation:** High values for poetry or brainstorming.

### MCQ 61 (Theory)
**Question:** What is temperature's range?  
A. 0-10  
B. 0-1  
C. 1-100  
D. -1-1  

**Answer:** B  
**Short Explanation:** Temperature ranges from 0 (deterministic) to 1 (creative).

### MCQ 62 (Practical)
**Question:** For a balanced brainstorming task, what config?  
A. Temp 0.9, Top-P 0.99, Top-K 40  
B. Temp 0.2, Top-P 0.95, Top-K 30  
C. Temp 0.1, Top-P 0.9, Top-K 20  
D. Temp 0, Top-P 1, Top-K 10  

**Answer:** B  
**Short Explanation:** Medium values for balance between creativity and consistency.

### MCQ 63 (Theory)
**Question:** What is nucleus sampling?  
A. Top-K  
B. Top-P  
C. Temperature  
D. Token limit  

**Answer:** B  
**Short Explanation:** Top-P uses cumulative probability for dynamic selection.

### MCQ 64 (Practical)
**Question:** If outputs are too predictable, what to increase?  
A. Temperature  
B. Token limit  
C. Top-K  
D. All of above  

**Answer:** A  
**Short Explanation:** Higher temperature adds randomness for variety.

### MCQ 65 (Theory)
**Question:** What is conservative config for factual questions?  
A. Temp 0.9, Top-P 0.99, Top-K 40  
B. Temp 0.1, Top-P 0.9, Top-K 20  
C. Temp 0.7, Top-P 0.95, Top-K 30  
D. Temp 1.0, Top-P 1, Top-K 50  

**Answer:** B  
**Short Explanation:** Low values for focused, deterministic responses.

### MCQ 66 (Practical)
**Question:** For a task requiring diversity, what Top-P value?  
A. 0.9  
B. 0.99  
C. 0.5  
D. 0  

**Answer:** B  
**Short Explanation:** High Top-P 0.99 allows more token options for diversity.

### MCQ 67 (Theory)
**Question:** What does token limit control?  
A. Randomness  
B. Maximum response length  
C. Expert selection  
D. Context rot  

**Answer:** B  
**Short Explanation:** Prevents cut-off responses and manages cost.

### MCQ 68 (Practical)
**Question:** If outputs are inconsistent, what to lower?  
A. Temperature  
B. Token limit  
C. Top-K  
D. Top-P  

**Answer:** A  
**Short Explanation:** Lower temperature reduces randomness for consistency.

### MCQ 69 (Theory)
**Question:** What is the purpose of Top-K?  
A. Probability threshold  
B. Limit to top likely tokens  
C. Length control  
D. Model choice  

**Answer:** B  
**Short Explanation:** Restricts predictions to top K tokens.

### MCQ 70 (Practical)
**Question:** For experimental poetry, what config?  
A. Temp 0.1, Top-P 0.9, Top-K 20  
B. Temp 0.2, Top-P 0.95, Top-K 30  
C. Temp 0.9, Top-P 0.99, Top-K 40  
D. Temp 0, Top-P 0.9, Top-K 10  

**Answer:** C  
**Short Explanation:** Creative config for diverse outputs.

## Prompting Techniques (MCQs 71-120)

### MCQ 71 (Theory)
**Question:** What is zero-shot prompting?  
A. Multiple examples  
B. Direct question without examples  
C. One example  
D. Role assignment  

**Answer:** B  
**Short Explanation:** Simple direct ask using model's general knowledge.

### MCQ 72 (Practical)
**Question:** Example of zero-shot?  
A. Translate with 3 examples  
B. Classify review as positive/negative  
C. One translation example  
D. "Act as a doctor"  

**Answer:** B  
**Short Explanation:** "Classify this review: 'Great product'" is direct without examples.

### MCQ 73 (Theory)
**Question:** How many examples in few-shot prompting?  
A. 1  
B. 3-5  
C. 0  
D. 10  

**Answer:** B  
**Answer:** B  
**Short Explanation:** 3-5 examples establish patterns for tasks like classification.

### MCQ 74 (Practical)
**Question:** Example of one-shot?  
A. No examples  
B. Translate with one example pair  
C. 3-5 examples  
D. Step-by-step reasoning  

**Answer:** B  
**Short Explanation:** "English: Hello → French: Bonjour. English: Goodbye → ?" guides format.

### MCQ 75 (Theory)
**Question:** When to use few-shot?  
A. Simple tasks  
B. When model has domain knowledge  
C. For patterns in complex tasks  
D. No examples needed  

**Answer:** C  
**Short Explanation:** Multiple examples for establishing clear patterns in structured tasks.

### MCQ 76 (Practical)
**Question:** What is role prompting?  
A. Step-by-step reasoning  
B. Assign persona to AI  
C. Multiple paths  
D. General question first  

**Answer:** B  
**Short Explanation:** "Act as a financial advisor" for expert-level responses.

### MCQ 77 (Theory)
**Question:** What is system prompting?  
A. Assign character  
B. Set behavior guidelines  
C. Provide background  
D. Multiple examples  

**Answer:** B  
**Short Explanation:** Overall context and rules, like "Always include key attractions."

### MCQ 78 (Practical)
**Question:** Example of contextual prompting?  
A. Direct question  
B. Provide background info  
C. One example  
D. Role assignment  

**Answer:** B  
**Short Explanation:** "Context: For beginners. Explain API in 200 words."

### MCQ 79 (Theory)
**Question:** What does CoT prompting encourage?  
A. Direct answers  
B. Step-by-step reasoning  
C. Multiple paths  
D. Tool use  

**Answer:** B  
**Short Explanation:** "Let's think step by step" for complex problems.

### MCQ 80 (Practical)
**Question:** When to use CoT?  
A. Simple tasks  
B. Math/logical reasoning  
C. Image generation  
D. No examples  

**Answer:** B  
**Short Explanation:** "Solve: If I was 6 when sister was half my age, her age when I'm 40?"

### MCQ 81 (Theory)
**Question:** What is Self-Consistency?  
A. Single path  
B. Multiple paths, pick common answer  
C. General question first  
D. Reasoning + actions  

**Answer:** B  
**Short Explanation:** Generate multiple answers and select the most frequent for reliability.

### MCQ 82 (Practical)
**Question:** Example of Self-Consistency?  
A. Direct classification  
B. 3 paths for discount calculation, pick $40  
C. Role assignment  
D. One example  

**Answer:** B  
**Short Explanation:** Multiple reasoning for "20% discount on $50" yields consistent $40.

### MCQ 83 (Theory)
**Question:** What is Step-Back prompting?  
A. Multiple branches  
B. General question first  
C. Reasoning + actions  
D. Step-by-step  

**Answer:** B  
**Short Explanation:** Broader question for context, then specific task.

### MCQ 84 (Practical)
**Question:** Example of Step-Back?  
A. Direct math solve  
B. "UI principles?" then redesign screen  
C. Multiple paths  
D. Tool call  

**Answer:** B  
**Short Explanation:** General UI principles before specific redesign.

### MCQ 85 (Theory)
**Question:** What is ReAct?  
A. Step-by-step reasoning  
B. Reasoning + actions/tools  
C. Branching decisions  
D. General first  

**Answer:** B  
**Short Explanation:** Interleave thinking (thought) with actions (e.g., search).

### MCQ 86 (Practical)
**Question:** Example of ReAct?  
A. Direct answer  
B. Thought: Need population; Action: web_search Tokyo  
C. Multiple examples  
D. Role prompt  

**Answer:** B  
**Short Explanation:** "Thought: Search population; Action: web_search" for comparison.

### MCQ 87 (Theory)
**Question:** What is Tree of Thoughts (ToT)?  
A. Linear reasoning  
B. Branching for complex decisions  
C. Tool use  
D. General question  

**Answer:** B  
**Short Explanation:** Multiple reasoning branches with pros/cons and scores.

### MCQ 88 (Practical)
**Question:** Example of ToT?  
A. Direct solve  
B. 3 marketing branches, select best  
C. One example  
D. Role assignment  

**Answer:** B  
**Short Explanation:** Branches for social media, events, partnerships; synthesis best strategy.

### MCQ 89 (Theory)
**Question:** Tip for CoT?  
A. High temp  
B. "Let's think step by step" with temp=0  
C. No examples  
D. Vague prompt  

**Answer:** B  
**Short Explanation:** Low temp for consistent reasoning in CoT.

### MCQ 90 (Practical)
**Question:** When to use ReAct?  
A. Simple classification  
B. Tasks needing tools/search  
C. Single path  
D. No actions  

**Answer:** B  
**Short Explanation:** For multi-step with external data, like population comparison.

### MCQ 91 (Theory)
**Question:** What to use for creative problem-solving?  
A. Zero-shot  
B. ToT  
C. One-shot  
D. System prompt  

**Answer:** B  
**Short Explanation:** ToT for exploring alternatives in complex decisions.

### MCQ 92 (Practical)
**Question:** Example of system prompting?  
A. Direct question  
B. "Always include key attractions" for travel guide  
C. One example  
D. Multiple paths  

**Answer:** B  
**Short Explanation:** Guidelines for consistent behavior in responses.

### MCQ 93 (Theory)
**Question:** What is one-shot for?  
A. No examples  
B. Single example to guide format  
C. 3-5 examples  
D. Branching  

**Answer:** B  
**Short Explanation:** One example to establish pattern, like translation pair.

### MCQ 94 (Practical)
**Question:** When to use few-shot?  
A. When model knows domain  
B. For patterns in classification  
C. For math  
D. No examples needed  

**Answer:** B  
**Short Explanation:** 3-5 examples for tasks like feedback to JSON.

### MCQ 95 (Theory)
**Question:** What is role prompting for?  
A. Background info  
B. Assign expertise  
C. Step-by-step  
D. Tool use  

**Answer:** B  
**Short Explanation:** "Act as software architect" for expert responses.

### MCQ 96 (Practical)
**Question:** Example of contextual prompting?  
A. "Classify review"  
B. "Context: For beginners. Explain API"  
C. Multiple paths  
D. "Think step by step"  

**Answer:** B  
**Short Explanation:** Background (beginners) for tailored explanation.

### MCQ 97 (Theory)
**Question:** What is Self-Consistency process?  
A. Single answer  
B. Ask same question multiple times, pick common  
C. General first  
D. Actions with reasoning  

**Answer:** B  
**Short Explanation:** Multiple phrasings for consistent result.

### MCQ 98 (Practical)
**Question:** Example of Step-Back?  
A. Direct "Optimize website"  
B. "Factors for speed?" then specific recommendations  
C. Branching  
D. Tool call  

**Answer:** B  
**Short Explanation:** General factors before e-commerce optimization.

### MCQ 99 (Theory)
**Question:** What is ToT for?  
A. Linear steps  
B. Explore branches for decisions  
C. No evaluation  
D. Simple tasks  

**Answer:** B  
**Short Explanation:** Branches with pros/cons for complex problems.

### MCQ 100 (Practical)
**Question:** In ToT example, how many branches for YouTube niche?  
A. 1  
B. 2  
C. At least 3  
D. 5  

**Answer:** C  
**Short Explanation:** Create at least 3 branches with thought, pros, cons, score.

### MCQ 101 (Theory)
**Question:** Tip for CoT consistency?  
A. High temp  
B. Temp=0  
C. No phrase  
D. Vague  

**Answer:** B  
**Short Explanation:** Temp=0 for consistent reasoning.

### MCQ 102 (Practical)
**Question:** When to use ReAct?  
A. Simple Q&A  
B. For external data/multi-step  
C. No tools  
D. Single path  

**Answer:** B  
**Short Explanation:** Thought-Action-Observation for population search.

### MCQ 103 (Theory)
**Question:** What is ReAct format?  
A. Thought-Action-Observation  
B. Branching  
C. General first  
D. Examples only  

**Answer:** A  
**Short Explanation:** Iterative cycle for reasoning and actions.

### MCQ 104 (Practical)
**Question:** Example of ReAct for discount?  
A. Direct calculation  
B. Observation, Reasoning, Action, Evaluation  
C. Multiple branches  
D. Role prompt  

**Answer:** B  
**Short Explanation:** Steps for 10% discount on 200 PKR, final 180 PKR.

### MCQ 105 (Theory)
**Question:** What is ToT style?  
A. Linear  
B. Branches with thought/pros/cons/score  
C. Tool calls  
D. No evaluation  

**Answer:** B  
**Short Explanation:** Evaluate branches and select best.

### MCQ 106 (Practical)
**Question:** For YouTube niche, what to do in ToT?  
A. Single idea  
B. 3 branches, select best  
C. Direct answer  
D. Role  

**Answer:** B  
**Short Explanation:** Branches for options, pros/cons, score, then final.

### MCQ 107 (Theory)
**Question:** When to use zero-shot?  
A. Complex tasks  
B. Simple, well-defined tasks  
C. Multiple examples  
D. Branching  

**Answer:** B  
**Short Explanation:** Direct ask for model's known domains.

### MCQ 108 (Practical)
**Question:** Example of few-shot for feedback?  
A. No examples  
B. 3 feedback to JSON examples  
C. One example  
D. "Think step by step"  

**Answer:** B  
**Short Explanation:** "Feedback: Great service → JSON: {service: positive}"

### MCQ 109 (Theory)
**Question:** What is system prompting?  
A. Background info  
B. Behavior guidelines  
C. Pose description  
D. Branching  

**Answer:** B  
**Short Explanation:** Overall rules, like "Always include attractions."

### MCQ 110 (Practical)
**Question:** Example of role prompting for code?  
A. "Write code"  
B. "Act as software architect, design app"  
C. Multiple paths  
D. Tool call  

**Answer:** B  
**Short Explanation:** "What architecture patterns for 1M users?"

### MCQ 111 (Theory)
**Question:** What is contextual prompting?  
A. Direct question  
B. Provide background info  
C. Multiple examples  
D. Role  

**Answer:** B  
**Short Explanation:** Specific background for accurate responses.

### MCQ 112 (Practical)
**Question:** When to use Self-Consistency?  
A. Simple classification  
B. For variable answers, pick common  
C. No evaluation  
D. Image generation  

**Answer:** B  
**Short Explanation:** Multiple paths for discount, select $40.

### MCQ 113 (Theory)
**Question:** What is Step-Back for?  
A. Branching  
B. General question first for context  
C. Tool use  
D. Examples  

**Answer:** B  
**Short Explanation:** Broader knowledge before specific task.

### MCQ 114 (Practical)
**Question:** Example of ReAct for population?  
A. Direct answer  
B. Thought, Action: web_search, Observation  
C. Branches  
D. Role  

**Answer:** B  
**Short Explanation:** Search Tokyo/New York population, compare.

### MCQ 115 (Theory)
**Question:** What is ToT when to use?  
A. Simple tasks  
B. Creative problem-solving  
C. No branches  
D. Linear  

**Answer:** B  
**Short Explanation:** For strategic planning with multiple alternatives.

### MCQ 116 (Practical)
**Question:** In ToT, what to include in branches?  
A. Thought only  
B. Thought, Pros, Cons, Score  
C. Tool call  
D. Examples  

**Answer:** B  
**Short Explanation:** For marketing strategies, pros/cons/score per branch.

### MCQ 117 (Theory)
**Question:** Tip for "Let's think step by step"?  
A. High temp  
B. With temp=0 for consistency  
C. No phrase  
D. Vague  

**Answer:** B  
**Short Explanation:** Low temp ensures reliable reasoning.

### MCQ 118 (Practical)
**Question:** For ReAct book discount, what is the format?  
A. Direct calc  
B. Observation, Reasoning, Action, Evaluation  
C. Branches  
D. Role  

**Answer:** B  
**Short Explanation:** Steps for 200 PKR with 10% discount, final 180 PKR.

### MCQ 119 (Theory)
**Question:** What is best for multi-step verification?  
A. Zero-shot  
B. ReAct  
C. One-shot  
D. Role  

**Answer:** B  
**Short Explanation:** Reasoning + actions for external data.

### MCQ 120 (Practical)
**Question:** Example of ToT for YouTube niche?  
A. Direct niche  
B. 3 branches, select best  
C. Tool search  
D. No score  

**Answer:** B  
**Short Explanation:** Branches with pros/cons/score for niche selection.

## Best Practices & Pitfalls (MCQs 121-160)

### MCQ 121 (Theory)
**Question:** What is a best practice for effective prompts?  
A. Vague verbs  
B. Specific/action verbs  
C. Negative instructions  
D. Overloading constraints  

**Answer:** B  
**Short Explanation:** Action verbs like "analyze" provide clear direction.

### MCQ 122 (Practical)
**Question:** Example of specific verb?  
A. "Give feedback"  
B. "Analyze feedback"  
C. "Help with story"  
D. "Tell about dogs"  

**Answer:** B  
**Short Explanation:** "Analyze" is specific for structured output.

### MCQ 123 (Theory)
**Question:** Why use positive instructions?  
A. Increase confusion  
B. Replace negative constraints  
C. Limit creativity  
D. Add vagueness  

**Answer:** B  
**Short Explanation:** Positive ( "Write formally" ) clearer than negative ( "Don't be informal" ).

### MCQ 124 (Practical)
**Question:** Bad example of constraints?  
A. "Write story"  
B. "No magic, no aliens, no sad ending"  
C. "Adventure story"  
D. "200 words"  

**Answer:** B  
**Short Explanation:** Too many negatives limit creativity.

### MCQ 125 (Theory)
**Question:** What is structured format?  
A. Random text  
B. JSON for complex data  
C. Vague output  
D. No format  

**Answer:** B  
**Short Explanation:** JSON organizes data for usability.

### MCQ 126 (Practical)
**Question:** Example of JSON format?  
A. Plain text  
B. {"main_idea": "string", "points": ["string"]}  
C. Bullet points  
D. Paragraph  

**Answer:** B  
**Short Explanation:** Structured for analysis output.

### MCQ 127 (Theory)
**Question:** What are variables for?  
A. One-time use  
B. Reusability  
C. Vagueness  
D. Negative instructions  

**Answer:** B  
**Short Explanation:** Variables like {expertise} make prompts reusable.

### MCQ 128 (Practical)
**Question:** Example of variable?  
A. "Role: expert"  
B. "Role: {expertise}"  
C. "Write story"  
D. "No aliens"  

**Answer:** B  
**Short Explanation:** Allows {expertise} = "doctor" for different roles.

### MCQ 129 (Theory)
**Question:** Why break tasks into chains?  
A. Increase complexity  
B. Improve accuracy for complex tasks  
C. Reduce context  
D. Add vagueness  

**Answer:** B  
**Short Explanation:** Sequential steps for manageability.

### MCQ 130 (Practical)
**Question:** Example of prompt chain?  
A. Single prompt  
B. Step 1: Research, Step 2: Outline, Step 3: Write  
C. Vague request  
D. Negative constraints  

**Answer:** B  
**Short Explanation:** Breaks content creation into steps.

### MCQ 131 (Theory)
**Question:** What is a common pitfall?  
A. Specific verbs  
B. Vague instructions  
C. Positive instructions  
D. Structured formats  

**Answer:** B  
**Short Explanation:** Leads to unpredictable outputs.

### MCQ 132 (Practical)
**Question:** Example of ambiguous prompt?  
A. "Write 300-word article on dog health"  
B. "Write about dogs"  
C. "Analyze feedback"  
D. "Generate code"  

**Answer:** B  
**Short Explanation:** "Write about dogs" is vague, leading to unfocused output.

### MCQ 133 (Theory)
**Question:** What is contradictory instructions pitfall?  
A. Clear output  
B. Conflicting requirements confuse model  
C. Improves creativity  
D. Reduces cost  

**Answer:** B  
**Short Explanation:** E.g., "Professional but casual" confuses AI.

### MCQ 134 (Practical)
**Question:** Example of contradictory prompt?  
A. "Write formal email"  
B. "Professional email that is casual and funny"  
C. "200 words"  
D. "Bullet points"  

**Answer:** B  
**Short Explanation:** Professional and casual can't combine easily.

### MCQ 135 (Theory)
**Question:** Why avoid too many constraints?  
A. Increases creativity  
B. Limits model creativity  
C. Improves format  
D. Reduces tokens  

**Answer:** B  
**Short Explanation:** Over-constraining makes output boring or incomplete.

### MCQ 136 (Practical)
**Question:** Example of too many constraints?  
A. "Adventure story"  
B. "Story, no magic, no aliens, no modern, no sad ending"  
C. "200 words"  
D. "Formal tone"  

**Answer:** B  
**Short Explanation:** Too many "no" rules limit flexibility.

### MCQ 137 (Theory)
**Question:** What is ignoring token limits pitfall?  
A. Complete responses  
B. Cut-off mid-sentence  
C. Better accuracy  
D. Low cost  

**Answer:** B  
**Short Explanation:** Responses incomplete if limit exceeded.

### MCQ 138 (Practical)
**Question:** Example of ignoring token limits?  
A. "100-word essay"  
B. "500-word essay with 300-token limit"  
C. "Bullet points"  
D. "Formal"  

**Answer:** B  
**Short Explanation:** Essay cuts off in middle.

### MCQ 139 (Theory)
**Question:** What is not testing variations pitfall?  
A. Optimal output  
B. Assuming first attempt best  
C. Improves prompts  
D. Reduces time  

**Answer:** B  
**Short Explanation:** Misses better results from different phrasings.

### MCQ 140 (Practical)
**Question:** Example of not testing variations?  
A. Multiple phrasings tested  
B. "Write story" once, no refinement  
C. A/B testing  
D. Different examples  

**Answer:** B  
**Short Explanation:** Single try misses engaging variations.

### MCQ 141 (Theory)
**Question:** Strong vs. weak prompt for analysis?  
A. "What customers think?" (weak)  
B. "Analyze reviews" (strong)  
C. Both strong  
D. Both weak  

**Answer:** A  
**Short Explanation:** Weak is vague; strong has sentiment/themes/recommendations.

### MCQ 142 (Practical)
**Question:** Weak prompt for coding?  
A. "Python function for sort" with requirements  
B. "Write function to sort list"  
C. With examples  
D. Specific key  

**Answer:** B  
**Short Explanation:** Vague, no requirements or examples.

### MCQ 143 (Theory)
**Question:** What to use for reusability?  
A. Vague verbs  
B. Variables  
C. Negative constraints  
D. Overloading  

**Answer:** B  
**Short Explanation:** {expertise} for flexible templates.

### MCQ 144 (Practical)
**Question:** Example of positive instruction?  
A. "Don't be informal"  
B. "Write in formal tone"  
C. "No details"  
D. "Avoid long"  

**Answer:** B  
**Short Explanation:** Positive guides what to do.

### MCQ 145 (Theory)
**Question:** Why provide examples?  
A. Increase vagueness  
B. Communicate expectations  
C. Limit creativity  
D. Add constraints  

**Answer:** B  
**Short Explanation:** Examples are powerful for format guidance.

### MCQ 146 (Practical)
**Question:** Structure your prompt example?  
A. No format  
B. Task, Context, Format, Example  
C. Vague  
D. Negative  

**Answer:** B  
**Short Explanation:** "Task: Generate ideas, Context: Eco-friendly brand, Format: List."

### MCQ 147 (Theory)
**Question:** What to use over constraints?  
A. Negative instructions  
B. Positive instructions  
C. Vague verbs  
D. Overloading  

**Answer:** B  
**Short Explanation:** Tell what to do, not what not to.

### MCQ 148 (Practical)
**Question:** Example of control output format?  
A. No specification  
B. Return as JSON with fields  
C. Vague  
D. Negative  

**Answer:** B  
**Short Explanation:** {"main_idea": "string", "points": ["string"]}

### MCQ 149 (Theory)
**Question:** Variables example for reusability?  
A. Fixed role  
B. "Role: {expertise}"  
C. Vague  
D. No variables  

**Answer:** B  
**Short Explanation:** Allows changing {expertise} = "lawyer" etc.

### MCQ 150 (Practical)
**Question:** Iterate and document for?  
A. Ignore successes  
B. Track what works  
C. Add vagueness  
D. Overload  

**Answer:** B  
**Short Explanation:** Successful prompts record for future use.

### MCQ 151 (Theory)
**Question:** Pitfall of ambiguous instructions?  
A. Predictable outputs  
B. Unpredictable outputs  
C. Better creativity  
D. Low cost  

**Answer:** B  
**Short Explanation:** Vague requests lead to irrelevant responses.

### MCQ 152 (Practical)
**Question:** Example of contradictory?  
A. "Write formal email"  
B. "Professional but casual"  
C. "200 words"  
D. "Bullet points"  

**Answer:** B  
**Short Explanation:** Conflicting tones confuse AI.

### MCQ 153 (Theory)
**Question:** Too many constraints cause?  
A. More creativity  
B. Limited creativity  
C. Better format  
D. Low tokens  

**Answer:** B  
**Short Explanation:** Over-constraining makes outputs boring.

### MCQ 154 (Practical)
**Question:** Example of token limit ignore?  
A. "100 words"  
B. "500 words with 300-token limit"  
C. "Formal"  
D. "Bullet points"  

**Answer:** B  
**Short Explanation:** Response cuts off mid-sentence.

### MCQ 155 (Theory)
**Question:** Not testing variations leads to?  
A. Optimal outputs  
B. Assuming first is best  
C. Better time saving  
D. More creativity  

**Answer:** B  
**Short Explanation:** Misses better phrasings or approaches.

### MCQ 156 (Practical)
**Question:** Strong vs. weak for content creation?  
A. "Write about coffee" (weak)  
B. "Instagram post for seasonal drink" (strong)  
C. Both weak  
D. Both strong  

**Answer:** B  
**Short Explanation:** Strong has context, audience, tone, format.

### MCQ 157 (Theory)
**Question:** What is data analysis pitfall?  
A. Specific insights  
B. Vague "What customers think?"  
C. Structured report  
D. Confidence level  

**Answer:** B  
**Short Explanation:** Vague leads to no sentiment/themes.

### MCQ 158 (Practical)
**Question:** Weak prompt for code?  
A. "Python function with requirements"  
B. "Write function to sort list"  
C. With examples  
D. Error handling  

**Answer:** B  
**Short Explanation:** No specifics, leads to incomplete code.

### MCQ 159 (Theory)
**Question:** Why iterate and document?  
A. Ignore failures  
B. Improve performance  
C. Add vagueness  
D. Overload  

**Answer:** B  
**Short Explanation:** Track successes for better future prompts.

### MCQ 160 (Practical)
**Question:** Example of positive over negative?  
A. "Don't make long"  
B. "Write in 200 words"  
C. "No informal"  
D. "Avoid details"  

**Answer:** B  
**Short Explanation:** Positive specifies what to do.

## Testing and Evaluation (MCQs 161-190)

### MCQ 161 (Theory)
**Question:** What is a testing framework?  
A. Random testing  
B. Documented system for recording variations  
C. No evaluation  
D. Vague notes  

**Answer:** B  
**Short Explanation:** Organized recording of prompts, goals, settings, quality.

### MCQ 162 (Practical)
**Question:** Example table in framework?  
A. No notes  
B. Version, Goal, Model, Temp, Quality, Notes  
C. Only prompt  
D. No model  

**Answer:** B  
**Short Explanation:** "v1.0 | Generate blog | GPT-4 | 0.7 | Good | Too formal"

### MCQ 163 (Theory)
**Question:** What is A/B testing?  
A. Single prompt  
B. Compare multiple versions  
C. No variations  
D. High temp only  

**Answer:** B  
**Short Explanation:** Test different phrasings, examples, settings.

### MCQ 164 (Practical)
**Question:** Variations to test?  
A. Same example sets  
B. Different example sets  
C. No phrasings  
D. Fixed temp  

**Answer:** B  
**Short Explanation:** Test different examples for pattern impact.

### MCQ 165 (Theory)
**Question:** Evaluation criteria?  
A. Accuracy, relevance, style  
B. Token limit only  
C. Model size  
D. No metrics  

**Answer:** A  
**Short Explanation:** Assess if output correct, on-topic, complete, styled right.

### MCQ 166 (Practical)
**Question:** Metric for same prompt similar outputs?  
A. Accuracy  
B. Consistency  
C. Relevance  
D. Style  

**Answer:** B  
**Short Explanation:** Checks reliability across runs.

### MCQ 167 (Theory)
**Question:** What is creativity metric for?  
A. Factual tasks  
B. When desired, novel responses  
C. Math  
D. Code  

**Answer:** B  
**Short Explanation:** For creative tasks like stories.

### MCQ 168 (Practical)
**Question:** Example of iteration?  
A. Keep v1.0  
B. From test insights, refine to v1.1  
C. No notes  
D. Ignore quality  

**Answer:** B  
**Short Explanation:** Add tone guidance after "too formal" note.

### MCQ 169 (Theory)
**Question:** Why document prompts?  
A. Forget successes  
B. Systematic improvement  
C. Add vagueness  
D. Reduce testing  

**Answer:** B  
**Short Explanation:** Track what works for future reference.

### MCQ 170 (Practical)
**Question:** A/B test for temperature?  
A. Same temp  
B. Temp 0.7 vs 0.3  
C. No variations  
D. Fixed format  

**Answer:** B  
**Short Explanation:** Compare consistency vs. creativity.

### MCQ 171 (Theory)
**Question:** What is completeness metric?  
A. Covers all needed  
B. Off-topic  
C. Vague  
D. Incomplete  

**Answer:** A  
**Short Explanation:** Checks if output everything required.

### MCQ 172 (Practical)
**Question:** Metric for format adherence?  
A. Accuracy  
B. Format  
C. Relevance  
D. Style  

**Answer:** B  
**Short Explanation:** Is it JSON as requested?

### MCQ 173 (Theory)
**Question:** What is following instructions metric?  
A. Ignore requirements  
B. Adherence to specs  
C. Random  
D. No check  

**Answer:** B  
**Short Explanation:** Checks if prompt requirements met.

### MCQ 174 (Practical)
**Question:** Example of A/B for phrasings?  
A. Same wording  
B. "Analyze" vs. "Tell about"  
C. No test  
D. Fixed  

**Answer:** B  
**Short Explanation:** "Analyze" gives structured output.

### MCQ 175 (Theory)
**Question:** What is factual accuracy metric?  
A. Creative fiction  
B. Correctness of info  
C. Vague  
D. Style  

**Answer:** B  
**Short Explanation:** Checks if information accurate.

### MCQ 176 (Practical)
**Question:** Test for output formats?  
A. No variations  
B. JSON vs. bullet points  
C. Same format  
D. Ignore  

**Answer:** B  
**Short Explanation:** See which is more usable.

### MCQ 177 (Theory)
**Question:** Why A/B test?  
A. Assume first best  
B. Optimize by comparison  
C. Reduce prompts  
D. Add vagueness  

**Answer:** B  
**Short Explanation:** Identify better versions.

### MCQ 178 (Practical)
**Question:** Notes in framework for?  
A. Ignore  
B. Quality insights  
C. Vague  
D. No use  

**Answer:** B  
**Short Explanation:** "Too formal" leads to tone adjustment.

### MCQ 179 (Theory)
**Question:** What is haphazard process?  
A. Systematic testing  
B. No framework  
C. Documented  
D. Iteration  

**Answer:** B  
**Short Explanation:** Without framework, prompt engineering random.

### MCQ 180 (Practical)
**Question:** Example of evaluation?  
A. No criteria  
B. Accuracy: Does answer correctly?  
C. Ignore style  
D. No iteration  

**Answer:** B  
**Short Explanation:** Check if output factually right.

### MCQ 181 (Theory)
**Question:** What is context management for long convos?  
A. Ignore history  
B. Summarize previous  
C. Full history always  
D. No break  

**Answer:** B  
**Short Explanation:** Summarize to avoid rot.

### MCQ 182 (Practical)
**Question:** Example of prompt chaining?  
A. Single step  
B. Research → Outline → Write  
C. Vague  
D. No format  

**Answer:** B  
**Short Explanation:** Sequential for complex tasks.

### MCQ 183 (Theory)
**Question:** What is structured outputs for?  
A. Random text  
B. Complex data JSON  
C. Vague  
D. No use  

**Answer:** B  
**Short Explanation:** JSON for analysis usability.

### MCQ 184 (Practical)
**Question:** Example of multi-modal?  
A. Text only  
B. "Analyze image for details"  
C. No images  
D. Vague  

**Answer:** B  
**Short Explanation:** "What to look for in images" with text instructions.

### MCQ 185 (Theory)
**Question:** When to use multi-modal?  
A. Text only models  
B. Models supporting images  
C. No context  
D. Vague  

**Answer:** B  
**Short Explanation:** For combining text and visual instructions.

### MCQ 186 (Practical)
**Question:** Use system messages for?  
A. Ignore  
B. Behavior guidelines  
C. Vague  
D. No iteration  

**Answer:** B  
**Short Explanation:** "Always cite sources" for consistency.

### MCQ 187 (Theory)
**Question:** What is prompt chaining?  
A. Single prompt  
B. Sequential steps  
C. No break  
D. Vague  

**Answer:** B  
**Short Explanation:** Break tasks into parts for clarity.

### MCQ 188 (Practical)
**Question:** Example of structured output?  
A. Plain text  
B. JSON with fields  
C. Vague  
D. No format  

**Answer:** B  
**Short Explanation:** "Return analysis as JSON {summary, insights}"

### MCQ 189 (Theory)
**Question:** What is explicit about image details?  
A. Vague  
B. Clear what to look for  
C. No images  
D. Text only  

**Answer:** B  
**Short Explanation:** For multi-modal, specify visual instructions.

### MCQ 190 (Practical)
**Question:** Use images as?  
A. No context  
B. Examples or context  
C. Vague  
D. Ignore  

**Answer:** B  
**Short Explanation:** "Based on this image, describe scene."

## Advanced Techniques (MCQs 191-220)

### MCQ 191 (Theory)
**Question:** What is leverage structured outputs?  
A. Random text  
B. JSON/XML for complex data  
C. Vague  
D. No format  

**Answer:** B  
**Short Explanation:** Organized data for usability.

### MCQ 192 (Practical)
**Question:** Example of JSON output?  
A. Plain summary  
B. { "summary": "overview", "insights": ["1", "2"] }  
C. Vague  
D. No recommendations  

**Answer:** B  
**Short Explanation:** Structured for analysis.

### MCQ 193 (Theory)
**Question:** Context management for long convos?  
A. Full history  
B. Summarize previous  
C. No messages  
D. Increase tokens  

**Answer:** B  
**Short Explanation:** Summarize to manage window.

### MCQ 194 (Practical)
**Question:** Use system messages for?  
A. Vague  
B. Guidelines effectively  
C. No use  
D. Ignore  

**Answer:** B  
**Short Explanation:** For behavior rules.

### MCQ 195 (Theory)
**Question:** Break complex tasks into?  
A. Single prompt  
B. Smaller parts  
C. Vague  
D. No break  

**Answer:** B  
**Short Explanation:** For manageability.

### MCQ 196 (Practical)
**Question:** Example of multi-modal?  
A. Text only  
B. "Look for in images"  
C. No details  
D. Vague  

**Answer:** B  
**Short Explanation:** "Explicit about image details."

### MCQ 197 (Theory)
**Question:** Prompt chaining example?  
A. Single  
B. Step 1: Research, Step 2: Outline, Step 3: Write  
C. Vague  
D. No steps  

**Answer:** B  
**Short Explanation:** Sequential for complex content.

### MCQ 198 (Practical)
**Question:** Structured outputs for?  
A. Vague text  
B. Complex data  
C. No format  
D. Simple  

**Answer:** B  
**Short Explanation:** JSON for recommendations.

### MCQ 199 (Theory)
**Question:** Multi-modal when?  
A. Text models  
B. Image-supporting models  
C. No context  
D. Vague  

**Answer:** B  
**Short Explanation:** For text + visual instructions.

### MCQ 200 (Practical)
**Question:** Use images as?  
A. Ignore  
B. Examples or context  
C. Vague  
D. No use  

**Answer:** B  
**Short Explanation:** For visual guidance.

### MCQ 201 (Theory)
**Question:** What is MoE gating network?  
A. Full activation  
B. Selects experts  
C. No routing  
D. Dense  

**Answer:** B  
**Short Explanation:** Routes inputs to relevant sub-networks.

### MCQ 202 (Practical)
**Question:** MoE in Grok 4?  
A. Speculated  
B. Confirmed, multi-agent  
C. Unknown  
D. Dense  

**Answer:** B  
**Short Explanation:** Confirmed MoE with ~500B parameters.

### MCQ 203 (Theory)
**Question:** MoE impact on prompting?  
A. No change  
B. Domain-specific signals upfront  
C. Vague prompts better  
D. High temp always  

**Answer:** B  
**Short Explanation:** Front-load cues to activate right experts.

### MCQ 204 (Practical)
**Question:** Example of front-load?  
A. Vague start  
B. "Role: Financial analyst. Task: Analysis"  
C. Mixed tasks  
D. Overlong preamble  

**Answer:** B  
**Short Explanation:** Locks router to finance expert early.

### MCQ 205 (Theory)
**Question:** MoE benefit?  
A. Routing instability  
B. Efficiency/specialization  
C. Memory overhead  
D. Slow scaling  

**Answer:** B  
**Short Explanation:** Sparse activation for efficient task handling.

### MCQ 206 (Practical)
**Question:** Drawback of MoE?  
A. No specialization  
B. Routing instability  
C. Low memory  
D. Full activation  

**Answer:** B  
**Short Explanation:** Vague prompts cause biases or inefficiencies.

### MCQ 207 (Theory)
**Question:** Expert-aware prompting tip?  
A. Vague vocabulary  
B. Explicit language/style  
C. Mixed tasks  
D. High temp  

**Answer:** B  
**Short Explanation:** "Language: Urdu. Style: technical" for specialized experts.

### MCQ 208 (Practical)
**Question:** Troubleshooting for inconsistent MoE answers?  
A. Increase temp  
B. Add domain anchors, reduce temp  
C. Vague start  
D. Mixed formats  

**Answer:** B  
**Short Explanation:** Sharper cues and low temp stabilize routing.

### MCQ 209 (Theory)
**Question:** Do less of in MoE?  
A. Front-load signals  
B. Overlong preambles  
C. Separate tasks  
D. Match examples  

**Answer:** B  
**Short Explanation:** Burying task weakens routing.

### MCQ 210 (Practical)
**Question:** Routing-friendly skeleton example?  
A. No role  
B. Role, Task, Instructions, Examples, Context  
C. Vague  
D. Mixed  

**Answer:** B  
**Short Explanation:** Structured for clear expert selection.

### MCQ 211 (Theory)
**Question:** MoE troubleshooting for mixed-topic?  
A. Keep mixed  
B. Split request  
C. High temp  
D. No plan  

**Answer:** B  
**Short Explanation:** Separate or ask for plan first.

### MCQ 212 (Practical)
**Question:** Bottom line for MoE prompting?  
A. Change foundation  
B. Leverage clear, early domain signals  
C. Vague signals  
D. High churn  

**Answer:** B  
**Short Explanation:** Signals decide which experts wake up.

### MCQ 213 (Theory)
**Question:** Prompt engineering conclusion key?  
A. Start complex  
B. Start simple, add complexity  
C. No examples  
D. No test  

**Answer:** B  
**Short Explanation:** Gradually build for success.

### MCQ 214 (Practical)
**Question:** 6-Part Framework link for?  
A. Basic prompting  
B. Next level prompting  
C. No iteration  
D. Vague  

**Answer:** B  
**Short Explanation:** For 10x better results with 6 steps.

### MCQ 215 (Theory)
**Question:** Why prompting skills matter?  
A. No advantage  
B. Professionals advantage in future  
C. Replace AI  
D. No work  

**Answer:** B  
**Short Explanation:** Doctors, engineers use AI for complex tasks.

### MCQ 216 (Practical)
**Question:** 6-Part Framework models?  
A. Only ChatGPT  
B. ChatGPT, Gemini, Claude  
C. No models  
D. Old models  

**Answer:** B  
**Short Explanation:** Works across major AI models.

### MCQ 217 (Theory)
**Question:** Command step problem?  
A. Specific requests  
B. Vague questions  
C. Strong verbs  
D. No issue  

**Answer:** B  
**Short Explanation:** Vague leads to wishy-washy responses.

### MCQ 218 (Practical)
**Question:** Good command example?  
A. "Give advice"  
B. "Recommend strategy for moderate risk"  
C. "Help with investing"  
D. "Tell me"  

**Answer:** B  
**Short Explanation:** Strong verb "recommend" with specifics.

### MCQ 219 (Theory)
**Question:** Context rule?  
A. Less is better  
B. Narrow with background/constraints  
C. No goals  
D. Vague  

**Answer:** B  
**Short Explanation:** Guide AI direction with details.

### MCQ 220 (Practical)
**Question:** Rule of Three in context?  
A. No framework  
B. Who, What, When  
C. Past only  
D. Future only  

**Answer:** B  
**Short Explanation:** Age, goal, timeline for strategy.

### MCQ 221 (Theory)
**Question:** Logic step solution?  
A. No guidance  
B. Tell how to think/respond  
C. Vague format  
D. No structure  

**Answer:** B  
**Short Explanation:** Define output structure for usability.

### MCQ 222 (Practical)
**Question:** Logic example?  
A. No format  
B. "List categories, explain allocation"  
C. Vague  
D. Negative  

**Answer:** B  
**Short Explanation:** Clear reasoning and format for strategy.

### MCQ 223 (Theory)
**Question:** Roleplay power?  
A. No change  
B. Transform AI into expert  
C. Vague  
D. Reduce quality  

**Answer:** B  
**Short Explanation:** Prompt affects who AI becomes.

### MCQ 224 (Practical)
**Question:** Role example for finance?  
A. "General advisor"  
B. "Certified financial advisor with 15 years experience"  
C. Vague  
D. No role  

**Answer:** B  
**Short Explanation:** Specific expertise for mid-term planning.

### MCQ 225 (Theory)
**Question:** Formatting goal?  
A. Unstructured  
B. Organize for usability  
C. Vague  
D. No format  

**Answer:** B  
**Short Explanation:** Actionable information.

### MCQ 226 (Practical)
**Question:** Formatting example?  
A. No sections  
B. "Format as list with sections"  
C. Vague  
D. Negative  

**Answer:** B  
**Short Explanation:** Bullet points under Asset Allocation, Rationale.

### MCQ 227 (Theory)
**Question:** Questions step why works?  
A. No gaps  
B. Identifies gaps, refines  
C. Reduces quality  
D. No iteration  

**Answer:** B  
**Short Explanation:** AI asks for tailoring, leads to better results.

### MCQ 228 (Practical)
**Question:** Advanced question strategy?  
A. One round  
B. Multiple rounds until repetition  
C. No questions  
D. Vague  

**Answer:** B  
**Short Explanation:** Round 1: 10 questions, Round 2: Based on answers.

### MCQ 229 (Theory)
**Question:** When extensive context?  
A. Simple tasks  
B. Complex tasks  
C. No tasks  
D. All tasks  

**Answer:** B  
**Short Explanation:** For business plans vs. minimal for recommendations.

### MCQ 230 (Practical)
**Question:** Great prompters do?  
A. Vague commands  
B. Use questions to refine  
C. Generic info  
D. Skip steps  

**Answer:** B  
**Short Explanation:** Iterative questions for tailored results.

### MCQ 231 (Theory)
**Question:** Common mistake in framework?  
A. Strong verbs  
B. Vague commands  
C. Structured  
D. Iteration  

**Answer:** B  
**Short Explanation:** Starting with questions instead of directives.

### MCQ 232 (Practical)
**Question:** Insufficient context mistake?  
A. Specific info  
B. Generic information  
C. Detailed  
D. No issue  

**Answer:** B  
**Short Explanation:** Applies to anyone, not tailored.

### MCQ 233 (Theory)
**Question:** No output structure mistake?  
A. Structured  
B. Let AI choose format  
C. JSON  
D. Bullet points  

**Answer:** B  
**Short Explanation:** AI chooses format, may not be useful.

### MCQ 234 (Practical)
**Question:** Generic roles mistake?  
A. Specific expertise  
B. Vague roles  
C. No role  
D. Detailed  

**Answer:** B  
**Short Explanation:** "Expert" vs. "15 years personal finance specialist."

### MCQ 235 (Theory)
**Question:** Stopping too early mistake?  
A. Use questions  
B. Not using questions to refine  
C. Iteration  
D. No issue  

**Answer:** B  
**Short Explanation:** Misses refined results.

### MCQ 236 (Practical)
**Question:** Framework benefits?  
A. Generic interactions  
B. Transforms to expert consultations  
C. Reduces quality  
D. Adds vagueness  

**Answer:** B  
**Short Explanation:** Turns AI into specialized advisor.

### MCQ 237 (Theory)
**Question:** When high-stakes decisions?  
A. Minimal context  
B. Heavy context/questions  
C. No iteration  
D. Vague  

**Answer:** B  
**Short Explanation:** For life-changing like investments.

### MCQ 238 (Practical)
**Question:** Voice memo strategy?  
A. Text only  
B. Natural answering for questions  
C. No follow-ups  
D. Vague  

**Answer:** B  
**Short Explanation:** Faster, conversational for AI questions.

### MCQ 239 (Theory)
**Question:** Iteration approach?  
A. No refinement  
B. Start basic, ask questions, refine  
C. Complex first  
D. No framework  

**Answer:** B  
**Short Explanation:** Gaps identify and refine until fresh questions stop.

### MCQ 240 (Practical)
**Question:** Advanced applications?  
A. No scale  
B. Scales from personal to professional  
C. Only daily  
D. No creative  

**Answer:** B  
**Short Explanation:** Meal planning to business plans.

### MCQ 241 (Theory)
**Question:** What is context engineering?  
A. Single prompts  
B. Dynamic systems for LLM input  
C. No optimization  
D. Vague  

**Answer:** B  
**Short Explanation:** Right info, format, time for tasks.

### MCQ 242 (Practical)
**Question:** LLM as CPU, context as?  
A. Disk  
B. RAM  
C. Network  
D. Screen  

**Answer:** B  
**Short Explanation:** Context window as RAM for temporary data.

### MCQ 243 (Theory)
**Question:** Context engineering for?  
A. Simple conversations  
B. Building AI agents/apps  
C. No agents  
D. Prompt only  

**Answer:** B  
**Short Explanation:** Comprehensive for complex applications.

### MCQ 244 (Practical)
**Question:** Difference from prompt engineering?  
A. Same  
B. More comprehensive, code-like for agents  
C. Less complex  
D. No difference  

**Answer:** B  
**Short Explanation:** Standalone instruction sets for autonomous scenarios.

### MCQ 245 (Theory)
**Question:** Agent component: Model?  
A. External interaction  
B. Core AI engine  
C. Dynamic history  
D. Safety  

**Answer:** B  
**Short Explanation:** GPT, Claude, etc., for processing.

### MCQ 246 (Practical)
**Question:** Tools for?  
A. Static info  
B. External interaction  
C. Voice  
D. Monitoring  

**Answer:** B  
**Short Explanation:** Calendar, email APIs for integration.

### MCQ 247 (Theory)
**Question:** Memory in agents?  
A. Static databases  
B. Dynamic history  
C. Deployment  
D. Safety  

**Answer:** B  
**Short Explanation:** Conversation history for retention.

### MCQ 248 (Practical)
**Question:** Knowledge?  
A. Dynamic  
B. Static info databases  
C. Tools  
D. Audio  

**Answer:** B  
**Short Explanation:** Legal databases for agents.

### MCQ 249 (Theory)
**Question:** Orchestration?  
A. Voice input  
B. Deployment/monitoring  
C. Safety  
D. Static  

**Answer:** B  
**Short Explanation:** Performance tracking and improvement.

### MCQ 250 (Practical)
**Question:** Guardrails?  
A. Increase harm  
B. Safety for behavior  
C. External tools  
D. No boundaries  

**Answer:** B  
**Short Explanation:** Prevent inappropriate language.

### MCQ 251 (Theory)
**Question:** Audio/Speech for?  
A. Text only  
B. Natural interaction  
C. Static  
D. No access  

**Answer:** B  
**Short Explanation:** Voice capabilities for hands-free.

### MCQ 252 (Practical)
**Question:** Multi-agent: Task splitting?  
A. All in one  
B. e.g., search + summarize  
C. No sharing  
D. Vague  

**Answer:** B  
**Short Explanation:** Separate agents for efficiency.

### MCQ 253 (Theory)
**Question:** Multi-agent context sharing?  
A. Avoid  
B. Always share  
C. No need  
D. Vague  

**Answer:** B  
**Short Explanation:** For coordinated performance.

### MCQ 254 (Practical)
**Question:** Writing context strategy?  
A. No notes  
B. Task notes for later  
C. Vague  
D. Ignore  

**Answer:** B  
**Short Explanation:** Decision rationales store.

### MCQ 255 (Theory)
**Question:** Selecting context?  
A. Random  
B. Pull relevant from sources  
C. No selection  
D. Full load  

**Answer:** B  
**Short Explanation:** Database queries for tasks.

### MCQ 256 (Practical)
**Question:** Compressing context?  
A. Expand  
B. Summarization for overload  
C. No key points  
D. Vague  

**Answer:** B  
**Short Explanation:** Key point extraction for token efficiency.

### MCQ 257 (Theory)
**Question:** Isolating context?  
A. Mix all  
B. Split task-specific  
C. No separation  
D. Full share  

**Answer:** B  
**Short Explanation:** User-specific info separate for security.

### MCQ 258 (Practical)
**Question:** Actions as decisions?  
A. Ignore  
B. Careful at decision points  
C. No actions  
D. Vague  

**Answer:** B  
**Short Explanation:** Implicit decisions in architecture.

### MCQ 259 (Theory)
**Question:** Advanced architecture: State management?  
A. No compaction  
B. Hierarchical summarization  
C. Vague  
D. Full history  

**Answer:** B  
**Short Explanation:** Compression for long tasks.

### MCQ 260 (Practical)
**Question:** Optimization for?  
A. Accuracy/latency/cost/recovery  
B. No accuracy  
C. High cost  
D. No recovery  

**Answer:** A  
**Short Explanation:** Balance for enterprise.

### MCQ 261 (Theory)
**Question:** Security in context?  
A. No isolation  
B. Isolation for leaks  
C. Mix sensitive  
D. Vague  

**Answer:** B  
**Short Explanation:** Sensitive data separate.

### MCQ 262 (Practical)
**Question:** Memory hierarchies?  
A. No levels  
B. Short-term vs long-term  
C. Vague  
D. Full window  

**Answer:** B  
**Short Explanation:** Context window vs database.

### MCQ 263 (Theory)
**Question:** RAG integration?  
A. No chunking  
B. Semantic chunking  
C. Vague  
D. Full doc  

**Answer:** B  
**Short Explanation:** Meaningful chunks for retrieval.

### MCQ 264 (Practical)
**Question:** Temporal reasoning?  
A. No graph  
B. Graph-based for time relationships  
C. Vague  
D. No reasoning  

**Answer:** B  
**Short Explanation:** Time-based analysis with graphs.

### MCQ 265 (Theory)
**Question:** Enterprise trade-offs?  
A. No modularity  
B. Modular components for scalability  
C. Vague  
D. Full monolithic  

**Answer:** B  
**Short Explanation:** Separate components for flexibility.

### MCQ 266 (Practical)
**Question:** When to use context engineering?  
A. Simple convos  
B. Autonomous scenarios  
C. No integration  
D. Vague  

**Answer:** B  
**Short Explanation:** For multiple inquiries, escalations.

### MCQ 267 (Theory)
**Question:** Burger analogy: Model?  
A. Vegetables  
B. Bun (holds together)  
C. Patty  
D. Condiments  

**Answer:** B  
**Short Explanation:** Model holds components together.

### MCQ 268 (Practical)
**Question:** Role of context engineer?  
A. No manual  
B. Instruction manual for components  
C. Vague  
D. Ignore tools  

**Answer:** B  
**Short Explanation:** How components work together.

### MCQ 269 (Theory)
**Question:** Prompt complexity in context engineering?  
A. Simple  
B. Code-like with XML/markdown  
C. Vague  
D. No structure  

**Answer:** B  
**Short Explanation:** Comprehensive for scenarios.

### MCQ 270 (Practical)
**Question:** AI research assistant example: Step 1?  
A. No subtasks  
B. Extract 10 subtasks  
C. Vague  
D. No prioritize  

**Answer:** B  
**Short Explanation:** Diverse subtasks for angles/sources.

### MCQ 271 (Theory)
**Question:** Advanced strategy: Writing context?  
A. No notes  
B. Task notes for later  
C. Vague  
D. Ignore  

**Answer:** B  
**Short Explanation:** Intermediate results store.

### MCQ 272 (Practical)
**Question:** Selecting context?  
A. Random  
B. Database queries  
C. No retrieval  
D. Full load  

**Answer:** B  
**Short Explanation:** Real-time data for tasks.

### MCQ 273 (Theory)
**Question:** Compressing context?  
A. Expand  
B. Summarization  
C. No structure  
D. Vague  

**Answer:** B  
**Short Explanation:** Key point extraction for overload.

### MCQ 274 (Practical)
**Question:** Isolating context?  
A. Mix  
B. Task-specific separation  
C. No boundary  
D. Vague  

**Answer:** B  
**Short Explanation:** Security for boundaries.

### MCQ 275 (Theory)
**Question:** Multi-agent sharing?  
A. Avoid  
B. Always share  
C. No principles  
D. Vague  

**Answer:** B  
**Short Explanation:** For coordination.

### MCQ 276 (Practical)
**Question:** Best practice: Structure?  
A. No tags  
B. XML, markdown  
C. Vague  
D. No format  

**Answer:** B  
**Short Explanation:** Clear formatting for prompts.

### MCQ 277 (Theory)
**Question:** Essential guideline: Comprehensive?  
A. Ignore scenarios  
B. Anticipate all scenarios  
C. No test  
D. Vague  

**Answer:** B  
**Short Explanation:** All cases cover.

### MCQ 278 (Practical)
**Question:** Resource: LangChain guide?  
A. No strategies  
B. Writing/selecting/compressing context  
C. Vague  
D. No application  

**Answer:** B  
**Short Explanation:** Practical implementation.

### MCQ 279 (Theory)
**Question:** Quiz 1: Difference prompt vs context?  
A. Same  
B. Prompt conversational, context for apps  
C. No difference  
D. Reverse  

**Answer:** B  
**Short Explanation:** Prompt iterative, context standalone.

### MCQ 280 (Practical)
**Question:** Quiz 3: Customer service scenarios?  
A. No billing  
B. Billing, refunds, login, escalation  
C. Vague  
D. No tone  

**Answer:** B  
**Short Explanation:** All inquiries, abusive, knowledge access.

### MCQ 281 (Theory)
**Question:** RAG prioritize?  
A. Old passages  
B. Relevant/newest passages  
C. Random  
D. No optimization  

**Answer:** B  
**Short Explanation:** For accurate, up-to-date responses.

### MCQ 282 (Practical)
**Question:** RAG chunking?  
A. Full doc  
B. Optimize for manageable pieces  
C. No ranking  
D. Duplicate  

**Answer:** B  
**Short Explanation:** Small chunks for efficient retrieval.

### MCQ 283 (Theory)
**Question:** RAG ranking?  
A. No order  
B. Relevance-based order  
C. Random  
D. No dedup  

**Answer:** B  
**Short Explanation:** Top relevant first.

### MCQ 284 (Practical)
**Question:** Deduping in RAG?  
A. Keep duplicates  
B. Remove duplicates  
C. Vague  
D. No budget  

**Answer:** B  
**Short Explanation:** For concise context.

### MCQ 285 (Theory)
**Question:** Token budgets in RAG?  
A. Unlimited  
B. Optimize to fit limits  
C. Ignore rot  
D. Full load  

**Answer:** B  
**Short Explanation:** Prevent rot with efficient use.

### MCQ 286 (Practical)
**Question:** Combining prompts and RAG?  
A. Prompts for knowledge  
B. Prompts for behavior, context for knowledge  
C. No combine  
D. Reverse  

**Answer:** B  
**Short Explanation:** "Extract JSON" prompt with RAG invoice context.

### MCQ 287 (Theory)
**Question:** Policy Q&A bot RAG?  
A. No chunking  
B. Chunking, metadata filters  
C. Vague  
D. No freshness  

**Answer:** B  
**Short Explanation:** For HR department, freshness boosts.

### MCQ 288 (Practical)
**Question:** Agentic workflow example?  
A. No tools  
B. Tool instructions + feed responses back  
C. Vague  
D. No state  

**Answer:** B  
**Short Explanation:** Function signatures with memory/state.

### MCQ 289 (Theory)
**Question:** Practical tip for prompts?  
A. Long, vague  
B. Short, specific, testable  
C. No schemas  
D. Ignore citations  

**Answer:** B  
**Short Explanation:** Define output schemas for testing.

### MCQ 290 (Practical)
**Question:** Few-shot in RAG?  
A. Always in prompt  
B. Move to retrieval if generalize  
C. No examples  
D. Vague  

**Answer:** B  
**Short Explanation:** Prefer retrieval for edge cases.

### MCQ 291 (Theory)
**Question:** Context for correctness?  
A. No citations  
B. Add citations, "answer from context"  
C. Vague  
D. Ignore  

**Answer:** B  
**Short Explanation:** For grounded responses.

### MCQ 292 (Practical)
**Question:** Evaluate layers?  
A. Combined only  
B. Prompt A/B, retrieval quality separate  
C. No evals  
D. Vague  

**Answer:** B  
**Short Explanation:** Precision/recall for retrieval, A/B for prompts.

### MCQ 293 (Theory)
**Question:** One-liner for prompt/context?  
A. Prompt show, context ask  
B. Prompt ask, context show  
C. Same  
D. No combine  

**Answer:** B  
**Short Explanation:** Prompt how to ask, context what to show.

### MCQ 294 (Practical)
**Question:** Invoice extractor prompt/context?  
A. Only prompt  
B. Prompt extract, context examples/spec  
C. No JSON  
D. Vague  

**Answer:** B  
**Short Explanation:** "Extract fields" prompt with labeled examples context.

### MCQ 295 (Theory)
**Question:** Policy bot context?  
A. No RAG  
B. RAG with chunking, filters  
C. Vague  
D. No citations  

**Answer:** B  
**Short Explanation:** Metadata filters like department=HR.

### MCQ 296 (Practical)
**Question:** Agentic workflow prompt?  
A. No tools  
B. Tool instructions, feed back  
C. Vague  
D. No memory  

**Answer:** B  
**Short Explanation:** Function signatures with state.

### MCQ 297 (Theory)
**Question:** Practical tip for context?  
A. No chunking  
B. Optimize chunking/ranking/deduping/token budgets  
C. Vague  
D. Full load  

**Answer:** B  
**Short Explanation:** For efficient retrieval.

### MCQ 298 (Practical)
**Question:** Add citations when?  
A. No correctness  
B. When correctness matters  
C. Vague  
D. Always ignore  

**Answer:** B  
**Short Explanation:** "Answer from context" for reliability.

### MCQ 299 (Theory)
**Question:** Evaluate separately?  
A. Combined  
B. Prompt and retrieval layers  
C. No evals  
D. Vague  

**Answer:** B  
**Short Explanation:** A/B for prompts, precision/recall for retrieval.

### MCQ 300 (Practical)
**Question:** One-liner example?  
A. Prompt show  
B. Prompt ask, context show  
C. No  
D. Reverse  

**Answer:** B  
**Short Explanation:** For reliable LLM apps.