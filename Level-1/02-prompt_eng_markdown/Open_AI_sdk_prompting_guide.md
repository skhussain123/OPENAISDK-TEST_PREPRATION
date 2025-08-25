
---

GPT-4.1 models ka family GPT-4o se ek bara qadam aagay hai, khaas taur pe coding, instructions follow karne aur lambi context samajhne me. Is prompting guide me hum ne bohot se important tips ikatthi ki hain jo internal testing se mili hain, taa ke developers is naye model family ki behtareen abilities ka poora faida utha saken.

GPT-4.1 par ab bhi wohi typical best practices apply hoti hain jaise ke context examples dena, instructions ko specific aur clear banana, aur planning induce karna prompts ke zariye taa ke model ki intelligence maximize ho. Lekin, hum expect karte hain ke is model ka poora faida uthane ke liye thoda prompt migration zaroori hoga. GPT-4.1 ko zyada closely aur literally instructions follow karne ke liye train kiya gaya hai, jabke pehle models zyada liberal tareeqe se user aur system prompts se intent infer karte thay. Iska matlab yeh bhi hai ke GPT-4.1 bohot steerable hai aur agar prompts achi tarah specify kiye gaye ho to yeh turant response deta hai. Agar model ka behavior aapki expectation se different aaye, to ek seedhi aur clear sentence jo aapke desired behavior ko explain kare, aam tor pe kafi hota hai model ko sahi raaste par steer karne ke liye.

Mazeed examples ke liye niche diye gaye prompts ko dekhiye aur yaad rakhiye ke yeh guidance wide level par apply hoti hai lekin har case me same result nahi deti. AI engineering waise bhi ek empirical discipline hai aur large language models by nature nondeterministic hote hain. Is guide ko follow karne ke sath sath hum recommend karte hain ke informative evals banayein aur bar bar iterate karein taa ke aapko yaqeen ho ke aapke prompt engineering changes waqai aapke use case me faida de rahe hain.

## 1. Agentic Workflows

GPT-4.1 agentic workflows banane ke liye ek bohot acha model hai. Is model ki training ke dauran humne mukhtalif qisam ke agentic problem-solving trajectories par focus kiya, aur jo agentic harness banayi gayi hai woh SWE-bench Verified test par state-of-the-art performance achieve karti hai. Ye model non-reasoning models ke liye 55% problems solve karta hai.

**System Prompt Reminders**

GPT-4.1 ki agentic capabilities ka poora faida uthane ke liye, hum recommend karte hain ke har agent prompt me teen qisam ke reminders shamil kiye jayein.

#### 1. Persistence
Ye prompts specially agentic coding workflows ke liye optimized hain, lekin inhe general agentic use cases me bhi asaani se modify kiya jaa sakta hai.
```bash
You are an agent - please keep going until the user’s query is completely resolved, 
before ending your turn and yielding back to the user. 
Only terminate your turn when you are sure that the problem is solved.
```

#### 2. Tool-calling
Ye model ko encourage karta hai ke woh apne tools ka poori tarah se istemal kare, aur is tarah se hallucinate karne (galat cheez soch lena) ya andaza lagane ki probability kam ho jati hai.

```bash
Agar aapko user ki request se related file content ya codebase structure ke baare me surety na ho, 
to apne tools ka istemal karke files ko read karo aur relevant information gather karo. 
Kabhi bhi andaza mat lagao ya khud se jawab create mat karo.
```

#### 3. Planning [optional]
Agar chaha jaye to, ye ensure karta hai ke model har tool call se pehle clearly plan banaye aur us tool call ke outcomes par reflect kare. Ye approach is baat ko rokti hai ke model sirf ek chain of tool calls bana kar task complete kare, bina kisi soch-vichar ke.

```bash
Aapko har function call se pehle bohot detail me planning karni hogi, aur pehle ke function calls ke results par bhi ghor karna hoga. Sirf function calls ka chain bana kar poora process mat karo, kyunki is se aapki problem solve karne ki ability aur insightful soch kamzor ho sakti hai.
```
GPT-4.1 ko aise train kiya gaya hai ke woh user instructions aur system prompts dono ka bohot qareeb se follow kare, khaaskar agentic setting me.
Model ne in teen simple instructions ko strictly follow kiya aur hamara internal SWE-bench Verified score lagbhag 20% barh gaya. Isi liye hum strongly recommend karte hain ke har agent prompt ki shuruaat clear reminders ke sath ki jaye jo upar di gayi teen categories cover karte hain.
Kul mila kar, humein ye teen instructions model ko ek chatbot jaisa banne ke bajaye ek zyada “eager” agent me transform karte hue nazar aaye, jo interaction ko khud-ba-khud aur independently aage le kar jata hai.

### Tool Calls
Pichlay models ke muqable mein, GPT-4.1 ko zyada training mili hai tools ko effectively use karne par jo OpenAI API request mein arguments ki tarah diye jate hain. Hum developers ko encourage karte hain ke wo sirf tools field ka use karein tools pass karne ke liye, bajaye iske ke manually tool descriptions apne prompt mein inject karein aur tool calls ke liye alag parser likhein, jaisa kuch log pehle karte rahe hain. Ye tareeqa sabse behtareen hai errors ko kam karne ke liye aur ye ensure karne ke liye ke model distribution mein rahe jab tool-calling trajectories chal rahi hoon. Humari apni experiments mein, humne dekha ke SWE-bench Verified pass rate mein 2% izafa hua jab API-parsed tool descriptions ka use kiya gaya bajaye manually schemas inject karne ke system prompt mein.

Developers ko chahiye ke tools ka naam clearly rakhein taa ke unka purpose samajh aaye aur "description" field mein ek clear aur detailed description add karein. Isi tarah, har tool param ke liye achhi naming aur descriptions use karni chahiye taa ke usage sahi tareeqe se ho. Agar aapka tool thoda complicated hai aur aap tool usage ke examples dena chahte hain, toh hum recommend karte hain ke aap apne system prompt mein ek # Examples section banayein aur examples wahan daalein, bajaye iske ke unhein "description" field mein daalain — jo ke thorough rehni chahiye lekin concise bhi. Examples dena faida mand ho sakta hai yeh batane ke liye ke kab tools use karne hain, user text ko tool calls ke saath include karna hai ya nahi, aur kin inputs ke liye kaunse parameters appropriate hain. Yaad rakhein ke aap “Generate Anything” ka use kar sakte hain Prompt Playground mein apne naye tool definitions ke liye ek acha starting point lene ke liye.


### Prompting-Induced Planning & Chain-of-Thought

