# Week 5: Publishing Reports with LaTeX

```{toctree}
:maxdepth: 1
Week4/intro_to_LaTeX.md
Week4/latex_essentials.md
Week7/LSEG_datastream.md
Week7/databento.md
```

## Learning Outcomes

- Basic familiarity with LaTeX: edit and compile the templates in the `blank_project` repo using `TeXworks` (included with TeX Live).
- Understand how to automate the inclusion of an image or table into a LaTeX document, so a PDF report rebuilds itself from your pipeline's outputs.
- Brief, as-needed exposure to additional data vendors (LSEG Datastream via WRDS, Databento).

## Agenda

Last week we published an HTML report (the ChartBook site) to GitHub Pages. This week is the other half of report generation: **LaTeX and PDFs**.

- **LaTeX for reports**: [Introduction to LaTeX](./Week4/intro_to_LaTeX.md) and [LaTeX Essentials](./Week4/latex_essentials.md). Compile the `blank_project` templates in `TeXworks`, and automate pulling a generated chart or table into the document — the same automated-pipeline idea as ChartBook, but producing a PDF.
- **Data vendors (brief, as they come up)**: [LSEG Datastream](./Week7/LSEG_datastream.md) via WRDS and [Databento](./Week7/databento.md). We'll keep these light and return to them when a project needs them.

% INSTRUCTOR-ONLY (does NOT render). To flesh out for the Week 5 class next pass:
%  - Introduce the MIDTERM REPORT here: a single shared GitHub repo that all students
%    contribute to via pull requests; PDF built from LaTeX; each student's charts should
%    relate to their assigned final project. (Kept OUT of Week 4 deliberately.)
%  - GitHub pull-request / open-source contribution workflow (currently in Week 6:
%    Week6/GitHub_pull_requests.md) pulls forward to here.
%  - Publishing a package to PyPI (chartbook / finm as the example), teed up by the
%    Week 4 ChartBook discussion.
%  - Bloomberg is NOT offered this quarter (online students lack terminal access); the
%    reference page now lives in the Appendix.
