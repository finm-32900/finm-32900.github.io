# Week 4: Generating Reports, featuring Jupyter Notebooks and LaTeX 

## Learning Outcomes
 
 - Familiarity with using Markdown cells within Jupyter Notebooks
   - Why should I only use Jupyter notebooks for final reports (not as steps within the pipeline)?
   - Familiarity with `nbconvert` to convert notebooks to scripts, HTML, PDFs
   - Using `nbconvert` to execute a notebook from the command line. (Why would we want to do this?)
   - How to fit a notebook into the PyDoit workflow? (Use the workflow set up in my `blank_project` GitHub template repo.)
 - Basic familiarity with LaTeX.
   - Ability to edit and compile LaTeX templates in `blank_project` repo using `TeXworks` (which is included with TeX Live).
   - Understanding of how to automate the inclusion of an image or table into a LaTeX document.

## Agenda

- Introduction Compustat and CRSP/Compustat Merged Data
- CRSP industry merge example
- Review HW 2. Meaning of new series? Lessons learned note? What were some gotchas?
    - People downloaded data in different ways. Some in fixed-width format, some in CSV format. Some included different samples, e.g. different time periods. Some included extra columns than others.
    - Some people had errors with the handling of the dates when using `.describe()`. This came up because they were using the wrong version of Pandas. Importance of using `requirements.txt` and `conda` environments.
    - `s24` didn't pass even though all previous tests pass. Unit tests sometimes don't cover all corner cases.
    - Slipped in `.env` into GitHub repo and that caused everything to fall apart. Important to never commit `.env` to your GitHub repo.
    - VS Code editor tips. Send code to interactive tab option and shift enter. Step through code because loading can take a long time.
- Final projects. Show example based on blank template. List will be released. Submit survey with group member names. Rank projects. 
- Review WRDS Python package functionality using [walkthrough here.](../../output/_01_wrds_python_package.ipynb)
- Review CRSP and Compustat cleaning procedure.
- Discuss generation of value weighted market index in terms of psuedo code?
- [Introduction to LaTeX](./intro_to_LaTeX.md)
- Generating reports with LaTeX in dodo.py
- Automatic generation of HTML notebook reports. Why are notebooks difficult with Git?



