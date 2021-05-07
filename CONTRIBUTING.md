# Contributing

## Ways to contribute

You can:

- write guides,
- proofread and correct them,
- review and discuss pull requests,
- suggest changes regarding this project.

### Writing / editing guides

Fork this repository, create and checkout a new branch (this is important, since
I intend to use squash merges, which would cause your `master` to be different
from upstream if you used `master` for pull requests). Do the changes you want
to do and submit a pull request on GitHub.

If you explicitly want to discuss something, still have work to be done (but you
want to prevent effort duplication) or don’t want the pull request to be merged
yet, mark it as a draft. This is why the posibility exists.

Try to follow the recommendations in the other part of this file, most of them
will be enforced anyway. If they do not mention something, the reviewer will try
to enforce their style. In case a reviewer points on something that doesn’t
match their style but matches yours, please open an issue or discuss it in the
pull request conversation; we have to agree on one or the other way and add it
to these guidelines.

### Reviewing pull requests

Do not be shy to suggest changes and point out mistakes. The goal is to have
good guides (although it is not a good idea to block a pull request for more
than a week with nitpicks).

You can also discuss the reviews by others.

### Suggesting changes

Create an issue and describe the suggestion. You can also create a pull request
if you have a more concrete idea—in that case it will be discussed there.

---

## File names

Unless you have a specific reason to do otherwise, use the ASCII hyphen `-` to
separate words and use only the characters a—z (lowercase), 0—9, the ASCII
hyphen `-` and dot `.` in file names.

## Writing style

- Write in sentences (you can choose how to write lists, but stay consistent in
  the whole file),
- use capital letters only where appropriate,
  - in headings, only the first word should start with a capital letter unless
    there is a name (this isn’t the standard style, but helps legibility),
- split text into paragraphs,
- group paragraphs under headings (use different levels, every document should
  contain exactly one level-one heading),
- use _italics_ and **bold** as needed, but don’t overuse them (that is,
  highlight what is important, but do not mark every verb and object),
- prefer American English style to British English style (I will have a problem
  with that):
  - use double quotes on the top level, each level exchanges the style,
  - use the em dash—without spaces, like shown here,
  - if you cannot differentiate the styles, no problem; it’s just for
    consistency,
- you can use short forms (I’m, you’re), but try to avoid words like “gonna,”
  “wanna,”
- prefer the words “and” and “or” to the characters “&” and “/”,
- use only ASCII in source code (except for strings, of course); prefer the more
  specific character otherwise.

## Images etc.

Images and other resources like them are in an `assets/` directory in the root
of the corresponding “project,” structured according to their use.

- Keep images as small (in both area and size) as possible,
- prefer static images to gifs or videos,
- try to keep them dark: use the “Dark” Vivaldi theme and the dark developer
  tools theme; if you show a web page, choose a dark one,
- if they contain code (which should happen only in case you are showing an
  environment or something; you should never use images to show code), make sure
  it follows the code style specifications.

## Code style / file format

- Indent with two spaces,
- try to keep every line short; in plain text, wrap lines at column 80,
- end every line with a line feed character (every means even the last one),
- do not use multiple empty lines without a good reason,
- avoid trailing whitespace,
- use comments as appropriate.

### Markdown

- Try to avoid HTML,
- use the hash `#` character for headings,
- use the underscore `_` character for _italics_; double asterisk `**` for
  **bold**,
- use three ASCII hyphens `---` for separators,
- use ordered lists only when the order matters,
- use the ASCII hyphen for unordered lists,
- do not interrupt lists; instead, indent continuation of any items,
- use three backticks for code blocks, always specify the language,
- add a space after `#` in headings and each `>` in block quotes,
- do not rely on implicit continuation of block quotes and similar,
- separate lists, block quotes, code blocks, headings, separators, images
  (unless they are inline) and similar from other content with a blank line on
  each side,
- specify links like “here” inline or using a reasonable identifier; links like
  “CSS” (with the address going to a specification or Wikipedia entry, not a
  guide) should use the reference style,
- specify the address of reference links at the end of the section where you use
  them; if you use them across several sections, consider them to be used in the
  section one level higher.

### CSS

- Make a separate line for every selector (so that commas are at the end of
  lines) and rule,
- however long a selector is, don’t break it into lines,
- the same for `url()` and similar,
- put opening braces at the end of the line, separated from the selector with a
  space,
- put closing braces on separate lines,
- use semicolons even after last rule in a block,
- indent continuations of long values relative to the value (not the property
  name),
  - it is preferable to start long values on a new line,
- separate blocks with empty lines (in case you ever need to group some blocks
  into sections without comments, separate only the sections, not blocks within
  a section),
- put spaces at the start and end of comments.

### JavaScript

- Put all types of opening brackets at the end of the line,
- put closing brackets and braces on a new line,
- keep closing parentheses at the same line as the statement they close,
- use semicolons even where they aren’t necessary,
- prefer `const` where possible; **never** use `var`,
- use camelCase for variable names; start them with a lowercase letter (classes
  start with an uppercase letter),
- use `SHOUTING_SNAKE_CASE` for constants defined in code (as opposed to
  constants generated during runtime),
- prefer line comments to block comments,
- put spaces at the start and end of block comments and at the start of line
  comments.