Jaisa ke pehle bhi mention hua hai, developers optionally GPT-4.1 par banaye gaye agents ko prompt kar sakte hain taa ke wo tool calls ke darmiyan plan aur reflect karein, bajaye iske ke tools ko silently ek continuous sequence mein call karein. GPT-4.1 ek reasoning model nahi hai — iska matlab ye hai ke ye answer dene se pehle koi internal chain of thought produce nahi karta — lekin prompt mein, developer model ko induce kar sakta hai taa ke wo explicitly step-by-step plan banaye, jo ke Planning prompt component ki kisi bhi variant ke zariye kiya ja sakta hai (jaise upar dikhaya gaya hai). Isay aap aise samajh sakte hain jaise model “soch ko zubaan deta ho.”

Humari experimentation mein SWE-bench Verified agentic task par, explicit planning induce karne se pass rate mein 4% ka izafa hua.

#### Sample Prompt: SWE-bench Verified
Neeche hum woh agentic prompt share kar rahe hain jo humne SWE-bench Verified mein highest score hasil karne ke liye use kiya. Ye prompt workflow aur problem-solving strategy ke detailed instructions deta hai. Ye general pattern kisi bhi agentic task ke liye use kiya ja sakta hai.

```bash
from openai import OpenAI
import os

client = OpenAI(
    api_key=os.environ.get(
        "OPENAI_API_KEY", "<your OpenAI API key if not set as env var>"
    )
)

SYS_PROMPT_SWEBENCH = """
You will be tasked to fix an issue from an open-source repository.

Your thinking should be thorough and so it's fine if it's very long. You can think step by step before and after each action you decide to take.

You MUST iterate and keep going until the problem is solved.

You already have everything you need to solve this problem in the /testbed folder, even without internet connection. I want you to fully solve this autonomously before coming back to me.

Only terminate your turn when you are sure that the problem is solved. Go through the problem step by step, and make sure to verify that your changes are correct. NEVER end your turn without having solved the problem, and when you say you are going to make a tool call, make sure you ACTUALLY make the tool call, instead of ending your turn.

THE PROBLEM CAN DEFINITELY BE SOLVED WITHOUT THE INTERNET.

Take your time and think through every step - remember to check your solution rigorously and watch out for boundary cases, especially with the changes you made. Your solution must be perfect. If not, continue working on it. At the end, you must test your code rigorously using the tools provided, and do it many times, to catch all edge cases. If it is not robust, iterate more and make it perfect. Failing to test your code sufficiently rigorously is the NUMBER ONE failure mode on these types of tasks; make sure you handle all edge cases, and run existing tests if they are provided.

You MUST plan extensively before each function call, and reflect extensively on the outcomes of the previous function calls. DO NOT do this entire process by making function calls only, as this can impair your ability to solve the problem and think insightfully.

# Workflow

## High-Level Problem Solving Strategy

1. Understand the problem deeply. Carefully read the issue and think critically about what is required.
2. Investigate the codebase. Explore relevant files, search for key functions, and gather context.
3. Develop a clear, step-by-step plan. Break down the fix into manageable, incremental steps.
4. Implement the fix incrementally. Make small, testable code changes.
5. Debug as needed. Use debugging techniques to isolate and resolve issues.
6. Test frequently. Run tests after each change to verify correctness.
7. Iterate until the root cause is fixed and all tests pass.
8. Reflect and validate comprehensively. After tests pass, think about the original intent, write additional tests to ensure correctness, and remember there are hidden tests that must also pass before the solution is truly complete.

Refer to the detailed sections below for more information on each step.

## 1. Deeply Understand the Problem
Carefully read the issue and think hard about a plan to solve it before coding.

## 2. Codebase Investigation
- Explore relevant files and directories.
- Search for key functions, classes, or variables related to the issue.
- Read and understand relevant code snippets.
- Identify the root cause of the problem.
- Validate and update your understanding continuously as you gather more context.

## 3. Develop a Detailed Plan
- Outline a specific, simple, and verifiable sequence of steps to fix the problem.
- Break down the fix into small, incremental changes.

## 4. Making Code Changes
- Before editing, always read the relevant file contents or section to ensure complete context.
- If a patch is not applied correctly, attempt to reapply it.
- Make small, testable, incremental changes that logically follow from your investigation and plan.

## 5. Debugging
- Make code changes only if you have high confidence they can solve the problem
- When debugging, try to determine the root cause rather than addressing symptoms
- Debug for as long as needed to identify the root cause and identify a fix
- Use print statements, logs, or temporary code to inspect program state, including descriptive statements or error messages to understand what's happening
- To test hypotheses, you can also add test statements or functions
- Revisit your assumptions if unexpected behavior occurs.

## 6. Testing
- Run tests frequently using `!python3 run_tests.py` (or equivalent).
- After each change, verify correctness by running relevant tests.
- If tests fail, analyze failures and revise your patch.
- Write additional tests if needed to capture important behaviors or edge cases.
- Ensure all tests pass before finalizing.

## 7. Final Verification
- Confirm the root cause is fixed.
- Review your solution for logic correctness and robustness.
- Iterate until you are extremely confident the fix is complete and all tests pass.

## 8. Final Reflection and Additional Testing
- Reflect carefully on the original intent of the user and the problem statement.
- Think about potential edge cases or scenarios that may not be covered by existing tests.
- Write additional tests that would need to pass to fully validate the correctness of your solution.
- Run these new tests and ensure they all pass.
- Be aware that there are additional hidden tests that must also pass for the solution to be successful.
- Do not assume the task is complete just because the visible tests pass; continue refining until you are confident the fix is robust and comprehensive.
"""

PYTHON_TOOL_DESCRIPTION = """This function is used to execute Python code or terminal commands in a stateful Jupyter notebook environment. python will respond with the output of the execution or time out after 60.0 seconds. Internet access for this session is disabled. Do not make external web requests or API calls as they will fail. Just as in a Jupyter notebook, you may also execute terminal commands by calling this function with a terminal command, prefaced with an exclamation mark.

In addition, for the purposes of this task, you can call this function with an `apply_patch` command as input.  `apply_patch` effectively allows you to execute a diff/patch against a file, but the format of the diff specification is unique to this task, so pay careful attention to these instructions. To use the `apply_patch` command, you should pass a message of the following structure as "input":

%%bash
apply_patch <<"EOF"
*** Begin Patch
[YOUR_PATCH]
*** End Patch
EOF

Where [YOUR_PATCH] is the actual content of your patch, specified in the following V4A diff format.

*** [ACTION] File: [path/to/file] -> ACTION can be one of Add, Update, or Delete.
For each snippet of code that needs to be changed, repeat the following:
[context_before] -> See below for further instructions on context.
- [old_code] -> Precede the old code with a minus sign.
+ [new_code] -> Precede the new, replacement code with a plus sign.
[context_after] -> See below for further instructions on context.

For instructions on [context_before] and [context_after]:
- By default, show 3 lines of code immediately above and 3 lines immediately below each change. If a change is within 3 lines of a previous change, do NOT duplicate the first change's [context_after] lines in the second change's [context_before] lines.
- If 3 lines of context is insufficient to uniquely identify the snippet of code within the file, use the @@ operator to indicate the class or function to which the snippet belongs. For instance, we might have:
@@ class BaseClass
[3 lines of pre-context]
- [old_code]
+ [new_code]
[3 lines of post-context]

- If a code block is repeated so many times in a class or function such that even a single @@ statement and 3 lines of context cannot uniquely identify the snippet of code, you can use multiple `@@` statements to jump to the right context. For instance:

@@ class BaseClass
@@ 	def method():
[3 lines of pre-context]
- [old_code]
+ [new_code]
[3 lines of post-context]

Note, then, that we do not use line numbers in this diff format, as the context is enough to uniquely identify code. An example of a message that you might pass as "input" to this function, in order to apply a patch, is shown below.

%%bash
apply_patch <<"EOF"
*** Begin Patch
*** Update File: pygorithm/searching/binary_search.py
@@ class BaseClass
@@     def search():
-        pass
+        raise NotImplementedError()

@@ class Subclass
@@     def search():
-        pass
+        raise NotImplementedError()

*** End Patch
EOF

File references can only be relative, NEVER ABSOLUTE. After the apply_patch command is run, python will always say "Done!", regardless of whether the patch was successfully applied or not. However, you can determine if there are issue and errors by looking at any warnings or logging lines printed BEFORE the "Done!" is output.
"""

python_bash_patch_tool = {
  "type": "function",
  "name": "python",
  "description": PYTHON_TOOL_DESCRIPTION,
  "parameters": {
      "type": "object",
      "strict": True,
      "properties": {
          "input": {
              "type": "string",
              "description": " The Python code, terminal command (prefaced by exclamation mark), or apply_patch command that you wish to execute.",
          }
      },
      "required": ["input"],
  },
}

# Additional harness setup:
# - Add your repo to /testbed
# - Add your issue to the first user message
# - Note: Even though we used a single tool for python, bash, and apply_patch, we generally recommend defining more granular tools that are focused on a single function

response = client.responses.create(
    instructions=SYS_PROMPT_SWEBENCH,
    model="gpt-4.1-2025-04-14",
    tools=[python_bash_patch_tool],
    input=f"Please answer the following question:\nBug: Typerror..."
)

response.to_dict()["output"]
```

