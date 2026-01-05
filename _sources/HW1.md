# Homework 1

```{toctree}
:maxdepth: 1
notebooks/_02_CRSP_market_index.ipynb
notebooks/_03_SP500_constituents_and_index.ipynb
```

**Due Date:** Friday, Jan 16 at 11:59 pm.
**Link to Assignment:** https://classroom.github.com/a/NTIt0NQ1

## Learning Outcomes

- **Do in class:** Introduction to GitHub and GitHub Education
    - Make sure students get added to GitHub Education. Start with Example HW
    - Make sure students know how to clone HW repository
    - Learn basic usage of PyTest to test HW solutions
    - Learn how to submit HW via GitHub Education
- **Do on own:** Explore the WRDS CRSP data

## Assignment

### Part 0 (not graded)

Please watch the following videos to better familiarize yourself with CRSP and Compustat in WRDS.

 - Watch the following videos about WRDS and CRSP
   - [WRDS Web Queries](https://player.vimeo.com/video/1019787855?h=83ee06d532) While we will be automating the query process using the WRDS Python package [`wrds`](https://pypi.org/project/wrds/), using the web query system is a good way for initial exploration of the data.
   - [CRSP Coverage](https://vimeo.com/417302309)
   - [CRSP - Useful Variale](https://wrds-www.wharton.upenn.edu/pages/grid-items/crsp-useful-variables/). This video goes over some points we made in class as well and is helpful for cleaning the CRSP data (e.g., negative prices).
   - [CRSP Stock Database Coverage](https://wrds-www.wharton.upenn.edu/pages/grid-items/crsp-stock-database-structure/) Useful for merging stock files and event files in CRSP via SQL. This is useful, for example, to incorporate delisting returns.


### Part 1 

In order to start mastering the many features of Github, please complete the following tutorials from the [GitHub Skills](https://skills.github.com/) page. Please make sure to use **public repositories** for this in your own GitHub user account. You will provide a link later to demonstrate that it was completed.

 - [Introduction to GitHub](https://github.com/skills/introduction-to-github)
 - [Communicate using Markdown](https://github.com/skills/communicate-using-markdown)
   - This will give you some ideas on how to more effectively communicate on the course [discussion board](https://github.com/orgs/finm-32900/discussions).
 - [GitHub Pages](https://github.com/skills/github-pages)
   - Later in this course, we will use GitHub Pages to host a website. The textbook for this course is hosted on GitHub Pages.
 
These tutorials are not graded, but please make sure to complete them before the next class.

### Part 2 (graded)

This will include a task of replicating the CRSP market index example from the lecture as well as a task of replicating the S&P 500 index from its constituent companies. 

To complete this assignment, please read the two HW guides here:

- [HW Guide Part A: CRSP Market Returns Indices](notebooks/_02_CRSP_market_index.ipynb)
- [HW Guide Part B: Reconstructing the S&P 500 Index](notebooks/_03_SP500_constituents_and_index.ipynb)

Recall that the way to go about this assignment is to run `pytest` and then determine how to write the code to pass the tests. As a tip, make sure to run the `doit` command before running `pytest`. This will ensure that all the data is pulled before running the tests.

Note, in order to complete this assignment, you will need to have the `wrds` package installed and you will need to have created a `.pgpass` file so that you can automatically authenticate to WRDS to pull the required data. Please refer to the textbook page [Example: Connecting to the WRDS Platform With Python](notebooks/_01_wrds_python_package.ipynb) for more information, specifically the section "Creating a .pgpass file".



## Additional Notes about the HW


### Why are we doing it this way? 

The point of structuring the assignment this way is to give you experience with unit testing, CI/CD, and the concept of test-driven development. These are concepts that you should learn to level-up your software development skills. These are real-world development concepts and getting experience with them should move you beyond the over-simplified approach that you might find in a typical university problem set.

We discussed unit tests and test-driven development in class a little. If you'd like more in-depth information, please watch these YouTube videos:

["Software Testing Explained in 100 Seconds"](https://www.youtube.com/watch?v=u6QfIXgjwGQ) (This short video is written from the perspective of a web developer, but the same concepts apply to us.)

<iframe width="560" height="315" src="https://www.youtube.com/embed/u6QfIXgjwGQ?si=-UGtBRl9aVCxV_N8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

["Test-Driven Development In Python // The Power of Red-Green-Refactor"](https://www.youtube.com/watch?v=B1j6k2j2eJg) (This video discussing unit testing with Python and PyTest.)

<iframe width="560" height="315" src="https://www.youtube.com/embed/B1j6k2j2eJg?si=ScZi46xUE4TN58N4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### How can I check if my tests are passing?

From the command-line, in the base directory of the project, run `pytest`

In `test_dodo.py` file, you'll also notice that one of the tests asks you to edit `dodo.py` file so that the command `doit` will run all of the code of the project. To execute the `dodo.py` file, make sure `PyDoit` is installed and then simply run `doit` from the command line in the base directory of the project.


### More information about Git and GitHub

Also, if you're looking for more instruction about how to use Git, here are two videos that I might recommend:

- [What is Version Control? (Learn Git Video Course)](https://www.youtube.com/watch?v=M-O8ZNW9icQ)
- [Using Git with Visual Studio Code (Official Beginner Tutorial)](https://www.youtube.com/watch?v=i_23KUAEtUM)
