# LaTeX - How to

## Basic structure

Every document starts with a ```\documentclass{}```, that tells the compiler what
kind of document, we want to create. The type goes into the curly braces.

Common document types are:

| Documenttype | Description |
|:-------------|:------------|
| article      |             |

Before the curly braces you can set options that apply to your document. The font
size for example. I usually put the ```a4paper``` option, as that is what my printer
uses.

```latex
% fist line of the document, regular font size is 12pt on a a4paper
% we are writing an article
\documentclass[12pt,a4paper]{article}
```

This is a very typical header. Notice that lines that start with ```%``` are comments
and will be ignored by the compiler. This is a way for you to add commentary to
your code, comment out lines with errors and for me to explain things in the examples.

The next necessary step ist to tell LaTeX where our document starts and where it
ends. We do that by using the ```\begin{}``` macro and put ```document``` in the
curly braces. We can't begin a document without ending it aswell. So we put
```\end{document}``` below the ```\begin{document}```.
LaTeX now knows, where the document starts and ends. This is basically the most
minimal document you can write. Although it has no content yet.
So we can just write some words in between ```begin``` and ```end``` and compile
it for the first time.

```latex
\documentclass[12pt,a4paper]{article}

\begin{document}
Here is some example text.
\end{document}
```

This is what our doucument looks like so far.

## Compiling

## Lists

## Tables

## References