---
```bash
[{'id': 'msg_67fe92df26ac819182ffafce9ff4e4fc07c7e06242e51f8b',
  'content': [{'annotations': [],
    'text': "Thank you for the report, but “Typerror” is too vague for me to start debugging right away.\n\n**To make progress, I need to:**\n1. Find the exact error message text (e.g. `'TypeError: ...'`).\n2. Find which file and which line/function/class the error occurred in.\n3. Figure out what triggered the error (test file, usage, reproduction steps).\n4. Find the root cause and details.\n\n**Next steps:**\n- Investigate error/log/test output files for a Python `TypeError` message.\n- Examine the relevant code sections for problematic type usage.\n- If possible, reproduce the bug locally.\n\n**Plan:**\n- First, I will search for test files and log output in the `/testbed` directory that may contain the full error message and stack trace.\n\nLet’s start by listing the contents of the `/testbed` directory to look for clues.",
    'type': 'output_text'}],
  'role': 'assistant',
  'status': 'completed',
  'type': 'message'},
 {'arguments': '{"input":"!ls -l /testbed"}',
  'call_id': 'call_frnxyJgKi5TsBem0nR9Zuzdw',
  'name': 'python',
  'type': 'function_call',
  'id': 'fc_67fe92e3da7081918fc18d5c96dddc1c07c7e06242e51f8b',
  'status': 'completed'}]
  ```


### 2. Long Context
GPT-4.1 ek powerful 1M token input context window rakhta hai, jo bohat si long context tasks ke liye useful hai — jese ke structured document parsing, re-ranking, relevant information select karna aur irrelevant context ignore karna, aur multi-hop reasoning perform karna context ke zariye.

#### Optimal Context Size
Humne dekha hai ke needle-in-a-haystack evaluations mein GPT-4.1 ki performance bohat achi hoti hai, poore 1M token context tak. Complex tasks mein bhi, jahan relevant aur irrelevant code ya documents ka mix hota hai, performance strong rehti hai.
Lekin, long context performance degrade kar sakti hai jab zyada items retrieve karne hon ya jab complex reasoning chahiye hoti hai jo poore context ka state samajhne par depend karti hai (misal ke taur par graph search).

#### Tuning Context Reliance
Sochiye ke aapke sawal ka jawab dene ke liye external aur internal world knowledge ka mix kitna zaroori hai.
* Kabhi kabhi model ke liye apni khud ki knowledge use karna important hota hai taa ke wo concepts ko connect kare ya logical jumps le sake.
* Jabke kuch situations mein ye behtar hota hai ke model sirf provided context ka use kare.
```bash
# Instructions
// for internal knowledge
- Only use the documents in the provided External Context to answer the User Query. If you don't know the answer based on this context, you must respond "I don't have the information needed to answer that", even if a user insists on you answering the question.
// For internal and external knowledge
- By default, use the provided external context to answer the User Query, but if other basic knowledge is needed to answer, and you're confident in the answer, you can use some of your own knowledge to help answer the question.
```

#### Prompt Organization
Khaas taur par jab long context use ho raha ho, to instructions aur context ki placement performance ko affect kar sakti hai.
* Agar aapke prompt mein long context hai, to behtareen tareeqa ye hai ke instructions ko shuru mein aur end mein dono jagah rakha jaye. Humne dekha hai ke ye sirf upar ya sirf neeche instructions dene se zyada effective hai.
* Agar aap instructions sirf ek dafa dena pasand karte ho, to upar (beginning) par rakhna neeche (end) par rakhne se behtar kaam karta hai.

### 3. Chain of Thought
Jaisa ke upar mention hua, GPT-4.1 ek reasoning model nahi hai. Lekin model ko step by step sochnay ka prompt dena (jise “chain of thought” kaha jata hai) ek effective tareeqa ho sakta hai — taa ke model problems ko manageable parts mein todh kar solve kare aur overall output quality improve ho.
Iska ek tradeoff hai: zyada output tokens use karne ki wajah se cost aur latency barh jati hai.

Model ko agentic reasoning aur real-world problem solving mein achi training mili hai, is liye zyada prompting ki zaroorat nahi hoti taa ke wo acha perform kare.

Hum recommend karte hain ke aap apne prompt ke end par ye basic chain-of-thought instruction add karen:
```bash
First, think carefully step by step about what documents are needed to answer the query. Then, print out the TITLE and ID of each document. Then, format the IDs into a list.
```

