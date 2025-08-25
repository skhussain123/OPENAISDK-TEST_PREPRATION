# 50 Markdown MCQs

---

### General Markdown Information

1.  What is Markdown primarily designed to be?
    a) A complex database management system
    b) A lightweight markup language that's easy to read and write
    c) A proprietary software for graphic design
    d) A network protocol for secure communication
    **Correct Answer: b) A lightweight markup language that's easy to read and write**

2.  For what purpose is Markdown widely used?
    a) Developing operating systems
    b) Creating formatted content for documentation, blogs, and platforms like GitHub
    c) Performing complex mathematical calculations
    d) Designing 3D models
    **Correct Answer: b) Creating formatted content for documentation, blogs, and platforms like GitHub**

3.  Markdown files can be converted into which of the following formats?
    a) Only PDF documents
    b) HTML or other formats
    c) Encrypted binaries
    d) Audio files
    **Correct Answer: b) HTML or other formats**

4.  How is Markdown characterized in its raw (unrendered) form?
    a) Difficult to interpret by humans
    b) Machine-readable only
    c) Human-readable
    d) Always encrypted
    **Correct Answer: c) Human-readable**

---

### Headings

5.  What Markdown syntax is used to create a Heading level 1 (`<h1>`)?
    a) `## My Main Topic`
    b) `# My Main Topic`
    c) `### My Main Topic`
    d) `My Main Topic` <br> `---------------`
    **Correct Answer: b) `# My Main Topic`**

6.  To create an `<h3>` HTML tag using Markdown, how many `#` symbols are required?
    a) One
    b) Two
    c) Three
    d) Four
    **Correct Answer: c) Three**

7.  Which characters are used in the alternate syntax for Heading level 1, placed below the text?
    a) `--`
    b) `==`
    c) `***`
    d) `___`
    **Correct Answer: b) `==`**

8.  According to Markdown heading best practices, what should always be present between the `#` symbols and the heading name for compatibility?
    a) No space
    b) A single space
    c) An underscore
    d) A dash
    **Correct Answer: b) A single space**

9.  For compatibility, what should be placed before and after a heading?
    a) A line of code
    b) Blank lines
    c) A special character (e.g., `*`)
    d) A comment line
    **Correct Answer: b) Blank lines**

---

### Paragraphs and Line Breaks

10. How do you create separate paragraphs in Markdown?
    a) By using `\n` at the end of each line
    b) By separating lines of text with a blank line
    c) By indenting each new paragraph with a tab
    d) By enclosing text within `[p]` tags
    **Correct Answer: b) By separating lines of text with a blank line**

11. To create a line break (`<br>`) within a paragraph using Markdown, what is the most common method?
    a) End the line with a single space
    b) End the line with a backslash `\`
    c) End the line with two or more spaces, then type return
    d) Start the new line with a dash `-`
    **Correct Answer: c) End the line with two or more spaces, then type return**

12. Why is "trailing whitespace" for line breaks considered controversial?
    a) It's only supported by outdated Markdown parsers.
    b) It's visually indistinct in editors and can be used accidentally.
    c) It creates excessive padding in HTML output.
    d) It interferes with image embedding.
    **Correct Answer: b) It's visually indistinct in editors and can be used accidentally.**

---

### Emphasis

13. To make text **bold** in Markdown, besides two asterisks (`**`), what other characters can be used?
    a) Single asterisks (`*`)
    b) Two underscores (`__`)
    c) Three asterisks (`***`)
    d) Plus signs (`+`)
    **Correct Answer: b) Two underscores (`__`)**

14. For compatibility, what is the recommended way to bold the *middle* of a word?
    a) `Love__is__bold`
    b) `Love**is**bold`
    c) `Love*is*bold`
    d) `Love-is-bold`
    **Correct Answer: b) `Love**is**bold`**

15. To *italicize* text, which Markdown syntax can be used besides a single asterisk (`*`)?
    a) Two asterisks (`**`)
    b) A single underscore (`_`)
    c) Two underscores (`__`)
    d) A hash sign (`#`)
    **Correct Answer: b) A single underscore (`_`)**

16. How do you make text both ***bold and italic*** in Markdown?
    a) Using two asterisks (`**`)
    b) Using three asterisks (`***`) or underscores (`___`)
    c) Using one asterisk and one underscore (`*_`)
    d) Using a double tilde (`~~`)
    **Correct Answer: b) Using three asterisks (`***`) or underscores (`___`)**

---

### Blockquotes

17. What character is used to denote a blockquote?
    a) `#`
    b) `*`
    c) `>`
    d) `-`
    **Correct Answer: c) `>`**

