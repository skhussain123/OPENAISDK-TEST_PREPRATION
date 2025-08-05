# GPT-4.1 Prompting Guide MCQs
## Multiple-Choice Questions

1. **What is a key difference in how GPT-4.1 handles instructions compared to its predecessors?**  
   a) It infers user intent more liberally  
   b) It follows instructions more literally and closely  
   c) It ignores system prompts  
   d) It requires fewer instructions  
   **Correct Answer**: b  
   **Explanation**: GPT-4.1 is trained to follow instructions more closely and literally than its predecessors, which tended to infer intent more liberally (Section: Introduction).

2. **What is the recommended approach if GPT-4.1’s behavior differs from expectations?**  
   a) Use all-caps instructions  
   b) Add a single sentence clarifying desired behavior  
   c) Ignore the issue and retry  
   d) Use a different model  
   **Correct Answer**: b  
   **Explanation**: A single sentence firmly clarifying desired behavior is almost always sufficient to steer GPT-4.1 (Section: Introduction).

3. **What is the pass rate of GPT-4.1 on SWE-bench Verified for non-reasoning models?**  
   a) 35%  
   b) 45%  
   c) 55%  
   d) 65%  
   **Correct Answer**: c  
   **Explanation**: GPT-4.1 achieves a 55% pass rate on SWE-bench Verified, as noted in the agentic workflows section (Section 1: Agentic Workflows).

4. **Which system prompt reminder ensures GPT-4.1 continues until the user’s query is resolved?**  
   a) Tool-calling  
   b) Persistence  
   c) Planning  
   d) Reflection  
   **Correct Answer**: b  
   **Explanation**: The persistence reminder ensures the model continues until the query is completely resolved (Section 1: System Prompt Reminders).

5. **What does the tool-calling reminder prevent GPT-4.1 from doing?**  
   a) Planning excessively  
   b) Hallucinating or guessing answers  
   c) Terminating early  
   d) Using external context  
   **Correct Answer**: b  
   **Explanation**: The tool-calling reminder reduces the likelihood of hallucinating or guessing by encouraging tool use (Section 1: System Prompt Reminders).

6. **What is the purpose of the optional planning reminder in agentic prompts?**  
   a) To terminate the model early  
   b) To ensure explicit planning and reflection between tool calls  
   c) To reduce tool usage  
   d) To simplify instructions  
   **Correct Answer**: b  
   **Explanation**: The planning reminder ensures explicit planning and reflection instead of chaining tool calls silently (Section 1: System Prompt Reminders).

7. **How much did the three system prompt reminders improve the SWE-bench Verified score?**  
   a) 10%  
   b) 15%  
   c) 20%  
   d) 25%  
   **Correct Answer**: c  
   **Explanation**: The three reminders increased the SWE-bench Verified score by close to 20% (Section 1: System Prompt Reminders).

8. **What is the recommended method for passing tools to GPT-4.1?**  
   a) Manually inject tool descriptions into the prompt  
   b) Use the tools field in the OpenAI API request  
   c) Avoid using tools altogether  
   d) Use a separate parser for tool calls  
   **Correct Answer**: b  
   **Explanation**: Using the tools field minimizes errors and ensures the model remains in distribution (Section 1: Tool Calls).

9. **What was the observed improvement in SWE-bench Verified pass rate when using API-parsed tool descriptions?**  
   a) 1%  
   b) 2%  
   c) 3%  
   d) 4%  
   **Correct Answer**: b  
   **Explanation**: A 2% increase in pass rate was observed when using API-parsed tool descriptions (Section 1: Tool Calls).

10. **Where should examples of tool usage be placed in a prompt?**  
    a) In the tool description field  
    b) In an # Examples section in the system prompt  
    c) In the user input  
    d) In the context section  
    **Correct Answer**: b  
    **Explanation**: Examples should be placed in an # Examples section to keep the description field concise (Section 1: Tool Calls).

