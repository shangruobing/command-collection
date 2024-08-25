# Markdown

Markdown is a lightweight markup language that can be used to add formatting elements to plain text documents. Markdown was created by John Gruber in 2004 and has become one of the most popular markup languages in the world today.

## Headings

Headings are created using the `#` symbol. The number of `#` symbols determines the level of the heading (from 1 to 6).

```markdown
# Heading 1

## Heading 2

### Heading 3
```

- `# Heading 1` produces a large, top-level heading.
- `## Heading 2` is a subheading.
- `### Heading 3` is a smaller subheading.

## Text Formatting

You can style your text using simple symbols:

- **Bold**: Surround the text with two asterisks (`**`) or underscores (`__`).
  ```markdown
  **Bold Text** or **Bold Text**
  ```
- _Italic_: Surround the text with one asterisk (`*`) or underscore (`_`).
  ```markdown
  _Italic Text_ or _Italic Text_
  ```
- **_Bold and Italic_**: Combine both by using three asterisks or underscores.
  ```markdown
  **_Bold and Italic_**
  ```

## Lists

### Unordered Lists

Use asterisks (`*`), plus signs (`+`), or hyphens (`-`) to create unordered lists.

```markdown
- Item 1
- Item 2
  - Sub-item 1
  - Sub-item 2
```

Produces:

- Item 1
- Item 2
  - Sub-item 1
  - Sub-item 2

### Ordered Lists

Use numbers followed by periods to create ordered lists.

```markdown
1. First item
2. Second item
   1. Sub-item 1
   2. Sub-item 2
```

Produces:

1. First item
2. Second item
   1. Sub-item 1
   2. Sub-item 2

## Links

To create a link, enclose the link text in square brackets `[ ]` and the URL in parentheses `( )`.

```markdown
[Google](https://www.google.com)
```

This will create a clickable link: [Google](https://www.google.com).

## Images

Images use a similar syntax to links, but you start with an exclamation mark (`!`).

```markdown
![Alt Text](https://example.com/image.jpg)
```

This will display an image with the provided URL.

## Blockquotes

Blockquotes are used for quoting text. Simply use the `>` symbol at the beginning of a line.

```markdown
> This is a quote.
```

Produces:

> This is a quote.

## Code Blocks

### Inline Code

For inline code, surround your code with backticks `` ` ``.

```markdown
Here is some `inline code`.
```

Produces:
`print("hello")`

### Block Code

For multiple lines of code, use three backticks (` ``` `) or indent the code by four spaces.

```python
def hello_world():
    print("Hello, world!")
```

## Horizontal Rules

You can create a horizontal rule using three or more asterisks (`***`), hyphens (`---`), or underscores (`___`).

```markdown
---
```

Produces:

---

## Tables

You can create tables using pipes (`|`) and hyphens. The columns are separated by pipes, and the header row is distinguished by using hyphens (`-`).

```markdown
| Header 1 | Header 2 | Header 3 |
| -------- | -------- | -------- |
| Row 1    | Data 1   | Data 2   |
| Row 2    | Data 3   | Data 4   |
```

Produces:

| Header 1 | Header 2 | Header 3 |
| -------- | -------- | -------- |
| Row 1    | Data 1   | Data 2   |
| Row 2    | Data 3   | Data 4   |

## Footnotes

Markdown footnotes are supported in some platforms. You can define a footnote by using a caret (`^`) and square brackets `[ ]`, and then define the footnote text later in the document.

```markdown
Here is a sentence with a footnote.[^1]

[^1]: This is the footnote text.
```
