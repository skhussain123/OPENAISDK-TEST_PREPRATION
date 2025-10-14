

#### Other Learning Resources:
1. [Open_AI_sdk_prompting_guide](https://cookbook.openai.com/examples/gpt4-1_prompting_guide)
2. [whitepaper-prompt-engineering](https://www.kaggle.com/whitepaper-prompt-engineering)
3. [Markdown Guide](https://www.markdownguide.org/basic-syntax/)
4. [Markdown Guide Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)

Lmm ko hum markdown me bhi input de sakty hain.na sirf markdown balky different structure me bhi de sakty hain.jismy se 3 documentation
me mention hai.
* json
* XML

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


### Nested Blockquotes
Blockquotes can be nested. Add a >> in front of the paragraph you want to nest.

> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.


### Blockquotes with Other Elements
Blockquotes can contain other Markdown formatted elements. Not all elements can be used — you’ll need to experiment to see which ones work.

> #### The quarterly results look great!
>
> - Revenue was off the chart.
> - Profits were higher than ever.
>
>  *Everything* is going according to **plan**.


### Blockquotes Best Practices
For compatibility, put blank lines before and after blockquotes.

| ✅ **Do karo (Do This)**    | ❌ **Mat karo (Don’t Do This)**                              |
| -------------------------- | ----------------------------------------------------------- |
| (blank line)               | (`>` blockquote direct without blank lines)                 |
| `> Yeh aik blockquote hai` | `> Yeh aik blockquote hai`<br>`Yeh blockquote k bahar text` |
| (blank line)               |                                                             |


## Lists
You can organize items into ordered and unordered lists.

### Ordered Lists
To create an ordered list, add line items with numbers followed by periods. The numbers don’t have to be in numerical order, but the list should start with the number one.

| **Markdown**                                                                                                                                                             | **HTML**                                                                                                                                                                                                                     | **Rendered Output** |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------- |
| `markdown<br>1. First item<br>2. Second item<br>3. Third item<br>4. Fourth item`                                                                                         | `html<br><ol><br>  <li>First item</li><br>  <li>Second item</li><br>  <li>Third item</li><br>  <li>Fourth item</li><br></ol>`                                                                                                |                     |
| `markdown<br>1. First item<br>1. Second item<br>1. Third item<br>1. Fourth item`                                                                                         | (same HTML as above)                                                                                                                                                                                                         |                     |
| `markdown<br>1. First item<br>8. Second item<br>3. Third item<br>5. Fourth item`                                                                                         | (same HTML as above)                                                                                                                                                                                                         |                     |
| `markdown<br>1. First item<br>2. Second item<br>3. Third item<br>&nbsp;&nbsp;&nbsp;&nbsp;1. Indented item<br>&nbsp;&nbsp;&nbsp;&nbsp;2. Indented item<br>4. Fourth item` | `html<br><ol><br>  <li>First item</li><br>  <li>Second item</li><br>  <li>Third item<br>    <ol><br>      <li>Indented item</li><br>      <li>Indented item</li><br>    </ol><br>  </li><br>  <li>Fourth item</li><br></ol>` |                     |

### Ordered List Best Practices
CommonMark and a few other lightweight markup languages let you use a parenthesis ()) as a delimiter (e.g., 1) First item), but not all Markdown applications support this, so it isn’t a great option from a compatibility perspective. For compatibility, use periods only.

| ✅ **Do this**    | ❌ **Don’t do this** |
| ---------------- | ------------------- |
| `1. First item`  | `1) First item`     |
| `2. Second item` | `2) Second item`    |


### Unordered Lists
To create an unordered list, add dashes (-), asterisks (*), or plus signs (+) in front of line items. Indent one or more items to create a nested list.

| **Markdown**                                                                                                              | **Generated HTML**                                                                        | **Rendered Output** (Visual)                                                                               |
| ------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| `- First item`<br>`- Second item`<br>`- Third item`<br>`- Fourth item`                                                    | `<ul><li>First item</li><li>Second item</li><li>Third item</li><li>Fourth item</li></ul>` | • First item<br>• Second item<br>• Third item<br>• Fourth item                                             |
| `* First item`<br>`* Second item`<br>`* Third item`<br>`* Fourth item`                                                    | Same as above                                                                             | • First item<br>• Second item<br>• Third item<br>• Fourth item                                             |
| `+ First item`<br>`+ Second item`<br>`+ Third item`<br>`+ Fourth item`                                                    | Same as above                                                                             | • First item<br>• Second item<br>• Third item<br>• Fourth item                                             |
| `- First item`<br>`- Second item`<br>`- Third item`<br> `    - Indented item`<br>`    - Indented item`<br>`- Fourth item` | `<ul>` with nested `<ul>` inside the third `<li>`                                         | • First item<br>• Second item<br>• Third item<br>   • Indented item<br>   • Indented item<br>• Fourth item |


### Starting Unordered List Items With Numbers
If you need to start an unordered list item with a number followed by a period, you can use a backslash (\) to escape the period.
| **Markdown**                                                  | **Generated HTML**                                                            | **Rendered Output**                                      |
| ------------------------------------------------------------- | ----------------------------------------------------------------------------- | -------------------------------------------------------- |
| `- 1968\. A great year!`<br>`- I think 1969 was second best.` | `<ul><li>1968. A great year!</li><li>I think 1969 was second best.</li></ul>` | • 1968. A great year!<br>• I think 1969 was second best. |


### Unordered List Best Practices
Markdown applications don’t agree on how to handle different delimiters in the same list. For compatibility, don’t mix and match delimiters in the same list — pick one and stick with it.

| ✅ **Do this**                                                          | ❌ **Don’t do this**                                                    |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `- First item`<br>`- Second item`<br>`- Third item`<br>`- Fourth item` | `+ First item`<br>`* Second item`<br>`- Third item`<br>`+ Fourth item` |


### Adding Elements in Lists
To add another element in a list while preserving the continuity of the list, indent the element four spaces or one tab, as shown in the following examples.

* This is the first list item.
* Here's the second list item.

    I need to add another paragraph below the second list item.

* And here's the third list item.

##### Blockquotes
* This is the first list item.
* Here's the second list item.

    > A blockquote would look great below the second list item.

* And here's the third list item.

##### Code Blocks
Code blocks are normally indented four spaces or one tab. When they’re in a list, indent them eight spaces or two tabs.
1. Open the file.
2. Find the following code block on line 21:

        <html>
          <head>
            <title>Test</title>
          </head>

3. Update the title to match the name of your website.

##### Images
1. Open the file containing the Linux mascot.
2. Marvel at its beauty.

    ![Tux, the Linux mascot](/assets/images/tux.png)

3. Close the file.


##### Lists
You can nest an unordered list in an ordered list, or vice versa.

1. First item
2. Second item
3. Third item
    - Indented item
    - Indented item
4. Fourth item


### Code
To denote a word or phrase as code, enclose it in backticks (`).
| **Markdown**                              | **HTML Output**                                  | **Rendered Output**                 |
| ----------------------------------------- | ------------------------------------------------ | ----------------------------------- |
| `` `At the command prompt, type `nano`.`` | `At the command prompt, type <code>nano</code>.` | At the command prompt, type `nano`. |


#### Escaping Backticks
If the word or phrase you want to denote as code includes one or more backticks, you can escape it by enclosing the word or phrase in double backticks (``).

| **Markdown**                          | **HTML Output**                                  | **Rendered Output**               |
| ------------------------------------- | ------------------------------------------------ | --------------------------------- |
| ``Use `code` in your Markdown file.`` | `<code>Use `code` in your Markdown file.</code>` | Use `code` in your Markdown file. |


##### Code Blocks
To create code blocks, indent every line of the block by at least four spaces or one tab.
 <html>
      <head>
      </head>
    </html>


#### Horizontal Rules
To create a horizontal rule, use three or more asterisks (***), dashes (---), or underscores (___) on a line by themselves.
***

---

_________________


### Horizontal Rule Best Practices
For compatibility, put blank lines before and after horizontal rules.
| ✅ **Do this**                         | ❌ **Don’t do this**                                                          |
| ------------------------------------- | ---------------------------------------------------------------------------- |
| (blank line)<br>`---`<br>(blank line) | `Without blank lines, this would be a heading.`<br>`---`<br>`Don't do this!` |


#### Links
To create a link, enclose the link text in brackets (e.g., [Duck Duck Go]) and then follow it immediately with the URL in parentheses (e.g., (https://duckduckgo.com)).
My favorite search engine is [Duck Duck Go](https://duckduckgo.com).


### Adding Titles
You can optionally add a title for a link. This will appear as a tooltip when the user hovers over the link. To add a title, enclose it in quotation marks after the URL.

My favorite search engine is [Duck Duck Go](https://duckduckgo.com "The best search engine for privacy").

#### URLs and Email Addresses
To quickly turn a URL or email address into a link, enclose it in angle brackets.

<https://www.markdownguide.org>
<fake@example.com>


#### Formatting Links
To emphasize links, add asterisks before and after the brackets and parentheses. To denote links as code, add backticks in the brackets.

I love supporting the **[EFF](https://eff.org)**.
This is the *[Markdown Guide](https://www.markdownguide.org)*.
See the section on [`code`](#code).


### Reference-style Links
Reference-style links are a special kind of link that make URLs easier to display and read in Markdown. Reference-style links are constructed in two parts: the part you keep inline with your text and the part you store somewhere else in the file to keep the text easy to read.


### Formatting the First Part of the Link
The first part of a reference-style link is formatted with two sets of brackets. The first set of brackets surrounds the text that should appear linked. The second set of brackets displays a label used to point to the link you’re storing elsewhere in your document.

Although not required, you can include a space between the first and second set of brackets. The label in the second set of brackets is not case sensitive and can include letters, numbers, spaces, or punctuation.

This means the following example formats are roughly equivalent for the first part of the link:

[hobbit-hole][1]
[hobbit-hole] [1]


#### Formatting the Second Part of the Link
The second part of a reference-style link is formatted with the following attributes:

1. The label, in brackets, followed immediately by a colon and at least one space (e.g., [label]: ).
2. The URL for the link, which you can optionally enclose in angle brackets.
3. The optional title for the link, which you can enclose in double quotes, single quotes, or parentheses.

This means the following example formats are all roughly equivalent for the second part of the link:

* [1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle
* [1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle "Hobbit lifestyles"
* [1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle 'Hobbit lifestyles'
* [1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle (Hobbit lifestyles)
* [1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> "Hobbit lifestyles"
* [1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> 'Hobbit lifestyles'
* [1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> (Hobbit lifestyles)

You can place this second part of the link anywhere in your Markdown document. Some people place them immediately after the paragraph in which they appear while other people place them at the end of the document (like endnotes or footnotes).


#### An Example Putting the Parts Together
Say you add a URL as a standard URL link to a paragraph and it looks like this in Markdown:

In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends
of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to
eat: it was a [hobbit-hole](https://en.wikipedia.org/wiki/Hobbit#Lifestyle "Hobbit lifestyles"), and that means comfort.


Though it may point to interesting additional information, the URL as displayed really doesn’t add much to the existing raw text other than making it harder to read. To fix that, you could format the URL like this instead:

In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends
of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to
eat: it was a [hobbit-hole][1], and that means comfort.

[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> "Hobbit lifestyles"


#### Link Best Practices
Markdown applications don’t agree on how to handle spaces in the middle of a URL. For compatibility, try to URL encode any spaces with %20. Alternatively, if your Markdown application supports HTML, you could use the a HTML tag.

| ✅ **Do this**                                       | ❌ **Don’t do this**                                                                                           |
| --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `[link](https://www.example.com/my%20great%20page)` | `<a href="https://www.example.com/my great page">link</a>`<br>`[link](https://www.example.com/my great page)` |


Parentheses in the middle of a URL can also be problematic. For compatibility, try to URL encode the opening parenthesis (() with %28 and the closing parenthesis ()) with %29. Alternatively, if your Markdown application supports HTML, you could use the a HTML tag.

| ✅ **Do this**                                                                    | ❌ **Don’t do this**                                                                                                                                                     |
| -------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `[a novel](https://en.wikipedia.org/wiki/The_Milagro_Beanfield_War_%28novel%29)` | `<a href="https://en.wikipedia.org/wiki/The_Milagro_Beanfield_War_(novel)">a novel</a>`<br>`[a novel](https://en.wikipedia.org/wiki/The_Milagro_Beanfield_War_(novel))` |


#### Images
To add an image, add an exclamation mark (!), followed by alt text in brackets, and the path or URL to the image asset in parentheses. You can optionally add a title in quotation marks after the path or URL.

![The San Juan Mountains are beautiful!](/assets/images/san-juan-mountains.jpg "San Juan Mountains")

#### Linking Images
To add a link to an image, enclose the Markdown for the image in brackets, and then add the link in parentheses.

[![An old rock in the desert](/assets/images/shiprock.jpg "Shiprock, New Mexico by Beau Rogers")](https://www.flickr.com/photos/
beaurogers/31833779864/in/photolist-Qv3rFw-34mt9F-a9Cmfy-5Ha3Zi-9msKdv-o3hgjr-hWpUte-4WMsJ1-KUQ8N-deshUb-vssBD-6CQci6-8AFCiD-zsJWT-nNfsgB-dPDwZJ-bn9JGn-5HtSXY-6CUhAL-a4UTXB-ugPum-KUPSo-fBLNm-6CUmpy-4WMsc9-8a7D3T-83KJev-6CQ2bK-nNusHJ-a78rQH-nw3NvT-7aq2qf-8wwBso-3nNceh-ugSKP-4mh4kh-bbeeqH-a7biME-q3PtTf-brFpgb-cg38zw-bXMZc-nJPELD-f58Lmo-bXMYG-bz8AAi-bxNtNT-bXMYi-bXMY6-bXMYv)


#### Escaping Characters
To display a literal character that would otherwise be used to format text in a Markdown document, add a backslash (\) in front of the character.

\* Without the backslash, this would be a bullet in an unordered list.


### Characters You Can Escape

| **Character** | **Naam (Name)**        |                     |
| ------------- | ---------------------- | ------------------- |
| `\`           | backslash              |                     |
| `` ` ``       | backtick               |                     |
| `*`           | asterisk               |                     |
| `_`           | underscore             |                     |
| `{ }`         | curly braces           |                     |
| `[ ]`         | square brackets        |                     |
| `< >`         | angle brackets         |                     |
| `( )`         | parentheses            |                     |
| `#`           | pound sign / hash mark |                     |
| `+`           | plus sign              |                     |
| `-`           | minus sign / hyphen    |                     |
| `.`           | dot                    |                     |
| `!`           | exclamation mark       |                     |
| \`            | \`                     | pipe (vertical bar) |









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
| **Clickable Image**   `[![alt text](image.jpg)](https://example.com)`        |



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