11. **What is the benefit of inducing explicit planning in GPT-4.1 for SWE-bench Verified tasks?**  
    a) Reduces latency  
    b) Increases pass rate by 4%  
    c) Eliminates tool calls  
    d) Simplifies the prompt  
    **Correct Answer**: b  
    **Explanation**: Inducing explicit planning increased the pass rate by 4% (Section 1: Prompting-Induced Planning & Chain-of-Thought).

12. **What is the context window size of GPT-4.1?**  
    a) 512K tokens  
    b) 1M tokens  
    c) 2M tokens  
    d) 128K tokens  
    **Correct Answer**: b  
    **Explanation**: GPT-4.1 has a 1M token input context window (Section 2: Long Context).

13. **What type of task is GPT-4.1 particularly useful for due to its context window?**  
    a) Short text generation  
    b) Structured document parsing  
    c) Image generation  
    d) Audio processing  
    **Correct Answer**: b  
    **Explanation**: The 1M token context window is useful for tasks like structured document parsing (Section 2: Long Context).

14. **What can degrade GPT-4.1’s long context performance?**  
    a) Using short prompts  
    b) Complex reasoning requiring knowledge of the entire context  
    c) Avoiding tool calls  
    d) Using markdown delimiters  
    **Correct Answer**: b  
    **Explanation**: Performance can degrade with complex reasoning tasks like graph search over the entire context (Section 2: Optimal Context Size).

15. **What should GPT-4.1 do if it lacks context to answer a query?**  
    a) Use its internal knowledge  
    b) Respond “I don’t have the information needed to answer that”  
    c) Guess the answer  
    d) Ignore the query  
    **Correct Answer**: b  
    **Explanation**: If instructed to use only provided context, GPT-4.1 should respond that it lacks information (Section 2: Tuning Context Reliance).

16. **Where should instructions be placed in a long context prompt for optimal performance?**  
    a) Only at the beginning  
    b) Only at the end  
    c) Both at the beginning and end  
    d) In the middle of the context  
    **Correct Answer**: c  
    **Explanation**: Placing instructions at both the beginning and end performs better (Section 2: Prompt Organization).

17. **What is a key benefit of using chain-of-thought (CoT) prompting with GPT-4.1?**  
    a) Reduces output token usage  
    b) Improves output quality by breaking down problems  
    c) Eliminates the need for tools  
    d) Speeds up response time  
    **Correct Answer**: b  
    **Explanation**: CoT prompting improves output quality by breaking problems into manageable pieces (Section 3: Chain of Thought).

18. **What is a trade-off of using CoT prompting?**  
    a) Lower accuracy  
    b) Higher cost and latency  
    c) Reduced context window  
    d) Inability to use tools  
    **Correct Answer**: b  
    **Explanation**: CoT prompting increases cost and latency due to more output tokens (Section 3: Chain of Thought).

19. **What is a common error in CoT prompting that can be addressed with more explicit instructions?**  
    a) Overuse of tools  
    b) Misunderstanding user intent  
    c) Excessive context usage  
    d) Ignoring system prompts  
    **Correct Answer**: b  
    **Explanation**: Misunderstanding user intent is a common error that can be addressed with explicit instructions (Section 3: Chain of Thought).

20. **What is the first step in the recommended reasoning strategy for CoT prompting?**  
    a) Context Analysis  
    b) Query Analysis  
    c) Synthesis  
    d) Tool Calling  
    **Correct Answer**: b  
    **Explanation**: The first step is Query Analysis to understand the user’s query (Section 3: Chain of Thought).

21. **What should developers do to improve CoT prompts after auditing failures?**  
    a) Remove all instructions  
    b) Codify successful strategies in the prompt  
    c) Use shorter prompts  
    d) Avoid examples  
    **Correct Answer**: b  
    **Explanation**: Codifying successful strategies addresses systematic errors (Section 3: Chain of Thought).

