# Homework 3

## Part 0 (not graded)

Please watch the following videos to better familiarize yourself with CRSP and Compustat in WRDS.

 - Watch the following videos about Compustat. The slides to accompany the videos are available [here](https://wrds-www.wharton.upenn.edu/documents/1374/intro_comp_access_link.pptx).
   - [Introduction to Compustat | Part 1](https://vimeo.com/417303405)
   - [Introduction to Compustat | Part 2](https://vimeo.com/417302901)
   - [Merging CRSP and Compustat Data](https://vimeo.com/447503392)

 - You may also find the following videos helpful:
   - [Fama-French SMB and HML | SAS Replication](https://vimeo.com/447603278)
   - [Fama-French SMB and HML | 1. Book-Equity](https://vimeo.com/447631819)
   - [Fama-French SMB and HML | 2. CRSP Stock Data](https://vimeo.com/447635241)
   - [Fama-French SMB and HML | 3. CRSP](https://vimeo.com/447867614)
   - [Fama-French SMB and HML | 4. Merge CRSP and Compustat. B/M Ratio](https://vimeo.com/447871296)
   - [Fama-French SMB and HML | 5. Calculating Fama-French Factors](https://vimeo.com/447876324)

## Part 1 (graded)

Again, we continue on our journey mastering the many features of Github. Please complete next 2 tutorials from the [GitHub Skills](https://skills.github.com/) page. Please make sure to use **public repositories** for this in your own GitHub user account. You will provide a link later to demonstrate that it was completed.

- [Release Based workflow](https://github.com/skills/release-based-workflow)
- [Connect the dots](https://github.com/skills/connect-the-dots)

## Part 2 (graded)

In this second part, you'll complete an exercise in which we create a value-weighted
index of market returns and an exercise related to the seminal paper [Fama and French (1993)](https://www.jufinance.com/mag/fin534_16/Common_risk_factors_Fama_French_JFE1993.pdf). These will comprise parts 2A and 2B.
You can find guides here:

 - [HW Guide: Replicate Fama-French 1993](./../../output/04_Fama_French_1993.ipynb)

The data will be downloaded using the WRDS Python package. The code for this is included in the HW. This data download step will be fully automated. 

The link to accept the HW is here: https://classroom.github.com/a/TF5xbCE8


## Part 3 (graded)

Note that within the HW repository above, you will find a file called `github_pages_tearsheet.py`. In this module, you will indicate whether or not you ahve created a tearsheet based off of a trading strategy of your choice. You must publish this tearsheet to the internet using GitHub pages, as we did in class.
That is, you will create a Jupyter notebook that reports some statistics about your trading strategy. Then, the `dodo.py` file will convert this notebook to HTML and publish it to the internet.

This is an example of what yours might look like:

 - Homepage: https://finm-32900.github.io/hw3--solutions/
 - Tearsheet: https://finm-32900.github.io/hw3--solutions/tearsheet_investment_profitability.html


**Citations:**

 - Eugene, Fama, and Kenneth French. "The cross-section of expected stock returns." Journal of Finance 47, no. 2 (1992): 427-465.
 - Fama, Eugene F., and Kenneth R. French. "Common risk factors in the returns on stocks and bonds." Journal of financial economics 33, no. 1 (1993): 3-56.

## Reminder

Do not make any changes to the unit test files. If an edit is made, you will be required to edit the history of your commits to remove any trace of the edits to these files.