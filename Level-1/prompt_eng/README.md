

Lmm ko hum markdown me bhi input de sakty hain.na sirf markdown balky different structure me bhi de sakty hain.jismy se 3 documentation
me mention hai.
* json
* XML
* Rap

The GPT-4.1 family of models represents a significant step forward from GPT-4o in capabilities across coding, instruction following, and long context. In this prompting guide, we collate a series of important prompting tips derived from extensive internal testing to help developers fully leverage the improved abilities of this new model family.

Many typical best practices still apply to GPT-4.1, such as providing context examples, making instructions as specific and clear as possible, and inducing planning via prompting to maximize model intelligence. However, we expect that getting the most out of this model will require some prompt migration. GPT-4.1 is trained to follow instructions more closely and more literally than its predecessors, which tended to more liberally infer intent from user and system prompts. This also means, however, that GPT-4.1 is highly steerable and responsive to well-specified prompts - if model behavior is different from what you expect, a single sentence firmly and unequivocally clarifying your desired behavior is almost always sufficient to steer the model on course.

Please read on for prompt examples you can use as a reference, and remember that while this guidance is widely applicable, no advice is one-size-fits-all. AI engineering is inherently an empirical discipline, and large language models are inherently nondeterministic; in addition to following this guide, we advise building informative evals and iterating often to ensure your prompt engineering changes are yielding benefits for your use case.

### Agentic Workflows
GPT-4.1 is a great place to build agentic workflows. In model training we emphasized providing a diverse range of agentic problem-solving trajectories, and our agentic harness for the model achieves state-of-the-art performance for non-reasoning models on SWE-bench Verified, solving 55% of problems.


#### System Prompt Reminders
In order to fully utilize the agentic capabilities of GPT-4.1, we recommend including three key types of reminders in all agent prompts. The following prompts are optimized specifically for the agentic coding workflow, but can be easily modified for general agentic use cases.

1. Persistence: this ensures the model understands it is entering a multi-message turn, and prevents it from prematurely yielding control back to the user. Our example is the following:
```bash
You are an agent - please keep going until the user’s query is completely resolved, before ending your turn and yielding back to the user. Only terminate your turn when you are sure that the problem is solved.
```


2. Tool-calling: this encourages the model to make full use of its tools, and reduces its likelihood of hallucinating or guessing an answer. Our example is the following:
```bash
If you are not sure about file content or codebase structure pertaining to the user’s request, use your tools to read files and gather the relevant information: do NOT guess or make up an answer.
```


3. Planning [optional]: if desired, this ensures the model explicitly plans and reflects upon each tool call in text, instead of completing the task by chaining together a series of only tool calls. Our example is the following:
```bash
You MUST plan extensively before each function call, and reflect extensively on the outcomes of the previous function calls. DO NOT do this entire process by making function calls only, as this can impair your ability to solve the problem and think insightfully.
```
GPT-4.1 is trained to respond very closely to both user instructions and system prompts in the agentic setting. The model adhered closely to these three simple instructions and increased our internal SWE-bench Verified score by close to 20% - so we highly encourage starting any agent prompt with clear reminders covering the three categories listed above. As a whole, we find that these three instructions transform the model from a chatbot-like state into a much more “eager” agent, driving the interaction forward autonomously and independently.



# What is MarkDown 
Markdown is a lightweight markup language with plain-text formatting syntax, designed to be easy to read and write. It allows users to format text for things like headings, lists, links, images, and more, using simple symbols (e.g., # for headings, * for emphasis). It’s widely used for creating formatted content in documentation, blogs, and platforms like GitHub, as it can be converted to HTML or other formats while remaining human-readable in its raw form. The provided cheat sheet from Markdown Guide outlines its basic and extended syntax, including elements like tables, code blocks, and emojis, though not all applications support the extended features.

### Basic Syntax

| **Element**         | **Markdown Syntax**                                    |
| ------------------- | ------------------------------------------------------ |
| **Heading**         | `# H1`<br>`## H2`<br>`### H3`                          |
| **Bold**            | `**bold text**`                                        |
| **Italic**          | `*italicized text*`                                    |
| **Blockquote**      | `> blockquote`                                         |
| **Ordered List**    | `1. First item`<br>`2. Second item`<br>`3. Third item` |
| **Unordered List**  | `- First item`<br>`- Second item`<br>`- Third item`    |
| **Code**            | `` `code` ``                                           |
| **Horizontal Rule** | `---`                                                  |
| **Link**            | `[title](https://www.example.com)`                     |
| **Image**           | `![alt text](image.jpg)`                               |



### Extended Syntax
These elements extend the basic syntax by adding additional features. Not all Markdown applications support these elements.

| **Element**           | **Markdown Syntax**                                                                            |        |             |         |             |             |        |        |       |        |           |      |    |
| --------------------- | ---------------------------------------------------------------------------------------------- | ------ | ----------- | ------- | ----------- | ----------- | ------ | ------ | ----- | ------ | --------- | ---- | -- |
| **Table**             | \`                                                                                             | Syntax | Description | ` <br>` | ----------- | ----------- | `<br>` | Header | Title | `<br>` | Paragraph | Text | \` |
| **Fenced Code Block** | <pre>`<br>{<br>  "firstName": "John",<br>  "lastName": "Smith",<br>  "age": 25<br>}`</pre>     |        |             |         |             |             |        |        |       |        |           |      |    |
| **Footnote**          | `Here's a sentence with a footnote. [^1]` <br><br> `[^1]: This is the footnote.`               |        |             |         |             |             |        |        |       |        |           |      |    |
| **Heading ID**        | `### My Great Heading {#custom-id}`                                                            |        |             |         |             |             |        |        |       |        |           |      |    |
| **Definition List**   | `term` <br> `: definition`                                                                     |        |             |         |             |             |        |        |       |        |           |      |    |
| **Strikethrough**     | `~~The world is flat.~~`                                                                       |        |             |         |             |             |        |        |       |        |           |      |    |
| **Task List**         | `- [x] Write the press release` <br> `- [ ] Update the website` <br> `- [ ] Contact the media` |        |             |         |             |             |        |        |       |        |           |      |    |
| **Emoji**             | `That is so funny! :joy:`                                                                      |        |             |         |             |             |        |        |       |        |           |      |    |
| **Highlight**         | `I need to highlight these ==very important words==.`                                          |        |             |         |             |             |        |        |       |        |           |      |    |
| **Subscript**         | `H~2~O`                                                                                        |        |             |         |             |             |        |        |       |        |           |      |    |
| **Superscript**       | `X^2^`                                                                                         |        |             |         |             |             |        |        |       |        |           |      |    |

