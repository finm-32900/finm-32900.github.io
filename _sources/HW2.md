# Homework 2


```{toctree}
:maxdepth: 1
notebooks/_04_Fama_French_1993_ipynb.ipynb
```

- **Due Date:** Friday, Jan 23 at 11:59 pm.
- **Link to Assignment:** https://classroom.github.com/a/wkZyHjl9


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

In Part 1, you will replicate portfolio analysis from the seminal paper [Fama and French (1993)](https://www.jufinance.com/mag/fin534_16/Common_risk_factors_Fama_French_JFE1993.pdf). A guide to this replication is available here:

 - [HW Guide: Replicate Fama-French 1993](notebooks/_04_Fama_French_1993_ipynb.ipynb)

The data will be downloaded using the WRDS Python package. The code for this is included in the HW, and the data download step is fully automated. Your job is to fill in the missing code to complete the replication.

The actual Fama-French factors and sorted portfolios are downloaded from the [Kenneth French data library](https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html). The HW code is already configured to automatically download these reference data (the precomputed factors and sorted portfolios from the Ken French data library). However, you will also download the raw underlying data from CRSP and Compustat via WRDS and construct the Fama-French factors and sorted portfolios from the raw data yourself. The unit tests will check that your code produces time series for the factors and portfolio returns that statistically match the reference data from the Kenneth French data library.


## Part 2 (graded)

In Part 1, you constructed the Fama-French size and book-to-market sorted portfolios. These 6 portfolios (Small/Low, Small/Medium, Small/High, Big/Low, Big/Medium, Big/High) represent different investment styles based on firm size and value characteristics.

For Part 2, you will:
1. Pick a trading strategy to analyze (we recommend one of the 6 size/BM portfolios from Part 1)
2. Use the [`quantstats_lumi`](https://github.com/Lumiwealth/quantstats_lumi) package to generate a tearsheet
3. Publish the tearsheet to the internet using GitHub Pages

**Note:** The Fama-French factors (SMB, HML, Mkt-RF) are long-short constructs used for analysis, not directly tradeable as-is. The 6 size/BM portfolios, however, represent long-only portfolios of actual stocks.

For detailed instructions on what tearsheets are and how to publish to GitHub Pages, see: [GitHub Pages and Tearsheets](Week2/github_pages_preview.md)

### Autograder Requirement

To receive credit for this part, you must update `src/github_pages_tearsheet.py` in your HW repository:

```python
# Set this to True once you've published your tearsheet
I_HAVE_CREATED_A_TEAR_SHEET_ON_GITHUB_PAGES = True

# Provide the URL to your published tearsheet
URL_TO_MY_TEAR_SHEET = "https://finm-32900.github.io/<your-repo-name>/"
```

The unit test `test_github_pages_tearsheet.py` will verify that both values are set correctly.

### Example

See a completed example here: https://finm-32900.github.io/hw2--solutions/


**Citations:**

 - Eugene, Fama, and Kenneth French. "The cross-section of expected stock returns." Journal of Finance 47, no. 2 (1992): 427-465.
 - Fama, Eugene F., and Kenneth R. French. "Common risk factors in the returns on stocks and bonds." Journal of financial economics 33, no. 1 (1993): 3-56.

## Reminder

Do not make any changes to the unit test files. If an edit is made, you will be required to edit the history of your commits to remove any trace of the edits to these files.