22. **How does GPT-4.1’s instruction-following performance compare to other models?**  
    a) It is less precise  
    b) It is outstanding and highly controllable  
    c) It ignores instructions  
    d) It requires more examples  
    **Correct Answer**: b  
    **Explanation**: GPT-4.1 exhibits outstanding instruction-following performance (Section 4: Instruction Following).

23. **What should developers do if existing prompts for other models fail with GPT-4.1?**  
    a) Use the same prompts without changes  
    b) Add explicit specifications for desired behavior  
    c) Remove all examples  
    d) Use all-caps instructions  
    **Correct Answer**: b  
    **Explanation**: Explicit specifications are needed as GPT-4.1 follows instructions more literally (Section 4: Instruction Following).

24. **What is the first step in the recommended workflow for developing instructions?**  
    a) Add examples immediately  
    b) Start with a “Response Rules” or “Instructions” section  
    c) Use all-caps instructions  
    d) Remove all delimiters  
    **Correct Answer**: b  
    **Explanation**: Start with a high-level “Response Rules” or “Instructions” section (Section 4: Instruction Following).

25. **What should be done if GPT-4.1’s behavior is not as expected?**  
    a) Ignore the issue  
    b) Check for conflicting or underspecified instructions  
    c) Remove all tools  
    d) Use a different delimiter  
    **Correct Answer**: b  
    **Explanation**: Check for conflicting or underspecified instructions to resolve unexpected behavior (Section 4: Instruction Following).

26. **What is a common failure mode when instructing GPT-4.1 to always call a tool?**  
    a) It ignores the tool  
    b) It may hallucinate tool inputs  
    c) It terminates early  
    d) It skips planning  
    **Correct Answer**: b  
    **Explanation**: Instructing to always call a tool can lead to hallucinated inputs if information is lacking (Section 4: Common Failure Modes).

27. **How can repetitive use of sample phrases be avoided?**  
    a) Remove all sample phrases  
    b) Instruct the model to vary phrases  
    c) Use all-caps phrases  
    d) Avoid instructions altogether  
    **Correct Answer**: b  
    **Explanation**: Instructing the model to vary sample phrases prevents repetitive responses (Section 4: Common Failure Modes).

28. **What is the recommended starting delimiter for structuring prompts?**  
    a) JSON  
    b) Markdown  
    c) XML  
    d) Plain text  
    **Correct Answer**: b  
    **Explanation**: Markdown is recommended as the starting delimiter for prompts (Section 5: Delimiters).

29. **Which delimiter performed poorly for long context document input?**  
    a) Markdown  
    b) XML  
    c) JSON  
    d) Plain text  
    **Correct Answer**: c  
    **Explanation**: JSON performed particularly poorly for long context document input (Section 5: Delimiters).

30. **What should be done if GPT-4.1 resists producing very long, repetitive outputs?**  
    a) Use shorter prompts  
    b) Instruct strongly to output in full  
    c) Avoid using tools  
    d) Remove delimiters  
    **Correct Answer**: b  
    **Explanation**: Strong instructions to output in full can address resistance to long outputs (Section 5: Caveats).

31. **What is a recommended action if parallel tool calls are incorrect?**  
    a) Increase the context window  
    b) Set parallel_tool_calls to false  
    c) Use JSON delimiters  
    d) Remove all tools  
    **Correct Answer**: b  
    **Explanation**: Setting parallel_tool_calls to false can address incorrect parallel tool calls (Section 5: Caveats).

32. **What is a key feature of GPT-4.1’s diff generation capabilities?**  
    a) Reliance on line numbers  
    b) Substantially improved performance  
    c) Inability to handle complex diffs  
    d) Exclusive use of JSON format  
    **Correct Answer**: b  
    **Explanation**: GPT-4.1 has substantially improved diff generation capabilities (Appendix: Generating and Applying File Diffs).

33. **What is a characteristic of the V4A diff format used by GPT-4.1?**  
    a) Uses line numbers  
    b) Includes context before and after changes  
    c) Requires absolute file paths  
    d) Excludes new code snippets  
    **Correct Answer**: b  
    **Explanation**: The V4A diff format includes context before and after changes without using line numbers (Appendix: Apply Patch).

