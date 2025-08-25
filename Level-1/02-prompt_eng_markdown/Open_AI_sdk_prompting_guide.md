
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