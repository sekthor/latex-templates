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

Also note that these options in the quare brackets are no necessity. So I will not
use them for now.

The next necessary step ist to tell LaTeX where our document starts and where it
ends. We do that by using the ```\begin{}``` macro and put ```document``` in the
curly braces. We can't begin a document without ending it aswell. So we put
```\end{document}``` below the ```\begin{document}```.
LaTeX now knows, where the document starts and ends. This is basically the most
minimal document you can write. Although it has no content yet.
So we can just write some words in between ```begin``` and ```end``` and compile
it for the first time.

```latex
\documentclass{article}

\begin{document}
Here is some example text.
\end{document}
```

This is what our doucument looks like so far.

## Compiling

To compile the document we need to have some form of LaTeX installed. If you
install a LaTeX editor it will come with that. There are different products
available, but they all work alike. You type your document, hit the compile button
and the IDE will take care of everything.

To understand what is going on in the background, we are going to compile manually.
Save your LaTeX code with the ```.tex``` file extension.

Then you simply run

```sh
pdflatex /path/to/doument.tex
```

The programm will have compiled your document to a pdf file with the same name.
Not that there are a bunch of more files with different extensions in the directory.
Those are files the compiler needs when compiling. There no longer needed after it's
finnished. It is save to delete them.

## Lists

## Tables

## References