34. **How many lines of context are shown by default in the V4A diff format?**  
    a) 1 line  
    b) 2 lines  
    c) 3 lines  
    d) 4 lines  
    **Correct Answer**: c  
    **Explanation**: By default, 3 lines of context are shown before and after each change (Appendix: Apply Patch).

35. **What operator is used in the V4A diff format to indicate class or function context?**  
    a) ##  
    b) @@  
    c) --  
    d) ++  
    **Correct Answer**: b  
    **Explanation**: The @@ operator indicates class or function context in the V4A diff format (Appendix: Apply Patch).

36. **What happens if a patch is not applied correctly in the V4A format?**  
    a) The model terminates  
    b) Warnings or logging lines are printed before “Done!”  
    c) The model ignores the patch  
    d) The model crashes  
    **Correct Answer**: b  
    **Explanation**: Warnings or logging lines are printed before “Done!” to indicate issues (Appendix: Apply Patch).

37. **What is the purpose of the `apply_patch` tool in the GPT-4.1 guide?**  
    a) To execute Python code  
    b) To apply diffs to files  
    c) To search for files  
    d) To delete files automatically  
    **Correct Answer**: b  
    **Explanation**: The `apply_patch` tool applies diffs to files in the V4A format (Appendix: Apply Patch).

38. **What is a key aspect of effective diff formats mentioned in the guide?**  
    a) Use of line numbers  
    b) Clear delimiters between old and new code  
    c) Absolute file paths  
    d) JSON-based structure  
    **Correct Answer**: b  
    **Explanation**: Effective diff formats use clear delimiters between old and new code without line numbers (Appendix: Other Effective Diff Formats).

39. **Which diff format performed well in addition to the V4A format?**  
    a) JSON-based diff  
    b) SEARCH/REPLACE diff  
    c) Line-numbered diff  
    d) Markdown-based diff  
    **Correct Answer**: b  
    **Explanation**: The SEARCH/REPLACE diff format performed well alongside V4A (Appendix: Other Effective Diff Formats).

40. **What is the first step in the high-level problem-solving strategy for agentic workflows?**  
    a) Implement the fix  
    b) Understand the problem deeply  
    c) Test frequently  
    d) Debug as needed  
    **Correct Answer**: b  
    **Explanation**: The first step is to understand the problem deeply (Section 1: High-Level Problem Solving Strategy).

41. **What should be done after making incremental code changes in agentic workflows?**  
    a) Terminate the task  
    b) Test frequently  
    c) Ignore testing  
    d) Remove all context  
    **Correct Answer**: b  
    **Explanation**: Testing frequently after each change verifies correctness (Section 1: High-Level Problem Solving Strategy).

42. **What is the final step in the agentic workflow strategy?**  
    a) Develop a plan  
    b) Reflect and validate comprehensively  
    c) Investigate the codebase  
    d) Make code changes  
    **Correct Answer**: b  
    **Explanation**: The final step is to reflect and validate comprehensively (Section 1: High-Level Problem Solving Strategy).

43. **What should GPT-4.1 do if tests fail during the agentic workflow?**  
    a) Ignore the failures  
    b) Analyze failures and revise the patch  
    c) Terminate the task  
    d) Remove all tests  
    **Correct Answer**: b  
    **Explanation**: If tests fail, the model should analyze failures and revise the patch (Section 1: Testing).

44. **What is the purpose of the `lookup_policy_document` tool in the customer service example?**  
    a) To execute Python code  
    b) To retrieve internal documents by topic  
    c) To delete files  
    d) To modify user accounts  
    **Correct Answer**: b  
    **Explanation**: The `lookup_policy_document` tool retrieves internal documents by topic (Section 4: Example Prompt: Customer Service).