Wahan se, aapko apna chain-of-thought (CoT) prompt behtar banana chahiye apne specific examples aur evaluations mein failures ko dekh kar, aur planning aur reasoning ki systematic ghaltiyon ko ziada explicit instructions ke zariye address kar ke.

Unconstrained CoT prompt mein strategies mein variance ho sakta hai jo model try karta hai, aur agar aapko koi aisa approach nazar aaye jo achi tarah kaam karta hai, to aap us strategy ko apne prompt mein codify kar sakte ho.

**Aam taur par ghaltiyan is wajah se hoti hain:**
   * user intent ko sahi tarah samajh na paana,
   * context ko theek se gather ya analyze na karna,
   * ya phir step by step thinking ka ghalat ya na-kaafi hona.

Is liye in cheezon ka khayal rakhein aur inhein ziada clear instructions ke zariye address karne ki koshish karein.

Neeche ek example prompt diya gaya hai jo model ko ziada methodical tareeqe se user intent analyze karne aur relevant context consider karne ki instruction deta hai, pehle jawab dene se pehle.
```bash
# Reasoning Strategy
1. Query Analysis: Break down and analyze the query until you're confident about what it might be asking. Consider the provided context to help clarify any ambiguous or confusing information.
2. Context Analysis: Carefully select and analyze a large set of potentially relevant documents. Optimize for recall - it's okay if some are irrelevant, but the correct documents must be in this list, otherwise your final answer will be wrong. Analysis steps for each:
	a. Analysis: An analysis of how it may or may not be relevant to answering the query.
	b. Relevance rating: [high, medium, low, none]
3. Synthesis: summarize which documents are most relevant and why, including all documents with a relevance rating of medium or higher.

# User Question
{user_question}

# External Context
{external_context}

First, think carefully step by step about what documents are needed to answer the query, closely adhering to the provided Reasoning Strategy. Then, print out the TITLE and ID of each document. Then, format the IDs into a list.
```

### 4. Instruction Following
GPT-4.1 ki instruction-following performance bohat zabardast hai, jise developers apne specific use cases ke liye outputs ko bilkul apne mutabiq shape aur control karne ke liye use kar sakte hain.

Developers aksar extensively prompt dete hain jisme agentic reasoning steps, response tone aur voice, tool calling information, output formatting, avoid karne wale topics, aur bohat si aur cheezein shaamil hoti hain.

Lekin, kyunke ye model instructions ko zyada literally follow karta hai, developers ko aksar zyada explicit specification deni parti hai — ke kya karna hai aur kya nahi karna.

Iske ilawa, jo prompts pehle ke models ke liye optimize kiye gaye thay wo hamesha is model ke sath immediately kaam nahi karenge, kyunke ab instructions ko bohat closely follow kiya jata hai aur implicit rules itni strongly infer nahi hote.


#### Recommended Workflow
1. Start with an overall “Response Rules” or “Instructions” section with high-level guidance and bullet points.
2. If you’d like to change a more specific behavior, add a section to specify more details for that category, like # Sample Phrases.
3. If there are specific steps you’d like the model to follow in its workflow, add an ordered list and instruct the model to follow these steps.
4. If behavior still isn’t working as expected:
    1. Check for conflicting, underspecified, or wrong instructions and examples. If there are conflicting instructions, GPT-4. tends to follow the one closer to the end of the prompt.
    2. Add examples that demonstrate desired behavior; ensure that any important behavior demonstrated in your examples are also cited in your rules.
    3. It’s generally not necessary to use all-caps or other incentives like bribes or tips. We recommend starting without these, and only reaching for these if necessary for your particular prompt. Note that if your existing prompts include these techniques, it could cause GPT-4.1 to pay attention to it too strictly.

*Note that using your preferred AI-powered IDE can be very helpful for iterating on prompts, including checking for consistency or conflicts, adding examples, or making cohesive updates like adding an instruction and updating instructions to demonstrate that instruction*

#### Common Failure Modes
These failure modes are not unique to GPT-4.1, but we share them here for general awareness and ease of debugging.

* Instructing a model to always follow a specific behavior can occasionally induce adverse effects. For instance, if told “you must call a tool before responding to the user,” models may hallucinate tool inputs or call the tool with null values if they do not have enough information. Adding “if you don’t have enough information to call the tool, ask the user for the information you need” should mitigate this.
* When provided sample phrases, models can use those quotes verbatim and start to sound repetitive to users. Ensure you instruct the model to vary them as necessary.
* Without specific instructions, some models can be eager to provide additional prose to explain their decisions, or output more formatting in responses than may be desired. Provide instructions and potentially examples to help mitigate.

#### Example Prompt: Customer Service
Ye ek fictional customer service agent ke liye best practices ko demonstrate karta hai. Rules ki diversity, unki specificity, zyada tafseel ke liye additional sections ka use, aur ek example dekhein jo precise behavior dikhata hai aur pehle diye gaye sab rules ko incorporate karta hai.

Neeche diya gaya notebook cell run karke try karein — aapko ek user message aur ek tool call dono dikhai denge. User message shuru hoga ek greeting se, phir apna jawab echo karega, aur phir ye mention karega ke wo tool call karne wala hai.

Instructions ko change karke aap model ke behavior ko shape kar sakte ho, ya phir dusre user messages try karke instruction-following performance test kar sakte ho.

