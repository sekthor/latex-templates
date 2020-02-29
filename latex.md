# LaTeX - How to

This is my guide on how to use LaTeX. It mostly consits of my own notes I took when
first getting into LaTeX. Topics covereed are:

- [Basic structure](#Basic-structure)
- [Copiling](#compiling)
- [Title](#title)
- [Headings](#headings)
- [Lists](#lists)
- [Tables and figures](#Tables-and-Figures)
- [Table of contents](#table-of-contents)
- [Index](#index)
- [References](#References)
  - [Citations](#Citations)
  - [Bibliography](#Biliography)
  - [APA-citations](#APA-citations)
- [Links (Hyperref)](#links-(hyperref))

## Basic structure

Every document starts with a ```\documentclass{}```, that tells the compiler what
kind of document, we want to create. The type goes into the curly braces.

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

Common document types are:

| Type     | Description |
|:---------|:------------|
| article  | For articles in scientific journals, presentations, short reports, program documentation, invitations. |
| IEEEtran | For articles with the IEEE Transactions format.|
| proc     | A class for proceedings based on the article class.|
| report   | For longer reports containing several chapters, small books, thesis, ...|
| book     | For real books.|
| slides   | For slides. The class uses big sans serif letters.|
| memoir   | For changing sensibly the output of the document. It is based on the book class, but you can create any kind of document with it [1]|
| letter   | For writing letters.|
| beamer   | For writing presentations (see LaTeX/Presentations).|

Common options are:

| option | Description |
|:-------|:------------|
| 10pt, 11pt, 12pt | Sets the size of the main font in the document. If no option is specified, 10pt is assumed. |
|a4paper, letterpaper,... | Defines the paper size. The default size is letterpaper; However, many European distributions of TeX now come pre-set for A4, not Letter, and this is also true of all distributions of pdfLaTeX. Besides that, a5paper, b5paper, executivepaper, and legalpaper can be specified. |
| fleqn | Typesets displayed formulas left-aligned instead of centered.|
| leqno | Places the numbering of formulas on the left hand side instead of the right. |
| titlepage, notitlepage | Specifies whether a new page should be started after the document title or not. The article class does not start a new page by default, while report and book do.|
| twocolumn | Instructs LaTeX to typeset the document in two columns instead of one.|
| twoside, oneside | Specifies whether double or single sided output should be generated. The classes article and report are single sided and the book class is double sided by default. Note that this option concerns the style of the document only. The option twoside does not tell the printer you use that it should actually make a two-sided printout.|
| landscape | Changes the layout of the document to print in landscape mode.|
| openright, openany | Makes chapters begin either only on right hand pages or on the next page available. This does not work with the article class, as it does not know about chapters. The report class by default starts chapters on the next page available and the book class starts them on right hand pages. |
| draft | makes LaTeX indicate hyphenation and justification problems with a small square in the right-hand margin of the problem line so they can be located quickly by a human. It also suppresses the inclusion of images and shows only a frame where they would normally occur. |

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

## Title

On of the first things you usually want to do in a document is to give it a title.
The ```\maktitle``` macro will display the title, author name and date.

In order for this to work, you need to set ```\title{}``` and ```\author{}```.
The date will be automatically set to todays date. You can change it by adding
the desired date into ```\date{}```. If don't want one of the three values in
your title, you can leave the curly braces blank.

So with the title our document now looks like this:

```latex
\documentclass{article}

\title{Title of Document}
\author{Your Name}

\begin{document}

\maketitle

Here is some example text.
\end{document}
```

## Headings

To structure your contnent with headings and subheadings, you can call ```\section{}```.
The Title of your section (heading) goes in the curly braces. If you want to subdivide
your sections you can call ```\subsection{}```. The sections and subsections, are
numbered automatically by LaTeX.

```latex
\documentclass{article}

\title{Title of Document}
\author{Your Name}

\begin{document}

\maketitle

\section{Title}
Here is some example text. Random words just to to fill a paragraph are added.

\subsection{Subtitle}
Here is some text in a subsection.

\subsubsection{Subsubtitle}
Here is some text in a subsubsection.
\end{document}
```

The output looks like this:

![image](img/section.png)

## Lists

Lists are very simple to create. All you need to do is to decide whether you want
your list to be ordered (```enumerate```) or unordered (```itemize```).

```latex
% A numbered list
\begin{enumerate}
    \item{Item 1}
    \item{Item 2}
\end{enumerate}

% An unordered list
\begin{itemize}
    \item{Item 1}
    \item{Item 2}
\end{itemize}
```

## Tables and Figures

```latex
\begin{table}            % will create the float environment
\centering               % centers table
\begin{tabular}{|l|c|r|} % tell LaTeX number of columns and their alignment
\hline                   % horizontal line
Heading 1 & Heading & Heading 3 \\ % columns separated by &, end of row with \\
\hline
1 & 2 & 3 \\
\hline
\end{tabular}
\end{table}
```

## Table of Contents

If you want to have an index of all your sections and subsections you can use the ```\tableofcontents```
macro. This is going to look like this:

![image](img/tableofcontents.png)

## Index

To create an Index of keywords, and what page to find them on, you can use the ```makeidx```-package. You will have to include the ```\makeindex``` macro in the preamble. Each mention of the Keyword you would like to index, you can annotate using the ```\indedx{keyword}``` macro.

To actually show the index, use ```\printindex```.

```latex
\documentclass{article}
\usepackage{makeidx}

\makeindex

\title{Title of Document}
\author{Your Name}

\begin{document}

\maketitle

Here is some text metioning the keyword.\index{keyword}

\printindex

\end{document}
```

![image](img/index1.png)
![image](img/index2.png)

## References

You can use BibTeX with LaTeX to manage all the references in your paper.
To do so you need a separate biblioraphy file with the ```.bib``` file
extension.

In this file you save all the sources you want to reference. The BibTeX
format looks like this:

```bibtex
@book{nameOfTheSource,
  title={Title of the source},
  author={Name of Author1, Name of Author2},
  booktitle={Title of the Book},
  pages={100},
  year={2020},
  publisher={Verlag},
  address={Verlagsaddresse}
}
```

At first you specify the type of the source you are refencing (```@book```,
```@article```, ```@journal```, ...). Note that not all types are supported
by all documentclasses. See [here](https://en.wikibooks.org/wiki/LaTeX/Bibliography_Management#BibTeX)
for details.

Then you give the source a name. You will use this name every time you
reference the source. A good idea is to use the format of author name plus
year.

### Citations

To actually cite a reference, we use the ```\cite``` macro. The options allow
for you to specify a page number.

```latex
This is some text, taken from a different source. \cite{nameOfTheSource}

In this sentence I'm including the pagenumber. \cite[p.~150]{nameOfTheSource}
```

### Bibliography

To include all the references in your document, you need to use
```\bibliography{}``` with the name of your bibliography file. You don't need to
write the ```.bib``` file extension. You do however need to specify a
```\bibliographystyle{}```. For starters, you can just use the regular ```plain```
style.

```latex
\bibliographystyle{plain}
\bibliography{filename}
```

### APA-Citations

There is a standard ```apalike```-style included. However, it does not comply
copletely with the way APA dictated how to cite references. To fix this, you need
to install the ```apacite``` package ([apacite](https://ctan.org/pkg/apacite)).

```latex
\usepackage{apacite}
[...]
\bibliographystyle{apacite}
\bibliography{filename}
```

## Links (Hyperref)

One of the cool features of LaTeX is the ability to link to places within or
outside your document. This is pretty neat, as you can klick on a section in your
table of contents for example and be brought right to that section.

The manual way to do stuff like that, is to set a label to where you want to
point to. Then you can use ```\ref{}```, to reference this label.

```latex
\section{Section}\label{sec1}
This is a section i want to point to.

\section{Mention}
In this section I am mention Section \ref{sec1}.
```

This will put the number of the section into the text, and when clicked bring
the reader to that section. Should the order of the sections change, the number
will update correctly.

Of course you can also set custom links in your document. To achieve this effect you only need to use the package ```hyperref```.

```latex
\usepackage{hyperref}
```

This will automatically link all elements in the table of contents to their
section. The same is true for all kinds of indexes. If you would like to make
a custom reference to something in your document you can do the following.

```latex
\section{Section}\label{sec1}
This section will be referenced.

\section{Mention}
When a reader clicks \hyperref{sec1}{here}, he will be brought to section 1.
```

You can also put links to external places in your document, using one of those
methods:

```latex
\url{<my_url>}                 % show link in monospace font
\href{<my_url>}{<description>} % show description in regiular font
```
