# Latex 

## Introduction 

LaTeX is a document preparation system used to produce professional-looking documents. Unlike traditional word processors, LaTeX emphasizes content over appearance by allowing the authors to focus on document structure while typesetting is handled automaticaly. LaTeX is particularly suited for creating long, structured documents and typesetting equations.

> **Key Features of LaTeX** 
> - Produces high-qualty documents. 
> - Ideal for academic papers, documents with mathematical equations, theses, and technical documents. 
> - Typesets mathematical equations with precision. 

## Compiling LaTeX Files: 

To compile a `.text` file into a readable format like a `.pdf`, the command line or a LaTeX editor can be used. 

```Bash
# Compile a LaTeX file to a .dvi file
latex [filename].tex 
> output is [filename].dvi

# Compile a LaTeX file directly to a .pdf 
pdflatex [filename].tex
> output is [filename].pdf

# Convert a .dvi file to a PostScript (.ps) file
dvips -o [filename].ps [filename].dvi
> output is [filename].ps

# Convert a .dvi file to a .pdf 
dvipdfm [filename].dvi
```

-- 

## Essentials of LaTeX

### Document Structure 

Every LaTeX document starts with a `\documentclass` declaration, specifying the document type, followed by content wrapped in a `document` environment:

```latex
\documentclass[a4paper,12pt]{article}
\begin{document}
    \title{My First Document}
    \author{Author Name}
    \date{\today}
    \maketitle
\end{document}
```

### Sections and Labels

Divide your document into sections for better organization:

```latex
\section{Introduction}
This is the introduction.

\section{Methods}
\subsection{Step 1}
The first step.

\section{Results}
Results are shown in Figure \ref{fig:example}.
```

---

## Creating Tables

To create a table, use the `tabular` environment:

```latex
\begin{tabular}{|l|c|r|}
\hline
Item & Quantity & Price (\$) \\
\hline
Nails & 500 & 0.34 \\
Wooden boards & 100 & 4.00 \\
Bricks & 240 & 11.50 \\
\hline
\end{tabular}
```

---

## Adding Figures

To include images, add the `graphicx` package in the preamble and use the `figure` environment:

```latex
\usepackage{graphicx}

\begin{figure}[h]
    \centering
    \includegraphics[width=0.8\textwidth]{example.png}
    \caption{An example image}
    \label{fig:example}
\end{figure}
```

---

## Writing Equations

LaTeX provides multiple ways to write mathematical equations:

- **Inline equations:** `$E = mc^2$`
- **Displayed equations:**
```latex
\begin{equation}
    E = mc^2
\end{equation}
```

- **Equation arrays:**
```latex
\begin{eqnarray}
    a & = & b + c \\
      & = & y - z
\end{eqnarray}
```

---

## References

LaTeX can manage references and citations using BibTeX. Create a `.bib` file with references:

```bibtex
@article{example,
    Author = {Author Name},
    Title = {Title of the Paper},
    Journal = {Journal Name},
    Year = {2021}
}
```

Include the bibliography in your `.tex` file:

```latex
\bibliographystyle{plain}
\bibliography{references}
```

---

## Further Reading

- [LaTeX Project](http://www.latex-project.org/)
- [LaTeX Wikibook](http://en.wikibooks.org/wiki/LaTeX/)
- [Not So Short Introduction to LaTeX](http://ctan.tug.org/tex-archive/info/lshort/english/lshort.pdf)

---

###Keybinding Summary
    * <leader>lt: Create a LaTeX file with a basic template.
    * <leader>ld: Save the .tex file and return to the markdown file.
    * <leader>lc: Compile the LaTeX file and move the PDF to SupportingFiles.
    * <leader>lm: Monitor the LaTeX file for changes and recompile on Enter or ..
    * <leader>ll: Link the PDF to the markdown file in markdown format.


