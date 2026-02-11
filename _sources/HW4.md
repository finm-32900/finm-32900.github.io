# Homework 4

```{toctree}
:maxdepth: 1
notebooks/_01_CRSP_treasury_overview_ipynb.ipynb
notebooks/_02_replicate_GSW2005_ipynb.ipynb
```

- **Due Date:** Friday, Feb 27 at 5:00 pm CT.
- **Link to Assignment:** https://classroom.github.com/a/a8Was0cz


## Learning Outcomes

 - Estimate the U.S. Treasury yield curve using the Nelson-Siegel-Svensson model following Gurkaynak, Sack and Wright (2006)
 - Use the `finm` package to implement yield curve functions (spot rates, discount factors, cashflow construction, and model fitting)
 - Build and verify a data pipeline using `doit`
 - Learn to use GitHub to scan for secrets and revise Git commit history

## Assignment


Please refer to the HW repo README for full details. The assignment consists of the following tasks:

 - **Task 1: GSW Yield Curve Module (2 pts)** — Replace `TODO` placeholders in `src/gsw2006_yield_curve.py` with imports from the [`finm`](https://jeremybejarano.com/finm/) package.
 - **Task 2: Data Pipeline (3 pts)** — Ensure the full data pipeline runs successfully via `doit`.
 - **Task 3: Federal Reserve Yield Curve Data (1 pt)** — Implement `task_pull_fed_yield_curve_data` in `dodo.py`.
 - **Task 4: Notebooks (1 pt)** — Ensure the Jupyter notebooks execute successfully.
 - **Task 5: GitHub Skills (2 pts)** — Complete the [Change Commit History](https://github.com/skills/change-commit-history) and [Introduction to Secret Scanning](https://github.com/skills/introduction-to-secret-scanning) tutorials.
 - **Task 6: Market Brief Self-Attestation (2 pts)** — Affirm that you have compiled your market brief and added custom metrics.

**Total: 11 points**

[Example Market Brief](./assets/market_brief.pdf)