45. **What is the required parameter for the `get_user_account_info` tool?**  
    a) Topic  
    b) Phone number  
    c) File path  
    d) User name  
    **Correct Answer**: b  
    **Explanation**: The required parameter is a phone number formatted as '(xxx) xxx-xxxx' (Section 4: Example Prompt: Customer Service).

46. **What tone is recommended for the customer service agent prompt?**  
    a) Casual and informal  
    b) Professional and concise  
    c) Humorous and playful  
    d) Technical and detailed  
    **Correct Answer**: b  
    **Explanation**: A professional and concise tone is recommended (Section 4: Example Prompt: Customer Service).

47. **What should the customer service agent do if a user asks about a prohibited topic?**  
    a) Provide a detailed response  
    b) Deflect and offer help with another topic  
    c) Ignore the request  
    d) Escalate immediately  
    **Correct Answer**: b  
    **Explanation**: The agent should deflect and offer help with another topic (Section 4: Example Prompt: Customer Service).

48. **What is the recommended output format for customer service responses?**  
    a) Plain text without citations  
    b) Include citations for factual statements  
    c) Use JSON exclusively  
    d) Avoid formatting altogether  
    **Correct Answer**: b  
    **Explanation**: Factual statements require citations in the specified format (Section 4: Example Prompt: Customer Service).

49. **What is a key consideration when selecting delimiters for prompts?**  
    a) Use the same delimiter as the document content  
    b) Choose delimiters that stand out to the model  
    c) Avoid structured formats  
    d) Use line numbers  
    **Correct Answer**: b  
    **Explanation**: Delimiters should provide clear information and stand out to the model (Section 5: Delimiters).

50. **What is the role of the `apply_patch.py` reference implementation?**  
    a) To generate Python code  
    b) To apply pseudo-diff patches to text files  
    c) To search for files  
    d) To delete files automatically  
    **Correct Answer**: b  
    **Explanation**: The `apply_patch.py` implementation applies pseudo-diff patches to text files (Appendix: Reference Implementation: apply_patch.py).

---

# MarkDown MCQS
# 50 Multiple Choice Questions on Markdown Basic Syntax

Below are 50 multiple-choice questions based on the Markdown basic syntax from the provided document. Each question includes four options, with one correct answer.

1. **What is the correct way to create a heading level 3 in Markdown?**  
   a) `# Heading level 3`  
   b) `### Heading level 3`  
   c) `Heading level 3 ===`  
   d) `Heading level 3 ---`  
   **Answer:** b) `### Heading level 3`

2. **Which Markdown syntax creates a heading level 1 using alternate syntax?**  
   a) `Heading level 1 ---`  
   b) `Heading level 1 ===`  
   c) `## Heading level 1`  
   d) `> Heading level 1`  
   **Answer:** b) `Heading level 1 ===`

3. **What is a best practice for headings to ensure compatibility across Markdown applications?**  
   a) Use underscores instead of number signs  
   b) Always put a space between the number signs and the heading name  
   c) Avoid blank lines before and after headings  
   d) Use parentheses after the heading  
   **Answer:** b) Always put a space between the number signs and the heading name

4. **How do you create a paragraph in Markdown?**  
   a) Indent the text with four spaces  
   b) Use a blank line to separate lines of text  
   c) Add a `>` before the text  
   d) Enclose the text in backticks  
   **Answer:** b) Use a blank line to separate lines of text