18. To include multiple paragraphs within a single blockquote, what should be added on the blank lines between them?
    a) Nothing, just a blank line
    b) A space
    c) A `>` character
    d) A `---` horizontal rule
    **Correct Answer: c) A `>` character**

19. How are nested blockquotes created?
    a) By using `>>>`
    b) By adding `>>` in front of the nested paragraph
    c) By indenting the inner blockquote with four spaces
    d) By using HTML `<q>` tags
    **Correct Answer: b) By adding `>>` in front of the nested paragraph**

20. For compatibility, what is the best practice regarding blank lines around blockquotes?
    a) They are strictly forbidden.
    b) They should only be after the blockquote.
    c) They should only be before the blockquote.
    d) They should be placed before and after the blockquote.
    **Correct Answer: d) They should be placed before and after the blockquote.**

---

### Lists

21. What is the correct way to start an ordered list in Markdown?
    a) `1) First item`
    b) `1. First item`
    c) `- First item`
    d) `* First item`
    **Correct Answer: b) `1. First item`**

22. In an ordered list, what rule applies to the numbers used for list items?
    a) They must always be in sequential numerical order.
    b) They can be any number, but the list must start with `1.`.
    c) They must be Roman numerals.
    d) Only odd numbers are allowed.
    **Correct Answer: b) They can be any number, but the list must start with `1.`.**

23. Which of the following symbols cannot be used to create an unordered list item?
    a) `-` (dash)
    b) `*` (asterisk)
    c) `+` (plus sign)
    d) `#` (hash sign)
    **Correct Answer: d) `#` (hash sign)**

24. To create an indented item within a list, how many spaces or tabs should you use for indentation?
    a) Two spaces or one tab
    b) Four spaces or one tab
    c) Eight spaces or two tabs
    d) One space only
    **Correct Answer: b) Four spaces or one tab**

25. If an unordered list item starts with a number followed by a period (e.g., `1968. A great year!`), how do you ensure it renders as part of the unordered list and not an ordered one?
    a) Use double backticks around the number.
    b) Escape the period with a backslash (`\`).
    c) Put the entire line in parentheses.
    d) Change the number to a letter.
    **Correct Answer: b) Escape the period with a backslash (`\`).**

---

### Code

26. How do you denote a single word or phrase as inline code in Markdown?
    a) By enclosing it in double quotes (`"word"`)
    b) By enclosing it in backticks (`` `word` ``)
    c) By enclosing it in asterisks (`*word*`)
    d) By enclosing it in curly braces (`{word}`)
    **Correct Answer: b) By enclosing it in backticks (`` `word` ``)**

27. If an inline code snippet itself contains a backtick, how can it be properly displayed?
    a) Use a backslash before the inner backtick.
    b) Enclose the snippet in double backticks (`` `` `code` `` ``).
    c) It's not possible to include backticks in inline code.
    d) Convert it to a code block.
    **Correct Answer: b) Enclose the snippet in double backticks (`` `` `code` `` ``).**

28. What is the minimum indentation for each line to create a code block in Markdown?
    a) Two spaces or one tab
    b) Four spaces or one tab
    c) Six spaces or two tabs
    d) No indentation, just new lines
    **Correct Answer: b) Four spaces or one tab**

---

### Horizontal Rules

29. What is the minimum number of consecutive dashes (`---`) required on a line by themselves to create a horizontal rule?
    a) Two
    b) Three
    c) Four
    d) One
    **Correct Answer: b) Three**

30. For compatibility, what is the best practice for placing horizontal rules?
    a) Directly after text without blank lines.
    b) Directly before text without blank lines.
    c) With blank lines before and after them.
    d) Only at the very beginning or end of the document.
    **Correct Answer: c) With blank lines before and after them.**

---

### Links

31. How is the link text (the visible part) enclosed when creating a standard Markdown link?
    a) In parentheses `()`
    b) In angle brackets `<>`
    c) In square brackets `[]`
    d) In curly braces `{}`
    **Correct Answer: c) In square brackets `[]`**

32. The URL for a standard Markdown link immediately follows the link text and is enclosed in what?
    a) Square brackets `[]`
    b) Parentheses `()`
    c) Angle brackets `<>`
    d) Quotation marks `""`
    **Correct Answer: b) Parentheses `()`**

33. What is the syntax to automatically turn a raw URL or email address into a clickable link?
    a) `[url](url)`
    b) `<url>`
    c) `url`
    d) `!url`
    **Correct Answer: b) `<url>`**

34. What is the primary benefit of using reference-style links?
    a) They automatically open in a new tab.
    b) They make URLs easier to manage and read in the raw Markdown text.
    c) They support custom CSS styling.
    d) They are faster to render.
    **Correct Answer: b) They make URLs easier to manage and read in the raw Markdown text.**

35. For compatibility, how should spaces within a URL in a Markdown link be handled?
    a) Leave them as-is.
    b) Replace them with underscores `_`.
    c) URL encode them (e.g., `%20`).
    d) Enclose the entire URL in double quotes.
    **Correct Answer: c) URL encode them (e.g., `%20`).**

---

### Images

36. What is the correct Markdown syntax to embed an image?
    a) `[alt text](path/to/image.jpg)`
    b) `!alt text[path/to/image.jpg]`
    c) `![alt text](path/to/image.jpg)`
    d) `<img alt="alt text" src="path/to/image.jpg">`
    **Correct Answer: c) `![alt text](path/to/image.jpg)`**

37. What is the purpose of the "alt text" in Markdown image syntax?
    a) It's the caption for the image.
    b) It's displayed if the image fails to load.
    c) It serves as the image's filename.
    d) It adds a border around the image.
    **Correct Answer: b) It's displayed if the image fails to load.**

38. How do you link an image to another URL in Markdown?
    a) `[![alt text](image.jpg)](link-url)`
    b) `![alt text](image.jpg) (link-url)`
    c) `[link-url]![alt text](image.jpg)`
    d) You cannot link images in Markdown.
    **Correct Answer: a) `[![alt text](image.jpg)](link-url)`**

---

### Escaping Characters

39. To display a Markdown formatting character literally (e.g., to show an asterisk `*` instead of italicizing), what do you precede it with?
    a) A forward slash `/`
    b) A backslash `\`
    c) A hash sign `#`
    d) An exclamation mark `!`
    **Correct Answer: b) A backslash `\`**

40. Which of the following characters is generally *not* required to be escaped to be displayed literally in common Markdown usage, unless it's part of a formatting sequence?
    a) `*` (asterisk)
    b) `\` (backslash)
    c) `a` (lowercase letter 'a')
    d) `[` (square bracket)
    **Correct Answer: c) `a` (lowercase letter 'a')**

---

### Extended Syntax

41. Which extended Markdown syntax element uses `~~text~~` for formatting?
    a) Bold
    b) Italic
    c) Strikethrough
    d) Highlight
    **Correct Answer: c) Strikethrough**

42. What is the Markdown syntax for marking a completed task in a task list?
    a) `- [ ] Task`
    b) `- [c] Task`
    c) `- [x] Task`
    d) `- [+] Task`
    **Correct Answer: c) `- [x] Task`**

43. How do you add an Emoji using extended Markdown syntax?
    a) `(emoji_name)`
    b) `[emoji_name]`
    c) `:emoji_name:`
    d) `#emoji_name`
    **Correct Answer: c) `:emoji_name:`**