```bash
SYS_PROMPT_CUSTOMER_SERVICE = """You are a helpful customer service agent working for NewTelco, helping a user efficiently fulfill their request while adhering closely to provided guidelines.

# Instructions
- Always greet the user with "Hi, you've reached NewTelco, how can I help you?"
- Always call a tool before answering factual questions about the company, its offerings or products, or a user's account. Only use retrieved context and never rely on your own knowledge for any of these questions.
    - However, if you don't have enough information to properly call the tool, ask the user for the information you need.
- Escalate to a human if the user requests.
- Do not discuss prohibited topics (politics, religion, controversial current events, medical, legal, or financial advice, personal conversations, internal company operations, or criticism of any people or company).
- Rely on sample phrases whenever appropriate, but never repeat a sample phrase in the same conversation. Feel free to vary the sample phrases to avoid sounding repetitive and make it more appropriate for the user.
- Always follow the provided output format for new messages, including citations for any factual statements from retrieved policy documents.
- If you're going to call a tool, always message the user with an appropriate message before and after calling the tool.
- Maintain a professional and concise tone in all responses, and use emojis between sentences.
- If you've resolved the user's request, ask if there's anything else you can help with

# Precise Response Steps (for each response)
1. If necessary, call tools to fulfill the user's desired action. Always message the user before and after calling a tool to keep them in the loop.
2. In your response to the user
    a. Use active listening and echo back what you heard the user ask for.
    b. Respond appropriately given the above guidelines.

# Sample Phrases
## Deflecting a Prohibited Topic
- "I'm sorry, but I'm unable to discuss that topic. Is there something else I can help you with?"
- "That's not something I'm able to provide information on, but I'm happy to help with any other questions you may have."

## Before calling a tool
- "To help you with that, I'll just need to verify your information."
- "Let me check that for you—one moment, please."
- "I'll retrieve the latest details for you now."

## After calling a tool
- "Okay, here's what I found: [response]"
- "So here's what I found: [response]"

# Output Format
- Always include your final response to the user.
- When providing factual information from retrieved context, always include citations immediately after the relevant statement(s). Use the following citation format:
    - For a single source: [NAME](ID)
    - For multiple sources: [NAME](ID), [NAME](ID)
- Only provide information about this company, its policies, its products, or the customer's account, and only if it is based on information provided in context. Do not answer questions outside this scope.

# Example
## User
Can you tell me about your family plan options?

## Assistant Response 1
### Message
"Hi, you've reached NewTelco, how can I help you? 😊🎉\n\nYou'd like to know about our family plan options. 🤝 Let me check that for you—one moment, please. 🚀"

### Tool Calls
lookup_policy_document(topic="family plan options")

// After tool call, the assistant would follow up with:

## Assistant Response 2 (after tool call)
### Message
"Okay, here's what I found: 🎉 Our family plan allows up to 5 lines with shared data and a 10% discount for each additional line [Family Plan Policy](ID-010). 📱 Is there anything else I can help you with today? 😊"
"""

get_policy_doc = {
    "type": "function",
    "name": "lookup_policy_document",
    "description": "Tool to look up internal documents and policies by topic or keyword.",
    "parameters": {
        "strict": True,
        "type": "object",
        "properties": {
            "topic": {
                "type": "string",
                "description": "The topic or keyword to search for in company policies or documents.",
            },
        },
        "required": ["topic"],
        "additionalProperties": False,
    },
}

get_user_acct = {
    "type": "function",
    "name": "get_user_account_info",
    "description": "Tool to get user account information",
    "parameters": {
        "strict": True,
        "type": "object",
        "properties": {
            "phone_number": {
                "type": "string",
                "description": "Formatted as '(xxx) xxx-xxxx'",
            },
        },
        "required": ["phone_number"],
        "additionalProperties": False,
    },
}

response = client.responses.create(
    instructions=SYS_PROMPT_CUSTOMER_SERVICE,
    model="gpt-4.1-2025-04-14",
    tools=[get_policy_doc, get_user_acct],
    input="How much will it cost for international service? I'm traveling to France.",
    # input="Why was my last bill so high?"
)

response.to_dict()["output"]
```
---
```bash
[{'id': 'msg_67fe92d431548191b7ca6cd604b4784b06efc5beb16b3c5e',
  'content': [{'annotations': [],
    'text': "Hi, you've reached NewTelco, how can I help you? 🌍✈️\n\nYou'd like to know the cost of international service while traveling to France. 🇫🇷 Let me check the latest details for you—one moment, please. 🕑",
    'type': 'output_text'}],
  'role': 'assistant',
  'status': 'completed',
  'type': 'message'},
 {'arguments': '{"topic":"international service cost France"}',
  'call_id': 'call_cF63DLeyhNhwfdyME3ZHd0yo',
  'name': 'lookup_policy_document',
  'type': 'function_call',
  'id': 'fc_67fe92d5d6888191b6cd7cf57f707e4606efc5beb16b3c5e',
  'status': 'completed'}]
```

### 5. General Advice
#### Prompt Structure
For reference, here is a good starting point for structuring your prompts.
```bash
# Role and Objective
# Instructions
## Sub-categories for more detailed instructions
# Reasoning Steps
# Output Format
# Examples
## Example 1
# Context
# Final instructions and prompt to think step by step
```
Add or remove sections to suit your needs, and experiment to determine what’s optimal for your usage.

#### Delimiters
Yahan kuch general guidelines di gayi hain apne prompt ke liye best delimiters select karne ke liye. Long Context section ko bhi dekhein is context type ke liye special considerations ke liye.

1. **Markdown:** Hum recommend karte hain ke aap yahan se shuru karein, aur major sections aur subsections ke liye markdown titles use karein (deep hierarchy ke sath, H4+ tak). Code ko wrap karne ke liye inline backticks ya backtick blocks ka use karein, aur zarurat ke mutabiq numbered ya bulleted lists ka istemal karein.

2. **XML:** Ye bhi bohat acha perform karte hain, aur is model ke sath XML mein di gayi information par zyada achi tarah se amal hota hai. XML convenient hai kyunke iske zariye aap ek section ko start aur end ke sath clearly wrap kar sakte ho, tags mein metadata add kar sakte ho extra context ke liye, aur nesting enable kar sakte ho. Neeche ek example diya gaya hai XML tags use kar ke ek example section mein examples nest karne ka, jisme inputs aur outputs dono diye gaye hain:
```bash
<examples>
<example1 type="Abbreviate">
<input>San Francisco</input>
<output>- SF</output>
</example1>
</examples>
```
3. **JSON** bohat structured hota hai aur model isay achi tarah samajhta hai, khaas taur par coding contexts mein. Lekin, ye zyada verbose ho sakta hai aur character escaping ki zaroorat parti hai jo overhead barha deti hai.

Guidance khaas taur par jab aap bohat saare documents ya files input context mein add kar rahe ho:

* XML ne humare long context testing mein acha perform kiya. <br>
Example: <doc id='1' title='The Fox'>The quick brown fox jumps over the lazy dog</doc>

* Ye format, jo Lee et al. (ref) ne propose kiya, ne bhi humare long context testing mein acha perform kiya.<br>
Example: ID: 1 | TITLE: The Fox | CONTENT: The quick brown fox jumps over the lazy dog

* JSON ne khaas taur par poor performance dikhayi.<br>
Example: [{'id': 1, 'title': 'The Fox', 'content': 'The quick brown fox jumped over the lazy dog'}]

Model ko train kiya gaya hai ke wo variety of formats mein structure ko robustly samajh sake. Aam taur par, apni judgement use karein aur sochiye ke kya clear information provide karega aur model ke liye “stand out” karega.
Misal ke taur par, agar aap aise documents retrieve kar rahe hain jisme bohat saari XML hai, to XML-based delimiter shayad utna effective na ho

#### Caveats
Kuch isolated cases mein humne dekha hai ke model bohat lambi, repetitive outputs produce karne mein resistant hota hai, jaise ke hundreds of items ko ek ek karke analyze karna. Agar ye aapke use case ke liye zaroori hai, to model ko strongly instruct karein ke wo ye information poori tarah output kare, aur problem ko break down karne ya zyada concise approach use karne ka bhi sochiye.

