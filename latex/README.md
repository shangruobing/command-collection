# Latex

LaTeX is a high-quality typesetting system; it includes features designed for the production of technical and scientific documentation. LaTeX is the de facto standard for the communication and publication of scientific documents.

## Installation

- [TeX Live](http://tug.org/texlive/)
- [Visual Studio Code](https://code.visualstudio.com)
- [Overleaf](https://www.overleaf.com)

## Document Structure

The `\documentclass` command must appear at the start of every document. The text in the curly brackets specifies the document class.

```tex
\documentclass[a4paper, 12pt]{article}

\begin{document}
  A sentence of text.
\end{document}
```

Document classes include:

- `article` shorter documents such as journal articles and short reports.
- `report` longer documents with chapters
- `proc` conference proceedings
- `book`
- `slides`

The text in the square brackets specifies options

> In this case it sets the paper size to A4 and the main font size to 12pt.

Anything typed before `\begin{document}` is known as the preamble, and will aﬀect the whole document.

Anything typed after `\end{document}` is ignored.

## Title

The `\maketitle` command creates a title.

```tex
\title{My First Document}
\author{My Name}
\date{\today}
\maketitle
```

Your document should now look like:

```tex
\documentclass[a4paper, 12pt]{article}

\begin{document}
  \title{My First Document}
  \author{My Name}
  \date{\today}
  \maketitle

  A sentence of text.
\end{document}
```

## Section

You should divide your document into chapters (if needed), sections and sub-sections.

- `\section{...}`
- `\subsection{...}`
- `\subsubsection{...}`
- `\paragraph{...}`
- `\subparagraph{...}`

```tex
\section{Introduction}
This is the introduction.

\section{Methods}

\subsection{Stage 1}
The first part of the methods.

\subsection{Stage 2}
The second part of the methods.

\section{Results}
Here are my results.
```

Your document should now look like:

```tex
\documentclass[a4paper, 12pt]{article}

\begin{document}
  \title{My First Document}
  \author{My Name}
  \date{\today}
  \maketitle

  \section{Introduction}
  This is the introduction.

  \section{Methods}

  \subsection{Stage 1}
  The first part of the methods.

  \subsection{Stage 2}
  The second part of the methods.

  \section{Results}
  Here are my results.
\end{document}
```

## Label

You can label any of the sectioning commands so they can be referred to in other parts of the document.
Label the section with `\label{labelname}`. Then type `\ref{labelname}` or `\pageref{labelname}`, when you want to refer to the section or page number of the label.

Your document should now look like:

```tex
\documentclass[a4paper, 12pt]{article}

\begin{document}
  \title{My First Document}
  \author{My Name}
  \date{\today}
  \maketitle

  \section{Introduction}
  This is the introduction.

  \section{Methods}

  \subsection{Stage 1}
  \label{sec1} The first part of the methods.

  \subsection{Stage 2}
  The second part of the methods.

  \section{Results}
  Here are my results. Referring to section \ref{sec1} on page \pageref{sec1}
\end{document}
```

## Table of Contents

If you use sectioning commands it is very easy to generate a table of contents. Type `\tableofcontents` where you want the table of contents to appear in your document — often directly after the title page.

```tex
\pagenumbering{roman}
\tableofcontents
\newpage
\pagenumbering{arabic}
```

## Word Processing

### Chinese Support

```tex
\usepackage[UTF8]{ctex}
```

The 'xelatex' command is used when compiling the document because it supports Chinese fonts.

### Font Effect

```tex
\textit{words in italics}
\textsl{words slanted}
\textsc{words in smallcaps}
\textbf{words in bold}
\texttt{words in teletype}
\textsf{sans serif words}
\textrm{roman words}
\underline{underlined words}
```

### Font Color

```tex
\usepackage{color}
{\color{colorname}text}
\colorbox{colorname}{text}
```

### Font Size

```tex
normal size words
{\tiny tiny words}
{\scriptsize scriptsize words}
{\footnotesize footnotesize words}
{\small small words}
{\large large words}
{\Large Large words}
{\LARGE LARGE words}
{\huge huge words}
```

### Indent

If you want a paragraph to be topped, prefix the paragraph you want to top with `\noindent`.
If you want all paragraphs to be highlighted globally, use the `\setlength{\parindent}{0pt}` command somewhere in the document

## List

Ordered (`enumerate`) and unordered (`itemize`). The elements in the list are defined as` \item`. Lists can have sublists.

```tex
\begin{enumerate}
  \item First thing

  \item Second thing
    \begin{itemize}
      \item A sub-thing
      \item Another sub-thing
    \end{itemize}

  \item Third thing
\end{enumerate}
```

## Comment

We use `%` to create a single-line comment, and anything on that line after that character will be ignored until the next line begins.

```tex
% This is a comment.
```

## Character

```text
# $ % ^ & _ { } ~ \
```

To use these characters, we need to escape them by prefixing them with a backslash:

```tex
\# \$ \% \^{} \& \_ \{ \} \~{}
```

## Table

- `l` represents a left-aligned column;
- `r` represents a right-aligned column;
- `c` represents a center-aligned column;
- `|` represents a vertical line between columns.

For example, `{lll}` creates a three-column table with all columns left-aligned and without explicit vertical lines. `{|l|l|r|}` creates a three-column table where the first two columns are left-aligned, the last column is right-aligned, and there are explicit vertical lines between adjacent columns.

The data for the table is input after `\begin{tabular}`:

- `&` is used to separate columns;
- `\\` is used for a line break;
- `\hline` inserts a horizontal line across all columns;
- `\cline{1-2}` inserts a horizontal line spanning the first and second columns.

Finally, the table is ended with `\end{tabular}`.

```tex
\begin{tabular}{|l|l|}
  Apples       & Green  \\
  Strawberries & Red    \\
  Orange       & Orange \\
\end{tabular}

\begin{tabular}{rc}
  Apples              & Green  \\
  \hline
  Strawberries        & Red    \\
  \cline{1-1} Oranges & Orange \\
\end{tabular}

\begin{tabular}{|r|l|}
  \hline
  8              & here's \\
  \cline{2-2} 86 & stuff  \\
  \hline
  \hline
  2008           & now    \\
  \hline
\end{tabular}
```

## Figure

You should import `\usepackage{graphicx}` to the document.

```tex
\begin{figure}[h]
  \centering
  \includegraphics[width=1\textwidth]{myimage}
  \caption{Here is my image}
  \label{image-myimage}
\end{figure}
```

`[h]` is a position parameter, where **h** indicates placing the figure approximately "here." **t** places it at the top of the page; **b** places it at the bottom of the page; **p** places it on a separate page for figures. You can also add an **!** to force the figure to be placed at the specified position.

`\centering` centers the image on the page. Without this command, the image will align to the left by default.

The `\includegraphics{...}` command automatically places the image into your document.

The `[width=1\textwidth]` option is optional and specifies that the image should be the same width as the text. Using `[scale=0.5]` scales the image proportionally (in this case, reducing the image to half its original size).

`\caption{...}` defines the caption for the figure. When this command is used, LaTeX will add a numbered "Figure" label to your figure.

You can generate a list of figures by using the `\listoffigures` command.

`\label{...}` creates a label that you can reference later in your document.

## Equation

You can use a pair of `$` symbols to enable math mode, which allows you to write inline mathematical expressions. For example, `$1+2=3$` will produce $1+2=3$.

```tex
\begin{equation}
  1+2=3
\end{equation}
```

## Reference

The BibTeX file contains all the documents you want to cite in your documents. It has a file extension named `.bib`

```text
@article{
    Birdetal2001,
    Author = {Bird, R. B. and Smith, E. A. and Bird, D. W.},
    Title = {The hunting handicap: costly signaling in human foraging strategies},
    Journal = {Behavioral Ecology and Sociobiology},
    Volume = {50},
    Pages = {9-19},
    Year = {2001}
}
```

Insert a reference list into the document.

```tex
\bibliographystyle{plain}
\bibliography{references}
```

Use `\cite{citationkey}` to insert a citation marker at the place where you want to reference a source.

To cite multiple references, separate them with commas: `\cite{citation01,citation02,citation03}`.

```tex
\cite{citationkey}
\cite{citation01,citation02,citation03}
```

## VS Code Settings

```json
{
  "latex-workshop.latex.tools": [
    {
      "name": "pdflatex",
      "command": "pdflatex",
      "args": ["-shell-escape", "-synctex=1", "-interaction=nonstopmode", "-file-line-error", "%DOCFILE%"]
    },
    {
      "name": "xelatex",
      "command": "xelatex",
      "args": ["-shell-escape", "-synctex=1", "-interaction=nonstopmode", "-file-line-error", "%DOCFILE%"]
    },
    {
      "name": "bibtex",
      "command": "bibtex",
      "args": ["%DOCFILE%"]
    },
    {
      "name": "biber",
      "command": "biber",
      "args": ["%DOCFILE%"]
    }
  ],
  "latex-workshop.latex.recipes": [
    {
      "name": "PdfLatex",
      "tools": ["pdflatex"]
    },
    {
      "name": "XeLatex",
      "tools": ["xelatex"]
    },
    {
      "name": "BibTex",
      "tools": ["bibtex"]
    },
    {
      "name": "pdf->biber->pdf*2",
      "tools": ["pdflatex", "biber", "pdflatex", "pdflatex"]
    },
    {
      "name": "xe->bibtex->xe*2",
      "tools": ["xelatex", "bibtex", "xelatex", "xelatex"]
    },
    {
      "name": "pdf->bibtex->pdf*2",
      "tools": ["pdflatex", "bibtex", "pdflatex", "pdflatex"]
    }
  ],
  "latex-workshop.latexindent.path": "/usr/local/texlive/2024/bin/universal-darwin/latexindent",
  "latex-workshop.message.error.show": true,
  "latex-workshop.message.warning.show": true,
  "latex-workshop.latex.autoClean.run": "onBuilt"
}
```
