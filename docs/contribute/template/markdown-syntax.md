---
title: Quick Guide to Markdown Syntax
---

# Using Markdown Syntax in Docusaurus Documentation

Docusaurus supports using **Markdown** as the primary content authoring format and compiles Markdown files into React components via the MDX compiler. This article introduces commonly used Markdown syntax and its usage in Docusaurus.

## 1. Headings

Use `#` for a first-level heading, `##` for a second-level heading, and so on.

```markdown
# First-level heading
## Second-level heading
### Third-level heading
```

## 2. Emphasis

- **Bold**: `**bold**` or `__bold__`
- _Italic_: `*italic*` or `_italic_`

## 3. Links and Images

- Link: `[Docusaurus Official Site](https://docusaurus.io/)`
- Image: `![Image description](/img/docusaurus.png)`

## 4. Code Blocks

Wrap code with triple backticks. You can specify the language for syntax highlighting:

````markdown
```js
console.log('Hello, Docusaurus!');
```
````
Demo:
```js
console.log('Hello, Docusaurus!');
```

## 5. Blockquotes
Use `>` for blockquotes:

```markdown
> This is a blockquote.
```
Demo:
> This is a blockquote.


## 6. Details

Docusaurus supports embedding HTML elements like `<details>`, with beautiful styles:

```markdown
<details>
  <summary>Click to expand</summary>
  Here is the detailed content, which can include **Markdown** syntax.
</details>
```
Demo:
<details>
  <summary>Click to expand</summary>
  Here is the detailed content, which can include **Markdown** syntax.
</details>



## 7. Front Matter

Each Markdown file can have metadata at the top, wrapped in three dashes, using YAML format:

```markdown
---
title: Document Title
description: This is the document description
---
```

## 8. MDX vs. CommonMark

- Docusaurus v3 uses the MDX parser for all `.md` and `.mdx` files by default, allowing you to embed React components directly in Markdown.
- To use standard CommonMark, set `markdown.format: 'detect'` in `docusaurus.config.js`. `.md` files will be parsed with CommonMark, `.mdx` with MDX.
- See the [official documentation](https://docusaurus.io/docs/markdown-features#mdx-vs-commonmark) for details.

## 9. Admonitions

````markdown
:::note
Content
:::

# Other available types
[note/tip/info/warning/danger]
````

:::note

Some **content** with _Markdown_ `syntax`. Check [this `api`](#).

:::

:::tip

Some **content** with _Markdown_ `syntax`. Check [this `api`](#).

:::

:::info

Some **content** with _Markdown_ `syntax`. Check [this `api`](#).

:::

:::warning

Some **content** with _Markdown_ `syntax`. Check [this `api`](#).

:::

:::danger

Some **content** with _Markdown_ `syntax`. Check [this `api`](#).

:::

## 10. Docusaurus-Specific Features

- Supports [Tabs](https://docusaurus.io/docs/markdown-features#tabs), [Admonitions](https://docusaurus.io/docs/markdown-features#admonitions), [Math Equations](https://docusaurus.io/docs/markdown-features#math-equations), and other extended syntax.
- You can directly insert React components into documents via MDX.


## 11. References

- [Docusaurus Official Markdown Features Documentation](https://docusaurus.io/docs/markdown-features)

---

To experiment with MDX syntax, use the [MDX Playground](https://mdxjs.com/playground/).
