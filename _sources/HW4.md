# Homework 4

- **Due Date:** TBD (will be announced on Canvas)
- **Link to Assignment:** TBD (the GitHub Classroom link will be posted on Canvas)

```{note}
The yield-curve estimation content that previously formed Homework 4 has moved to
**[Homework 3](./HW3.md)**. Homework 4 is now a short options case study; full
instructions arrive with the GitHub Classroom link.
```

## Overview

Homework 4 is a deliberately minimal introduction to working with options data.
The spine of the assignment is [finm-32900/case_study_options](https://github.com/finm-32900/case_study_options),
a pipeline built from the same ChartBook template as your other course repos. The
pipeline pulls option-chain data from WRDS OptionMetrics (a year-by-year SQL query
against WRDS, in `src/pull_options_data.py`) and works through two hedging case
studies as notebook reports:

- **Corporate hedging**: designing a hedging program for a firm exposed to oil
  prices, using Brent crude futures and options (the futures strips and
  option-chain snapshots ship with the repo in `data_manual/`).
- **SPX hedging**: hedging an equity portfolio with S&P 500 index options.

As in HW 3, the pipeline is orchestrated with `doit` and ends by building a
ChartBook site from the registered dataframes and executed notebooks.

We launch the assignment together in Week 7 and review the two case-study
notebooks in class:

- [Corporate Hedging](notebooks/_01_corporate_hedging_ipynb.ipynb)
- [SPX Hedging](notebooks/_02_spx_hedging_ipynb.ipynb)
