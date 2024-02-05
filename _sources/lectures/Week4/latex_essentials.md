# LaTeX Essentials

Now that we've introduced the concept of LaTeX and discussed how to compile a document, we'll now go over a few of
the essential pieces that you'll need to know.

For this, we'll review each of the concepts listed below as they appear in `/reports/report_example.tex` in my `blank_project` repository: https://github.com/jmbejara/blank_project.

## Environments

In LaTeX, environments are used to define specific sections of a document that have different formatting or behavior. They are initiated with the `\begin{environmentName}` command and closed with the `\end{environmentName}` command. The `itemize` environment, for example, is used to create bullet lists. Each environment provides a set of formatting rules or structures, such as list environments (`itemize`, `enumerate`), table environments (`tabular`), mathematical environments (`equation`), and many others, catering to various types of content structuring and formatting needs.

```latex
\begin{itemize}
\item Something
\item Another thing
\item Something else
\end{itemize}
```

## The Various Equation Environments

- Inline math with `$y = x^2$`. This would inline like this: $y = x^2$.
- Display math with `$$`, vs `equation` environment

Display math with `$$`
```latex
$$
\frac{\partial V}{\partial t} + \frac{1}{2}\sigma^2 S^2 \frac{\partial^2 V}{\partial S^2} 
+ rS\frac{\partial V}{\partial S} - rV = 0
$$
```
will be rendered like this:
$$
\frac{\partial V}{\partial t} + \frac{1}{2}\sigma^2 S^2 \frac{\partial^2 V}{\partial S^2} + 
rS\frac{\partial V}{\partial S} - rV = 0
$$
This will do the same thing:

```latex
\begin{equation}
\frac{\partial V}{\partial t} + \frac{1}{2}\sigma^2 S^2 \frac{\partial^2 V}{\partial S^2} 
+ rS\frac{\partial V}{\partial S} - rV = 0
\end{equation}
```

- `align` environment for equations. Sometimes you want to align several equations for the purpose of derivations. For example, this code

```latex
\begin{align}
P(S_t, t) &= Ke^{-r(T - t)} - S_t + C(S_t, t)  \\
          &= N(-d_-) Ke^{-r(T - t)} - N(-d_+) S_t 
\end{align}
```

produces the following:

\begin{align}
P(S_t, t) &= Ke^{-r(T - t)} - S_t + C(S_t, t)   \\
          &= N(-d_-) Ke^{-r(T - t)} - N(-d_+) S_t 
\end{align}

## Tables and Figures

- `tabular` vs `table` environment

The `tabular` environment in LaTeX is used to create a table with specified alignment for columns, without providing floating capabilities. It's useful for inserting tables directly in the text flow. On the other hand, the `table` environment is a floating container that allows you to position tables in a more flexible manner within the document, including adding captions and labels for referencing. The `table` environment can encapsulate a `tabular` environment, enabling the table to float and be captioned, but `tabular` is what actually defines the table's structure and content.

A minimal working example of a document with a table would look like this:
```latex

\documentclass{article}
\usepackage{booktabs}
\begin{document}
First document. This is a simple example, with no 
extra parameters or packages included.

\begin{table}
\centering
\begin{tabular}{lrrrrr}
\toprule
 & 0 & 1 & 2 & 3 & 4 \\
\midrule
0 & 0.543405 & 0.278369 & 0.424518 & 0.844776 & 0.004719 \\
1 & 0.121569 & 0.670749 & 0.825853 & 0.136707 & 0.575093 \\
2 & 0.891322 & 0.209202 & 0.185328 & 0.108377 & 0.219697 \\
3 & 0.978624 & 0.811683 & 0.171941 & 0.816225 & 0.274074 \\
4 & 0.431704 & 0.940030 & 0.817649 & 0.336112 & 0.175410 \\
\bottomrule
\end{tabular}
\end{table}
\end{document}

```

Automating the generation of the tables can be done by swapping out the tabular environment and generating that from
a Pandas DataFrame.

```latex
\documentclass{article}
\usepackage{booktabs}
\begin{document}
First document. This is a simple example, with no 
extra parameters or packages included.

\begin{table}
\centering
\input{example_table.tex}
\end{table}
\end{document}
```
where `example_table.tex` is generated from 
code like this:
```python
import pandas as pd
import numpy as np
np.random.seed(100)

import config
from pathlib import Path
DATA_DIR = Path(config.DATA_DIR)
OUTPUT_DIR = Path(config.OUTPUT_DIR)


## Suppress scientific notation and limit to 3 decimal places
# Sets display, but doesn't affect formatting to LaTeX
pd.set_option('display.float_format', lambda x: '%.2f' % x)
# Sets format for printing to LaTeX
float_format_func = lambda x: '{:.2f}'.format(x)


df = pd.DataFrame(np.random.random((5, 5)))
latex_table_string = df.to_latex(float_format=float_format_func)
print(latex_table_string)

path = OUTPUT_DIR / f'pandas_to_latex_simple_table1.tex'
with open(path, "w") as text_file:
    text_file.write(latex_table_string)

```
## Labels and References

- Demonstrate labels and references, using `tag` and `ref`.

## Bibliographies

- Bibliography, with `.bib` files and `\cite{}`. Use Google Scholar to add bibliography entry to BibTeX file and then cite the paper in the LaTeX document.