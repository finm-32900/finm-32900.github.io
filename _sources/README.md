Course Syllabus: FINM 32900, Winter 2025
========================================

**FINM 32900, Full Stack Quantitative Finance**

##  Summary

**Course Description** "Full Stack Quantitative Finance" is a hands-on course
centered on a core set of fundamental tools common across 
financial computing and data science. 
That is, this course examines elements of
the analytical pipeline, from data extraction and cleaning to exploratory
analysis, visualization, and modeling, and finally, publication and deployment.
It does so with the aim of teaching the tools and principles behind creating
reproducible and scalable workflows, including build automation, dependency
management, unit testing, the command-line environment, shell scripting, Git for
version control, and GitHub for team collaboration. These skills are taught
through case studies, each of which will additionally give students practical
experience with key financial data sets and sources such as CRSP and Compustat
for pricing and financials, macroeconomic data from FRED and the BEA, bond
transactions from FINRA TRACE, Treasury auction data from TreasuryDirect,
textual data from EDGAR, and high-frequency trade and quote data from NYSE.
Prior experience at an intermediate level with Python and the PyData stack is
assumed.

- **Class:** Mondays, 6 - 9 PM, in-person at the Stevanovich Center building,
  Room #112. (5727 S. University Ave.)
- **Lecturer:** Jeremy Bejarano, jbejarano@uchicago.edu
- **Instructor Office Hours:** Monday, 5 - 6 pm, in the FinMath library (first floor of the Stevanovich Center, 5727 S. University Ave.)
- **Teaching Assistants:**
  - Viren Desai, vdd@uchicago.edu
  - Nick Lewis, nicklewis16@uchicago.edu
  - Note: Please include both TAs on all emails. However, students are strongly
    encouraged to post questions on the discussion page of the class GitHub
    repository here.

- **TA Session/TA Office Hours:** Fridays from 12-1 pm CT on Zoom. See the Zoom link on the Canvas calendar.

- **Website:** Canvas will be used for grades and for publishing Zoom links
  only. Homework and notes will be posted on the course GitHub repo:
  https://github.com/finm-32900/finm-32900-data-science. Questions and other
  class-related discussions should be posted here as well.
- **Textbook:** The text for the course will be published incrementally here:
  https://finm-32900.github.io/

**NOTE:** Due to the holiday on January 20, a makeup class will be scheduled. This makeup class will be held on Friday, January 24 during the TA office hours. I will use the same Zoom link as the TA office hours, which you can find on the Canvas calendar.


### Assignments

- Assignments must be submitted via GitHub before 6 pm on Fridays. Each
  assignment will be distributed on a Monday, and will be due the on the Friday
  of the following week (11 days later).
- Assignments are automatically graded via the autograder on GitHub Classroom
  and solutions will be released shortly after. This means that the due date is
  strict. Late assignments will not be accepted.
- Each student is to individually submit their assignment (unless otherwise
  specified). Students are encouraged to work in groups, but students are not
  allowed to copy each other's code. Each student must write their own solutions
  individually.
- After assignments are graded, solutions will be posted in separate GitHub
  repos, found here: https://github.com/finm-32900

### Final Project

In lieu of a final exam, students will be organized into groups of 2 (pairs) and
will each complete a course project. Each group will present their completed
project to the instructor at the end of the course. These presentations will be
scheduled individually. 

## Assessment

Grades will be based on coding assignments (70%), a final group project (25%),
and participation (5%). 

- Assignments will be submitted individually and will be graded using GitHub’s
  automated testing tools. 
- The final project will be completed in groups. Students will choose the
  project from among a few options provided at the beginning of the quarter. The
  project will be graded not only on how well it accomplishes the assigned data
  cleaning and analysis task, but will be primarily graded on whether (1) the
  steps to reproduce it are fully automated and well documented, (2) the code is
  written in a clean and reusable fashion, and (3) the results are presented
  clearly and presented in a way that convinces the reader that the results are
  correct. A more specific rubric will be provided in class.