5. **What is the correct way to create a line break in Markdown?**  
   a) End a line with a backslash (`\`)  
   b) End a line with two or more spaces  
   c) Press return without any spaces  
   d) Use a single asterisk at the end of the line  
   **Answer:** b) End a line with two or more spaces

6. **Which of the following is a recommended method for creating a line break for compatibility?**  
   a) Use a backslash at the end of the line  
   b) Use trailing whitespace or the `<br>` HTML tag  
   c) Press return without spaces  
   d) Add a single space at the end of the line  
   **Answer:** b) Use trailing whitespace or the `<br>` HTML tag

7. **How do you bold text in Markdown?**  
   a) `*bold text*`  
   b) `**bold text**`  
   c) `_bold text_`  
   d) `***bold text***`  
   **Answer:** b) `**bold text**`

8. **What is the best practice for bolding the middle of a word in Markdown?**  
   a) Use underscores (`__is__`)  
   b) Use asterisks (`**is**`)  
   c) Use single quotes (`'is'`)  
   d) Use backticks (`` `is` ``)  
   **Answer:** b) Use asterisks (`**is**`)

9. **How do you italicize text in Markdown?**  
   a) `**italic text**`  
   b) `*italic text*`  
   c) `***italic text***`  
   d) `` `italic text` ``  
   **Answer:** b) `*italic text*`

10. **What is the best practice for italicizing the middle of a word in Markdown?**  
    a) Use underscores (`_cat_`)  
    b) Use asterisks (`*cat*`)  
    c) Use double quotes (`"cat"`)  
    d) Use parentheses (`(cat)`)  
    **Answer:** b) Use asterisks (`*cat*`)

11. **How do you create text that is both bold and italic in Markdown?**  
    a) `**italic and bold**`  
    b) `*italic and bold*`  
    c) `***italic and bold***`  
    d) `_italic and bold_`  
    **Answer:** c) `***italic and bold***`

12. **What is the correct syntax for a blockquote in Markdown?**  
    a) `# This is a blockquote`  
    b) `> This is a blockquote`  
    c) `* This is a blockquote`  
    d) `` `This is a blockquote` ``  
    **Answer:** b) `> This is a blockquote`

13. **How do you create a blockquote with multiple paragraphs?**  
    a) Add `>` on blank lines between paragraphs  
    b) Add `>>` before each paragraph  
    c) Use a blank line without any symbols  
    d) Enclose paragraphs in backticks  
    **Answer:** a) Add `>` on blank lines between paragraphs

14. **How do you nest a blockquote in Markdown?**  
    a) Use `>` for all levels  
    b) Use `>>` for the nested paragraph  
    c) Use `>>>` for the nested paragraph  
    d) Use `#>` for the nested paragraph  
    **Answer:** b) Use `>>` for the nested paragraph

15. **Which element can be included in a blockquote?**  
    a) Headings  
    b) Lists  
    c) Both headings and lists  
    d) Neither headings nor lists  
    **Answer:** c) Both headings and lists

16. **What is a best practice for blockquotes to ensure compatibility?**  
    a) Avoid blank lines before and after blockquotes  
    b) Put blank lines before and after blockquotes  
    c) Indent blockquotes with four spaces  
    d) Use asterisks instead of `>`  
    **Answer:** b) Put blank lines before and after blockquotes

17. **How do you create an ordered list in Markdown?**  
    a) Use dashes (`-`) before items  
    b) Use numbers followed by periods  
    c) Use asterisks (`*`) before items  
    d) Use plus signs (`+`) before items  
    **Answer:** b) Use numbers followed by periods

18. **What happens if the numbers in an ordered list are not in sequence?**  
    a) The list will not render  
    b) The numbers will be displayed as written  
    c) The list will render in numerical order starting from 1  
    d) The list will render as an unordered list  
    **Answer:** c) The list will render in numerical order starting from 1

19. **What is the best practice for ordered list delimiters?**  
    a) Use parentheses (`1)`)  
    b) Use periods (`1.`)  
    c) Use colons (`1:`)  
    d) Use commas (`1,`)  
    **Answer:** b) Use periods (`1.`)

20. **How do you create an unordered list in Markdown?**  
    a) Use numbers followed by periods  
    b) Use dashes, asterisks, or plus signs  
    c) Use backticks  
    d) Use angle brackets  
    **Answer:** b) Use dashes, asterisks, or plus signs

21. **What should you do if an unordered list item starts with a number followed by a period?**  
    a) Use a backslash to escape the period  
    b) Enclose the number in backticks  
    c) Add a space before the number  
    d) Use a colon instead of a period  
    **Answer:** a) Use a backslash to escape the period