44. Which syntax is used for Superscript text?
    a) `X~2~`
    b) `X^2^`
    c) `X_2_`
    d) `X{2}`
    **Correct Answer: b) `X^2^`**

45. The extended syntax `H~2~O` would render as what?
    a) H^2^O
    b) H₂O (Subscript)
    c) H²O (Superscript)
    d) H-2-O
    **Correct Answer: b) H₂O (Subscript)**

---

### Prompt Engineering Best Practices (from provided context)

46. What is the most important best practice in prompt engineering to improve model performance?
    a) Using extremely long prompts.
    b) Providing one-shot/few-shot examples.
    c) Only using negative constraints.
    d) Setting a very high temperature.
    **Correct Answer: b) Providing one-shot/few-shot examples.**

47. When designing prompts, they should be concise, clear, and easy to understand for whom?
    a) Only the Large Language Model.
    b) Only other prompt engineers.
    c) Both you (the user) and the model.
    d) Only for automated evaluation systems.
    **Correct Answer: c) Both you (the user) and the model.**

48. What type of instructions are generally more effective in guiding an LLM?
    a) Negative instructions (what not to do).
    b) Ambiguous instructions.
    c) Positive instructions (what to do).
    d) Instructions with many constraints.
    **Correct Answer: c) Positive instructions (what to do).**

49. Why is using JSON as an output format for data extraction tasks often beneficial for LLMs?
    a) It makes the output more visually appealing.
    b) It increases the model's creativity.
    c) It forces the model to create a structure and can limit hallucinations.
    d) It reduces the processing time significantly.
    **Correct Answer: c) It forces the model to create a structure and can limit hallucinations.**

50. What is a key drawback of using JSON for LLM output, especially with token limits?
    a) It's difficult to sort the data.
    b) It always produces plain, unstructured text.
    c) It consumes significantly more tokens, potentially leading to truncation and invalid JSON.
    d) It cannot return data types.
    **Correct Answer: c) It consumes significantly more tokens, potentially leading to truncation and invalid JSON.**