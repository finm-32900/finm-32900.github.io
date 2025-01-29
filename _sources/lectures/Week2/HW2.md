# Homework 2

## Part 0 (not graded)

Please watch the following videos to better familiarize yourself with CRSP and Compustat in WRDS.

 - Watch the following videos about WRDS and CRSP
   - [WRDS Web Queries](https://player.vimeo.com/video/1019787855?h=83ee06d532) While we will be automating the query process using the WRDS Python package [`wrds`](https://pypi.org/project/wrds/), using the web query system is a good way for initial exploration of the data.
   - [CRSP Coverage](https://vimeo.com/417302309)
   - [CRSP - Useful Variale](https://wrds-www.wharton.upenn.edu/pages/grid-items/crsp-useful-variables/). This video goes over some points we made in class as well and is helpful for cleaning the CRSP data (e.g., negative prices).
   - [CRSP Stock Database Coverage](https://wrds-www.wharton.upenn.edu/pages/grid-items/crsp-stock-database-structure/) Useful for merging stock files and event files in CRSP via SQL. This is useful, for example, to incorporate delisting returns.

## Part 1 (graded)

In order to continue on our journey mastering the many features of Github, please complete next 2 tutorials from the [GitHub Skills](https://skills.github.com/) page. Please make sure to use **public repositories** for this in your own GitHub user account. You will provide a link later to demonstrate that it was completed.

- [Review pull requests](https://github.com/skills/review-pull-requests) You may want to seek out the help of a friend or teammate with this one.
- [Resolve merge conflicts](https://github.com/skills/resolve-merge-conflicts)

Also, if you're looking for more instruction about how to use Git, here are two videos that I might recommend:

- [What is Version Control? (Learn Git Video Course)](https://www.youtube.com/watch?v=M-O8ZNW9icQ)
- [Using Git with Visual Studio Code (Official Beginner Tutorial)](https://www.youtube.com/watch?v=i_23KUAEtUM)

## Part 2 (graded)

This will include a task of replicating the CRSP market index example from the lecture as well as a task of replicating the S&P 500 index from its constituent companies. The link to accept the assignment is here: https://classroom.github.com/a/KMvpqo_F

To complete this assignment, please read the two HW guides here:

- [HW Guide Part A: CRSP Market Returns Indices](../../output/_02_CRSP_market_index.ipynb)
- [HW Guide Part B: Reconstructing the S&P 500 Index](../../output/_03_SP500_constituents_and_index.ipynb)

Recall that the way to go about this assignment is to run `pytest` and then determine how to write the code to pass the tests. As a tip, make sure to run the `doit` command before running `pytest`. This will ensure that all the data is pulled before running the tests.

Note, in order to complete this assignment, you will need to have the `wrds` package installed and you will need to have created a `.pgpass` file so that you can automatically authenticate to WRDS to pull the required data. Please refer to the textbook page [Example: Connecting to the WRDS Platform With Python](../../output/_01_wrds_python_package.ipynb) for more information, specifically the section "Creating a .pgpass file".