22. **What is the best practice for unordered list delimiters?**  
    a) Mix dashes, asterisks, and plus signs in the same list  
    b) Use only one type of delimiter in a list  
    c) Use parentheses for all items  
    d) Use backticks for all items  
    **Answer:** b) Use only one type of delimiter in a list

23. **How do you add a paragraph to a list item while preserving list continuity?**  
    a) Indent the paragraph by two spaces  
    b) Indent the paragraph by four spaces or one tab  
    c) Add a blank line before the paragraph  
    d) Use a backslash before the paragraph  
    **Answer:** b) Indent the paragraph by four spaces or one tab

24. **How many spaces should a code block be indented when inside a list?**  
    a) Four spaces  
    b) Six spaces  
    c) Eight spaces  
    d) Two spaces  
    **Answer:** c) Eight spaces

25. **How do you denote a word as code in Markdown?**  
    a) Enclose it in single quotes  
    b) Enclose it in backticks  
    c) Enclose it in asterisks  
    d) Enclose it in underscores  
    **Answer:** b) Enclose it in backticks

26. **How do you escape a backtick in a code span?**  
    a) Use a backslash before the backtick  
    b) Enclose the code in double backticks  
    c) Use single quotes instead of backticks  
    d) Add a space before the backtick  
    **Answer:** b) Enclose the code in double backticks

27. **How do you create a code block without using fenced code blocks?**  
    a) Indent every line by four spaces or one tab  
    b) Enclose the block in backticks  
    c) Use a `>` before each line  
    d) Add asterisks around the block  
    **Answer:** a) Indent every line by four spaces or one tab

28. **How do you create a horizontal rule in Markdown?**  
    a) Use three or more asterisks, dashes, or underscores  
    b) Use a single dash on a line  
    c) Use a backslash followed by a dash  
    d) Use three backticks  
    **Answer:** a) Use three or more asterisks, dashes, or underscores

29. **What is a best practice for horizontal rules?**  
    a) Avoid blank lines before and after  
    b) Put blank lines before and after  
    c) Indent the rule with four spaces  
    d) Use backticks around the rule  
    **Answer:** b) Put blank lines before and after

30. **How do you create a link in Markdown?**  
    a) `[link text](URL)`  
    b) `<link text> (URL)`  
    c) `{link text} [URL]`  
    d) `*link text* (URL)`  
    **Answer:** a) `[link text](URL)`

31. **How do you add a title to a link in Markdown?**  
    a) Add it in parentheses after the URL  
    b) Add it in quotation marks after the URL  
    c) Add it in backticks before the URL  
    d) Add it in brackets before the link text  
    **Answer:** b) Add it in quotation marks after the URL

32. **How do you turn a URL into a link without link text?**  
    a) Enclose it in backticks  
    b) Enclose it in angle brackets  
    c) Enclose it in parentheses  
    d) Enclose it in asterisks  
    **Answer:** b) Enclose it in angle brackets

33. **How do you emphasize a link in Markdown?**  
    a) Add backticks around the link text  
    b) Add asterisks around the brackets and parentheses  
    c) Add underscores around the URL  
    d) Add a backslash before the link  
    **Answer:** b) Add asterisks around the brackets and parentheses

34. **What is the first part of a reference-style link in Markdown?**  
    a) `[link text][label]`  
    b) `[link text](URL)`  
    c) `[label]: URL`  
    d) `<link text> [label]`  
    **Answer:** a) `[link text][label]`

35. **How is the second part of a reference-style link formatted?**  
    a) `[label]: URL`  
    b) `[link text]: URL`  
    c) `(label): URL`  
    d) `{label}: URL`  
    **Answer:** a) `[label]: URL`

36. **Where can you place the second part of a reference-style link?**  
    a) Only at the end of the document  
    b) Only immediately after the paragraph  
    c) Anywhere in the document  
    d) Only at the beginning of the document  
    **Answer:** c) Anywhere in the document