- The participation grade will depend on the positive impacts that a student has
  on the class. These include participating in in-class discussions and/or
  answering questions on the class GitHub page (or on Canvas). Students are in
  no way penalized for giving wrong answers in these in-class discussions nor is
  there any penalty for asking for help—asking for help is often the best way to
  learn!


## Schedule

The schedule will follow the ordering of the chapters listed in the GitHub book
found here: https://finm-32900.github.io/. Each week is it's own chapter and the
agenda is listed in the first sub-section of the chapter.

### HW Due Dates

- [HW 0: Ungraded. Due ASAP](HW0.md)
- [HW 1: Due Friday, Jan  at 6 pm](HW1.md)
- [HW 2: Due Friday, Jan  at 31 pm](HW2.md)
- [HW 3: Due Tuesday, Feb 11, at 11:59 pm](HW3.md)
- [HW 4: Due Tuesday, Feb 25, at 11:59 pm](HW4.md)
- HW 5: TBD
- HW 6: TBD

## References

I will provide the lecture notes that we will use in class here:
https://finm-32900.github.io/. As a prerequisite, you should have some prior
familiarity with Python and the PyData stack (e.g., Numpy, Scipy, Pandas,
Matplotlib). The following references may serve as useful refreshers:

- [Python for Data Analysis, 3rd Edition](https://wesmckinney.com/book/), by Wes
  McKinney
- [Python Data Science
  Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/), by Jake
  VanderPlas
- [Python Programming for Economics and
  Finance](https://python-programming.quantecon.org/intro.html), by Thomas J.
  Sargent and John Stachurski

A significant portion of this course is inspired by ["The Missing Semester of
Your CS Education"](https://missing.csail.mit.edu/), a short course taught in
the Computer Science department at MIT. I'll rely on the material shown there
for portions of this course.


## Software to be used in class

Lectures will feature live programming exercises in class, so students should
have a WiFi-enabled laptop to bring to class.

Before the first class, please make sure to install the required software and
sign up for the required services. Students will need to install the following
software on their laptop. Each of these pieces of software are free:
 - [Anaconda distribution of Python (Individual
   Edition)](https://www.anaconda.com/download)
 - [Visual Studio Code](https://code.visualstudio.com/) (NOT Visual Studio.
   Visual Studio Code is different from Visual Studio)
 - [Git](https://git-scm.com/)
 - [GitKraken](https://www.gitkraken.com/) You will need to use GitKraken Client
   Pro, which is available for [free for
   students.](https://www.gitkraken.com/github-student-developer-pack)
 - [TeX Live](https://tug.org/texlive/)
 - [PuTTY](https://www.putty.org/)
 - [WinSCP](https://winscp.net/eng/download.php) For those using a Mac, you may
   need to find a software alternatives for WinSCP.

Students should also sign up for an account with the following websites. We will
use free versions of each of these services:
 - [GitHub](https://github.com/)
 - [IPUMS CPS](https://cps.ipums.org/cps/)
 - [Wharton Research Data Services (WRDS)](https://wrds-www.wharton.upenn.edu/)
   Apply for access through the University of Chicago, using the registration
   form [here.](https://wrds-www.wharton.upenn.edu/register/) For any issues
   that may arise, please contact the WRDS representative for UChicago's
   Mathematics department, John Zekos, zekos@math.uchicago.edu. 


## Quick Start

To quickest way to run code in this repo is to use the following steps. First, you must have the `conda`  
package manager installed (e.g., via Anaconda). However, I recommend using `mamba`, via [miniforge]
(https://github.com/conda-forge/miniforge) as it is faster and more lightweight than `conda`. Second, you 
must have TexLive (or another LaTeX distribution) installed on your computer and available in your path.
You can do this by downloading and 
installing it from here ([windows](https://tug.org/texlive/windows.html#install) 
and [mac](https://tug.org/mactex/mactex-download.html) installers).
Having done these things, open a terminal and navigate to the root directory of the project and create a 
conda environment using the following command:
```
conda create -n finm python=3.12
conda activate finm
```
and then install the dependencies with pip
```
pip install -r requirements.txt
```
Finally, you can then run 
```
doit
```
And that's it! The landing page of the textbook website will be available at `./_build/html/index.html`.