Humne kuch rare instances dekhe hain jahan parallel tool calls incorrect hui hain. Hum advise karte hain ke isko test karein, aur agar issues nazar aaye to parallel_tool_calls param ko false set karne ka bhi sochiye.


### Appendix: Generating and Applying File Diffs
Developers ne hume feedback diya hai ke accurate aur well-formed diff generation ek critical capability hai jo coding-related tasks ko power karti hai.

Is liye, GPT-4.1 family ne previous GPT models ke muqable mein diff capabilities ko substantially improve kiya hai.

Aur jabke GPT-4.1 strong performance rakhta hai diffs generate karne mein kisi bhi format ke liye, jab clear instructions aur examples diye jayein, hum yahan ek recommended diff format open-source kar rahe hain, jisme model extensively train hua hai.

Humari umeed hai ke khaas taur par developers ke liye jo abhi start kar rahe hain, ye diffs create karne mein guesswork kaafi had tak kam kar dega.

### Apply Patch
See the example below for a prompt that applies our recommended tool call correctly.
```bash
APPLY_PATCH_TOOL_DESC = """This is a custom utility that makes it more convenient to add, remove, move, or edit code files. `apply_patch` effectively allows you to execute a diff/patch against a file, but the format of the diff specification is unique to this task, so pay careful attention to these instructions. To use the `apply_patch` command, you should pass a message of the following structure as "input":

%%bash
apply_patch <<"EOF"
*** Begin Patch
[YOUR_PATCH]
*** End Patch
EOF

Where [YOUR_PATCH] is the actual content of your patch, specified in the following V4A diff format.

*** [ACTION] File: [path/to/file] -> ACTION can be one of Add, Update, or Delete.
For each snippet of code that needs to be changed, repeat the following:
[context_before] -> See below for further instructions on context.
- [old_code] -> Precede the old code with a minus sign.
+ [new_code] -> Precede the new, replacement code with a plus sign.
[context_after] -> See below for further instructions on context.

For instructions on [context_before] and [context_after]:
- By default, show 3 lines of code immediately above and 3 lines immediately below each change. If a change is within 3 lines of a previous change, do NOT duplicate the first change’s [context_after] lines in the second change’s [context_before] lines.
- If 3 lines of context is insufficient to uniquely identify the snippet of code within the file, use the @@ operator to indicate the class or function to which the snippet belongs. For instance, we might have:
@@ class BaseClass
[3 lines of pre-context]
- [old_code]
+ [new_code]
[3 lines of post-context]

- If a code block is repeated so many times in a class or function such that even a single @@ statement and 3 lines of context cannot uniquely identify the snippet of code, you can use multiple `@@` statements to jump to the right context. For instance:

@@ class BaseClass
@@ 	def method():
[3 lines of pre-context]
- [old_code]
+ [new_code]
[3 lines of post-context]

Note, then, that we do not use line numbers in this diff format, as the context is enough to uniquely identify code. An example of a message that you might pass as "input" to this function, in order to apply a patch, is shown below.

%%bash
apply_patch <<"EOF"
*** Begin Patch
*** Update File: pygorithm/searching/binary_search.py
@@ class BaseClass
@@     def search():
-          pass
+          raise NotImplementedError()

@@ class Subclass
@@     def search():
-          pass
+          raise NotImplementedError()

*** End Patch
EOF
"""

APPLY_PATCH_TOOL = {
    "name": "apply_patch",
    "description": APPLY_PATCH_TOOL_DESC,
    "parameters": {
        "type": "object",
        "properties": {
            "input": {
                "type": "string",
                "description": " The apply_patch command that you wish to execute.",
            }
        },
        "required": ["input"],
    },
}
```

#### Reference Implementation: apply_patch.py
Yahan apply_patch tool ka ek reference implementation diya gaya hai jo humne model training ke hissa ke taur par use kiya.