37. **How do you handle spaces in a URL for compatibility?**  
    a) Replace spaces with underscores  
    b) URL encode spaces with `%20`  
    c) Remove spaces entirely  
    d) Enclose the URL in backticks  
    **Answer:** b) URL encode spaces with `%20`

38. **How do you encode parentheses in a URL for compatibility?**  
    a) Use `%28` for `(` and `%29` for `)`  
    b) Use `%20` for both parentheses  
    c) Use backslashes before parentheses  
    d) Use underscores instead of parentheses  
    **Answer:** a) Use `%28` for `(` and `%29` for `)`

39. **How do you add an image in Markdown?**  
    a) `[alt text](image URL)`  
    b) `![alt text](image URL)`  
    c) `<alt text> (image URL)`  
    d) `*alt text* (image URL)`  
    **Answer:** b) `![alt text](image URL)`

40. **How do you add a title to an image in Markdown?**  
    a) Add it in brackets before the alt text  
    b) Add it in quotation marks after the image URL  
    c) Add it in backticks after the alt text  
    d) Add it in parentheses after the alt text  
    **Answer:** b) Add it in quotation marks after the image URL

41. **How do you create a linked image in Markdown?**  
    a) Enclose the image Markdown in backticks and add a URL  
    b) Enclose the image Markdown in brackets and add a URL in parentheses  
    c) Enclose the image URL in angle brackets  
    d) Add asterisks around the image Markdown  
    **Answer:** b) Enclose the image Markdown in brackets and add a URL in parentheses

42. **How do you escape a character like an asterisk in Markdown?**  
    a) Add a backslash before the character  
    b) Enclose the character in backticks  
    c) Add an asterisk before the character  
    d) Enclose the character in quotes  
    **Answer:** a) Add a backslash before the character

43. **Which character cannot be escaped with a backslash in Markdown?**  
    a) Asterisk (`*`)  
    b) Backslash (`\`)  
    c) Dollar sign (`$`)  
    d) Backtick (`` ` ``)  
    **Answer:** c) Dollar sign (`$`)

44. **How do you include HTML tags in a Markdown document?**  
    a) Enclose them in backticks  
    b) Place them directly in the text  
    c) Enclose them in angle brackets  
    d) Add a backslash before each tag  
    **Answer:** b) Place them directly in the text

45. **What is a best practice for block-level HTML tags in Markdown?**  
    a) Indent them with four spaces  
    b) Use blank lines to separate them from surrounding content  
    c) Enclose them in backticks  
    d) Add asterisks around them  
    **Answer:** b) Use blank lines to separate them from surrounding content

46. **Why might Markdown syntax not work inside block-level HTML tags?**  
    a) Markdown is not supported in HTML  
    b) Block-level HTML tags override Markdown syntax  
    c) Markdown requires backticks inside HTML  
    d) HTML tags must be indented  
    **Answer:** b) Block-level HTML tags override Markdown syntax

47. **Which of the following is a valid way to create a nested list?**  
    a) Indent the nested items by two spaces  
    b) Indent the nested items by four spaces or one tab  
    c) Use a backslash before nested items  
    d) Add a blank line before nested items  
    **Answer:** b) Indent the nested items by four spaces or one tab

48. **What is the rendered output of `Love**is**bold` in Markdown?**  
    a) Love *is* bold  
    b) Love **is** bold  
    c) Love isbold  
    d) Love is bold  
    **Answer:** c) Love isbold

49. **What is the HTML output of `*italic text*` in Markdown?**  
    a) `<i>italic text</i>`  
    b) `<em>italic text</em>`  
    c) `<strong>italic text</strong>`  
    d) `<code>italic text</code>`  
    **Answer:** b) `<em>italic text</em>`

50. **What is the purpose of the alt text in an image in Markdown?**  
    a) It specifies the image URL  
    b) It provides a description for accessibility  
    c) It sets the image size  
    d) It adds a caption below the image  
    **Answer:** b) It provides a description for accessibility