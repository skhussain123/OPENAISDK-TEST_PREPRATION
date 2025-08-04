

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


### Headings
To create a heading, add number signs (#) in front of a word or phrase. The number of number signs you use should correspond to the heading level. For example, to create a heading level three (<h3>), use three number signs (e.g., ### My Header).


| **Markdown**             | **HTML**                   | **Rendered Output** |
| ------------------------ | -------------------------- | ------------------- |
| `# Heading level 1`      | `<h1>Heading level 1</h1>` | **Heading level 1** |
| `## Heading level 2`     | `<h2>Heading level 2</h2>` | **Heading level 2** |
| `### Heading level 3`    | `<h3>Heading level 3</h3>` | **Heading level 3** |
| `#### Heading level 4`   | `<h4>Heading level 4</h4>` | **Heading level 4** |
| `##### Heading level 5`  | `<h5>Heading level 5</h5>` | **Heading level 5** |
| `###### Heading level 6` | `<h6>Heading level 6</h6>` | **Heading level 6** |


### Alternate Syntax
Alternatively, on the line below the text, add any number of == characters for heading level 1 or -- characters for heading level 2.

| **Markdown**                              | **HTML**                   | **Rendered Output** |
| ----------------------------------------- | -------------------------- | ------------------- |
| `Heading level 1`  <br> `===============` | `<h1>Heading level 1</h1>` | **Heading level 1** |
| `Heading level 2`  <br> `---------------` | `<h2>Heading level 2</h2>` | **Heading level 2** |


### Heading Best Practices
Markdown applications don’t agree on how to handle a missing space between the number signs (#) and the heading name. For compatibility, always put a space between the number signs and the heading name.

| ✅ **Do this**        | ❌ **Don't do this** |
| -------------------- | ------------------- |
| `# Here's a Heading` | `#Here's a Heading` |


* You should also put blank lines before and after a heading for compatibility.

| ✅ **Do this**                                                                       | ❌ **Don't do this**                                                              |
| ----------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| Try to put a blank line before...<br><br>`# Heading`<br><br>...and after a heading. | Without blank lines, this might not look right.<br>`# Heading`<br>Don't do this! |


### Paragraphs
To create paragraphs, use a blank line to separate one or more lines of text.

| **Markdown**                                                                                        | **HTML**                                                                                                              | **Rendered Output**                                                                                 |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| I really like using Markdown.<br><br>I think I'll use it to format all of my documents from now on. | `<p>I really like using Markdown.</p>`<br><br>`<p>I think I'll use it to format all of my documents from now on.</p>` | I really like using Markdown.<br><br>I think I'll use it to format all of my documents from now on. |

### Line Breaks
To create a line break or new line (<br>), end a line with two or more spaces, and then type return.
| **Markdown**                                                    | **HTML**                                                               | **Rendered Output**                                        |
| --------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------- |
| `This is the first line.  `  <br>`And this is the second line.` | `<p>This is the first line.<br>`<br>`And this is the second line.</p>` | This is the first line.  <br> And this is the second line. |


### Line Break Best Practices
You can use two or more spaces (commonly referred to as “trailing whitespace”) for line breaks in nearly every Markdown application, but it’s controversial. It’s hard to see trailing whitespace in an editor, and many people accidentally or intentionally put two spaces after every sentence. For this reason, you may want to use something other than trailing whitespace for line breaks. If your Markdown application supports HTML, you can use the <br> HTML tag.

For compatibility, use trailing white space or the <br> HTML tag at the end of the line.

There are two other options I don’t recommend using. CommonMark and a few other lightweight markup languages let you type a backslash (\) at the end of the line, but not all Markdown applications support this, so it isn’t a great option from a compatibility perspective. And at least a couple lightweight markup languages don’t require anything at the end of the line — just type return and they’ll create a line break.

| ✅ **Do this**                                                                                       | ❌ **Don't do this**                                                                                   |
| --------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Using two spaces at the end:**  <br>`First line with two spaces after.  `<br>`And the next line.` | **No break — just a new line in text:**  <br>`First line with nothing after.`<br>`And the next line.` |
| **Using `<br>` tag (HTML):**  <br>`First line with the HTML tag after.<br>`<br>`And the next line.` | *(Works, but not pure Markdown — relies on raw HTML)*                                                 |
| **Using backslash `\` at end:**  <br>`First line with a backslash after.\`<br>`And the next line.`  | *(Backslash doesn't always work reliably — depends on Markdown engine)*                               |


## Emphasis
You can add emphasis by making text bold or italic.

### Bold
To bold text, add two asterisks or underscores before and after a word or phrase. To bold the middle of a word for emphasis, add two asterisks without spaces around the letters.

| **Markdown**                 | **HTML**                                  | **Rendered Output**                          |
| ---------------------------- | ----------------------------------------- | -------------------------------------------- |
| `I just love **bold text**.` | `I just love <strong>bold text</strong>.` | I just love **bold text**                    |
| `I just love __bold text__.` | `I just love <strong>bold text</strong>.` | I just love **bold text**                    |
| `Love**is**bold`             | `Love<strong>is</strong>bold`             | Love**is**bold (incorrect spacing/rendering) |



### Bold Best Practices
Markdown applications don’t agree on how to handle underscores in the middle of a word. For compatibility, use asterisks to bold the middle of a word for emphasis.

| ✅ **Do this**    | ❌ **Don't do this** |
| ---------------- | ------------------- |
| `Love**is**bold` | `Love__is__bold`    |


### Italic
To italicize text, add one asterisk or underscore before and after a word or phrase. To italicize the middle of a word for emphasis, add one asterisk without spaces around the letters.
| **Markdown**                           | **HTML**                                      | **Rendered Output**                  |
| -------------------------------------- | --------------------------------------------- | ------------------------------------ |
| `Italicized text is the *cat's meow*.` | `Italicized text is the <em>cat's meow</em>.` | *Italicized text is the cat’s meow.* |
| `Italicized text is the _cat's meow_.` | `Italicized text is the <em>cat's meow</em>.` | *Italicized text is the cat’s meow.* |
| `A*cat*meow`                           | `A<em>cat</em>meow`                           | Acatmeow *(renders incorrectly)*     |


### Italic Best Practices
Markdown applications don’t agree on how to handle underscores in the middle of a word. For compatibility, use asterisks to italicize the middle of a word for emphasis.
| ✅ **Do this** | ❌ **Don't do this** |
| ------------- | ------------------- |
| `A*cat*meow`  | `A_cat_meow`        |


### Bold and Italic
To emphasize text with bold and italics at the same time, add three asterisks or underscores before and after a word or phrase. To bold and italicize the middle of a word for emphasis, add three asterisks without spaces around the letters.

| **Markdown**                              | **HTML**                                                      | **Rendered Output**                                             |
| ----------------------------------------- | ------------------------------------------------------------- | --------------------------------------------------------------- |
| `This text is ***really important***.`    | `<em><strong>really important</strong></em>`                  | *really important* (bold + italic)                              |
| `This text is ___really important___.`    | `<em><strong>really important</strong></em>`                  | *really important* (bold + italic)                              |
| `This text is __*really important*__.`    | `<em><strong>really important</strong></em>`                  | *really important* (bold + italic)                              |
| `This text is **_really important_**.`    | `<em><strong>really important</strong></em>`                  | *really important* (bold + italic)                              |
| `This is really***very***important text.` | `This is really<em><strong>very</strong></em>important text.` | This is really**very**important text *(combined into one word)* |


### Bold and Italic Best Practices
Markdown applications don’t agree on how to handle underscores in the middle of a word. For compatibility, use asterisks to bold and italicize the middle of a word for emphasis.

| ✅ **Do this**                               | ❌ **Don't do this**                       |
| ------------------------------------------- | ----------------------------------------- |
| `This is really ***very*** important text.` | `This is really___very___important text.` |



### Blockquotes
> Dorothy followed her through many of the beautiful rooms in her castle.

### Blockquotes with Multiple Paragraphs
Blockquotes can contain multiple paragraphs. Add a > on the blank lines between the paragraphs.
> Dorothy followed her through many of the beautiful rooms in her castle.
>
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.










## cheat-sheet
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