Aapko isay executable banana hoga aur shell se apply_patch ke naam se available karna hoga jahan model commands execute karega.
```bash
#!/usr/bin/env python3

"""
A self-contained **pure-Python 3.9+** utility for applying human-readable
“pseudo-diff” patch files to a collection of text files.
"""

from __future__ import annotations

import pathlib
from dataclasses import dataclass, field
from enum import Enum
from typing import (
    Callable,
    Dict,
    List,
    Optional,
    Tuple,
    Union,
)


# --------------------------------------------------------------------------- #
#  Domain objects
# --------------------------------------------------------------------------- #
class ActionType(str, Enum):
    ADD = "add"
    DELETE = "delete"
    UPDATE = "update"


@dataclass
class FileChange:
    type: ActionType
    old_content: Optional[str] = None
    new_content: Optional[str] = None
    move_path: Optional[str] = None


@dataclass
class Commit:
    changes: Dict[str, FileChange] = field(default_factory=dict)


# --------------------------------------------------------------------------- #
#  Exceptions
# --------------------------------------------------------------------------- #
class DiffError(ValueError):
    """Any problem detected while parsing or applying a patch."""


# --------------------------------------------------------------------------- #
#  Helper dataclasses used while parsing patches
# --------------------------------------------------------------------------- #
@dataclass
class Chunk:
    orig_index: int = -1
    del_lines: List[str] = field(default_factory=list)
    ins_lines: List[str] = field(default_factory=list)


@dataclass
class PatchAction:
    type: ActionType
    new_file: Optional[str] = None
    chunks: List[Chunk] = field(default_factory=list)
    move_path: Optional[str] = None


@dataclass
class Patch:
    actions: Dict[str, PatchAction] = field(default_factory=dict)


# --------------------------------------------------------------------------- #
#  Patch text parser
# --------------------------------------------------------------------------- #
@dataclass
class Parser:
    current_files: Dict[str, str]
    lines: List[str]
    index: int = 0
    patch: Patch = field(default_factory=Patch)
    fuzz: int = 0

    # ------------- low-level helpers -------------------------------------- #
    def _cur_line(self) -> str:
        if self.index >= len(self.lines):
            raise DiffError("Unexpected end of input while parsing patch")
        return self.lines[self.index]

    @staticmethod
    def _norm(line: str) -> str:
        """Strip CR so comparisons work for both LF and CRLF input."""
        return line.rstrip("\r")

    # ------------- scanning convenience ----------------------------------- #
    def is_done(self, prefixes: Optional[Tuple[str, ...]] = None) -> bool:
        if self.index >= len(self.lines):
            return True
        if (
            prefixes
            and len(prefixes) > 0
            and self._norm(self._cur_line()).startswith(prefixes)
        ):
            return True
        return False

    def startswith(self, prefix: Union[str, Tuple[str, ...]]) -> bool:
        return self._norm(self._cur_line()).startswith(prefix)

    def read_str(self, prefix: str) -> str:
        """
        Consume the current line if it starts with *prefix* and return the text
        **after** the prefix.  Raises if prefix is empty.
        """
        if prefix == "":
            raise ValueError("read_str() requires a non-empty prefix")
        if self._norm(self._cur_line()).startswith(prefix):
            text = self._cur_line()[len(prefix) :]
            self.index += 1
            return text
        return ""

    def read_line(self) -> str:
        """Return the current raw line and advance."""
        line = self._cur_line()
        self.index += 1
        return line

    # ------------- public entry point -------------------------------------- #
    def parse(self) -> None:
        while not self.is_done(("*** End Patch",)):
            # ---------- UPDATE ---------- #
            path = self.read_str("*** Update File: ")
            if path:
                if path in self.patch.actions:
                    raise DiffError(f"Duplicate update for file: {path}")
                move_to = self.read_str("*** Move to: ")
                if path not in self.current_files:
                    raise DiffError(f"Update File Error - missing file: {path}")
                text = self.current_files[path]
                action = self._parse_update_file(text)
                action.move_path = move_to or None
                self.patch.actions[path] = action
                continue

            # ---------- DELETE ---------- #
            path = self.read_str("*** Delete File: ")
            if path:
                if path in self.patch.actions:
                    raise DiffError(f"Duplicate delete for file: {path}")
                if path not in self.current_files:
                    raise DiffError(f"Delete File Error - missing file: {path}")
                self.patch.actions[path] = PatchAction(type=ActionType.DELETE)
                continue

            # ---------- ADD ---------- #
            path = self.read_str("*** Add File: ")
            if path:
                if path in self.patch.actions:
                    raise DiffError(f"Duplicate add for file: {path}")
                if path in self.current_files:
                    raise DiffError(f"Add File Error - file already exists: {path}")
                self.patch.actions[path] = self._parse_add_file()
                continue

            raise DiffError(f"Unknown line while parsing: {self._cur_line()}")

        if not self.startswith("*** End Patch"):
            raise DiffError("Missing *** End Patch sentinel")
        self.index += 1  # consume sentinel

    # ------------- section parsers ---------------------------------------- #
    def _parse_update_file(self, text: str) -> PatchAction:
        action = PatchAction(type=ActionType.UPDATE)
        lines = text.split("\n")
        index = 0
        while not self.is_done(
            (
                "*** End Patch",
                "*** Update File:",
                "*** Delete File:",
                "*** Add File:",
                "*** End of File",
            )
        ):
            def_str = self.read_str("@@ ")
            section_str = ""
            if not def_str and self._norm(self._cur_line()) == "@@":
                section_str = self.read_line()

            if not (def_str or section_str or index == 0):
                raise DiffError(f"Invalid line in update section:\n{self._cur_line()}")

            if def_str.strip():
                found = False
                if def_str not in lines[:index]:
                    for i, s in enumerate(lines[index:], index):
                        if s == def_str:
                            index = i + 1
                            found = True
                            break
                if not found and def_str.strip() not in [
                    s.strip() for s in lines[:index]
                ]:
                    for i, s in enumerate(lines[index:], index):
                        if s.strip() == def_str.strip():
                            index = i + 1
                            self.fuzz += 1
                            found = True
                            break

            next_ctx, chunks, end_idx, eof = peek_next_section(self.lines, self.index)
            new_index, fuzz = find_context(lines, next_ctx, index, eof)
            if new_index == -1:
                ctx_txt = "\n".join(next_ctx)
                raise DiffError(
                    f"Invalid {'EOF ' if eof else ''}context at {index}:\n{ctx_txt}"
                )
            self.fuzz += fuzz
            for ch in chunks:
                ch.orig_index += new_index
                action.chunks.append(ch)
            index = new_index + len(next_ctx)
            self.index = end_idx
        return action

    def _parse_add_file(self) -> PatchAction:
        lines: List[str] = []
        while not self.is_done(
            ("*** End Patch", "*** Update File:", "*** Delete File:", "*** Add File:")
        ):
            s = self.read_line()
            if not s.startswith("+"):
                raise DiffError(f"Invalid Add File line (missing '+'): {s}")
            lines.append(s[1:])  # strip leading '+'
        return PatchAction(type=ActionType.ADD, new_file="\n".join(lines))


# --------------------------------------------------------------------------- #
#  Helper functions
# --------------------------------------------------------------------------- #
def find_context_core(
    lines: List[str], context: List[str], start: int
) -> Tuple[int, int]:
    if not context:
        return start, 0

    for i in range(start, len(lines)):
        if lines[i : i + len(context)] == context:
            return i, 0
    for i in range(start, len(lines)):
        if [s.rstrip() for s in lines[i : i + len(context)]] == [
            s.rstrip() for s in context
        ]:
            return i, 1
    for i in range(start, len(lines)):
        if [s.strip() for s in lines[i : i + len(context)]] == [
            s.strip() for s in context
        ]:
            return i, 100
    return -1, 0


def find_context(
    lines: List[str], context: List[str], start: int, eof: bool
) -> Tuple[int, int]:
    if eof:
        new_index, fuzz = find_context_core(lines, context, len(lines) - len(context))
        if new_index != -1:
            return new_index, fuzz
        new_index, fuzz = find_context_core(lines, context, start)
        return new_index, fuzz + 10_000
    return find_context_core(lines, context, start)


def peek_next_section(
    lines: List[str], index: int
) -> Tuple[List[str], List[Chunk], int, bool]:
    old: List[str] = []
    del_lines: List[str] = []
    ins_lines: List[str] = []
    chunks: List[Chunk] = []
    mode = "keep"
    orig_index = index

    while index < len(lines):
        s = lines[index]
        if s.startswith(
            (
                "@@",
                "*** End Patch",
                "*** Update File:",
                "*** Delete File:",
                "*** Add File:",
                "*** End of File",
            )
        ):
            break
        if s == "***":
            break
        if s.startswith("***"):
            raise DiffError(f"Invalid Line: {s}")
        index += 1

        last_mode = mode
        if s == "":
            s = " "
        if s[0] == "+":
            mode = "add"
        elif s[0] == "-":
            mode = "delete"
        elif s[0] == " ":
            mode = "keep"
        else:
            raise DiffError(f"Invalid Line: {s}")
        s = s[1:]

        if mode == "keep" and last_mode != mode:
            if ins_lines or del_lines:
                chunks.append(
                    Chunk(
                        orig_index=len(old) - len(del_lines),
                        del_lines=del_lines,
                        ins_lines=ins_lines,
                    )
                )
            del_lines, ins_lines = [], []

        if mode == "delete":
            del_lines.append(s)
            old.append(s)
        elif mode == "add":
            ins_lines.append(s)
        elif mode == "keep":
            old.append(s)

    if ins_lines or del_lines:
        chunks.append(
            Chunk(
                orig_index=len(old) - len(del_lines),
                del_lines=del_lines,
                ins_lines=ins_lines,
            )
        )

    if index < len(lines) and lines[index] == "*** End of File":
        index += 1
        return old, chunks, index, True

    if index == orig_index:
        raise DiffError("Nothing in this section")
    return old, chunks, index, False


# --------------------------------------------------------------------------- #
#  Patch → Commit and Commit application
# --------------------------------------------------------------------------- #
def _get_updated_file(text: str, action: PatchAction, path: str) -> str:
    if action.type is not ActionType.UPDATE:
        raise DiffError("_get_updated_file called with non-update action")
    orig_lines = text.split("\n")
    dest_lines: List[str] = []
    orig_index = 0

    for chunk in action.chunks:
        if chunk.orig_index > len(orig_lines):
            raise DiffError(
                f"{path}: chunk.orig_index {chunk.orig_index} exceeds file length"
            )
        if orig_index > chunk.orig_index:
            raise DiffError(
                f"{path}: overlapping chunks at {orig_index} > {chunk.orig_index}"
            )

        dest_lines.extend(orig_lines[orig_index : chunk.orig_index])
        orig_index = chunk.orig_index

        dest_lines.extend(chunk.ins_lines)
        orig_index += len(chunk.del_lines)

    dest_lines.extend(orig_lines[orig_index:])
    return "\n".join(dest_lines)


def patch_to_commit(patch: Patch, orig: Dict[str, str]) -> Commit:
    commit = Commit()
    for path, action in patch.actions.items():
        if action.type is ActionType.DELETE:
            commit.changes[path] = FileChange(
                type=ActionType.DELETE, old_content=orig[path]
            )
        elif action.type is ActionType.ADD:
            if action.new_file is None:
                raise DiffError("ADD action without file content")
            commit.changes[path] = FileChange(
                type=ActionType.ADD, new_content=action.new_file
            )
        elif action.type is ActionType.UPDATE:
            new_content = _get_updated_file(orig[path], action, path)
            commit.changes[path] = FileChange(
                type=ActionType.UPDATE,
                old_content=orig[path],
                new_content=new_content,
                move_path=action.move_path,
            )
    return commit


# --------------------------------------------------------------------------- #
#  User-facing helpers
# --------------------------------------------------------------------------- #
def text_to_patch(text: str, orig: Dict[str, str]) -> Tuple[Patch, int]:
    lines = text.splitlines()  # preserves blank lines, no strip()
    if (
        len(lines) < 2
        or not Parser._norm(lines[0]).startswith("*** Begin Patch")
        or Parser._norm(lines[-1]) != "*** End Patch"
    ):
        raise DiffError("Invalid patch text - missing sentinels")

    parser = Parser(current_files=orig, lines=lines, index=1)
    parser.parse()
    return parser.patch, parser.fuzz


def identify_files_needed(text: str) -> List[str]:
    lines = text.splitlines()
    return [
        line[len("*** Update File: ") :]
        for line in lines
        if line.startswith("*** Update File: ")
    ] + [
        line[len("*** Delete File: ") :]
        for line in lines
        if line.startswith("*** Delete File: ")
    ]


def identify_files_added(text: str) -> List[str]:
    lines = text.splitlines()
    return [
        line[len("*** Add File: ") :]
        for line in lines
        if line.startswith("*** Add File: ")
    ]


# --------------------------------------------------------------------------- #
#  File-system helpers
# --------------------------------------------------------------------------- #
def load_files(paths: List[str], open_fn: Callable[[str], str]) -> Dict[str, str]:
    return {path: open_fn(path) for path in paths}


def apply_commit(
    commit: Commit,
    write_fn: Callable[[str, str], None],
    remove_fn: Callable[[str], None],
) -> None:
    for path, change in commit.changes.items():
        if change.type is ActionType.DELETE:
            remove_fn(path)
        elif change.type is ActionType.ADD:
            if change.new_content is None:
                raise DiffError(f"ADD change for {path} has no content")
            write_fn(path, change.new_content)
        elif change.type is ActionType.UPDATE:
            if change.new_content is None:
                raise DiffError(f"UPDATE change for {path} has no new content")
            target = change.move_path or path
            write_fn(target, change.new_content)
            if change.move_path:
                remove_fn(path)


def process_patch(
    text: str,
    open_fn: Callable[[str], str],
    write_fn: Callable[[str, str], None],
    remove_fn: Callable[[str], None],
) -> str:
    if not text.startswith("*** Begin Patch"):
        raise DiffError("Patch text must start with *** Begin Patch")
    paths = identify_files_needed(text)
    orig = load_files(paths, open_fn)
    patch, _fuzz = text_to_patch(text, orig)
    commit = patch_to_commit(patch, orig)
    apply_commit(commit, write_fn, remove_fn)
    return "Done!"


# --------------------------------------------------------------------------- #
#  Default FS helpers
# --------------------------------------------------------------------------- #
def open_file(path: str) -> str:
    with open(path, "rt", encoding="utf-8") as fh:
        return fh.read()


def write_file(path: str, content: str) -> None:
    target = pathlib.Path(path)
    target.parent.mkdir(parents=True, exist_ok=True)
    with target.open("wt", encoding="utf-8") as fh:
        fh.write(content)


def remove_file(path: str) -> None:
    pathlib.Path(path).unlink(missing_ok=True)


# --------------------------------------------------------------------------- #
#  CLI entry-point
# --------------------------------------------------------------------------- #
def main() -> None:
    import sys

    patch_text = sys.stdin.read()
    if not patch_text:
        print("Please pass patch text through stdin", file=sys.stderr)
        return
    try:
        result = process_patch(patch_text, open_file, write_file, remove_file)
    except DiffError as exc:
        print(exc, file=sys.stderr)
        return
    print(result)


if __name__ == "__main__":
    main()
```

#### Other Effective Diff Formats

Agar aap different diff format use karna chahte hain, to humne testing mein dekha ke:
* SEARCH/REPLACE diff format jo Aider ke polyglot benchmark mein use hota hai,
* aur ek pseudo-XML format jisme internal escaping nahi hoti,
dono ne high success rates dikhaye.

**Ye diff formats do key aspects share karte hain:**
* Ye line numbers use nahi karte,
* Ye exact code to be replaced aur exact code jo replace karega dono provide karte hain, aur dono ke darmiyan clear delimiters hote hain.

```bash
SEARCH_REPLACE_DIFF_EXAMPLE = """
path/to/file.py

>>>>>>> SEARCH
def search():
    pass
=======
def search():
   raise NotImplementedError()
<<<<<<< REPLACE
"""

PSEUDO_XML_DIFF_EXAMPLE = """
<edit>
<file>
path/to/file.py
</file>
<old_code>
def search():
    pass
</old_code>
<new_code>
def search():
   raise NotImplementedError()
</new_code>
</edit>
"""
```


