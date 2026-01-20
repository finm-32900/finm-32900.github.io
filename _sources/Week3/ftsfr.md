# Financial Time Series Forecasting Repository (FTSFR)

The Financial Time Series Forecasting Repository (FTSFR) is an open-source benchmark designed to enable standardized, "apples-to-apples" comparisons of time series forecasting methods on financial data. The project addresses a critical gap in quantitative finance research: until now, no comprehensive forecasting benchmark existed specifically for financial markets.

**Resources:**
- GitHub Repository: [https://github.com/jmbejara/ftsfr](https://github.com/jmbejara/ftsfr)
- Documentation: [https://jeremybejarano.com/ftsfr/](https://jeremybejarano.com/ftsfr/)
- Simplified, separated repositories: https://github.com/ftsfr

## Why This Project Matters

### The Problem with Current Research

The time-series forecasting community increasingly recognizes the need for standardized evaluation frameworks. The absence of standardized benchmark datasets has meant that most studies evaluate their methods on limited, arbitrarily selected time series, making meaningful comparisons across methods virtually impossible. This lack of standardization has resulted in poor quality evaluations and irreproducible comparisons across forecasting studies.

While several benchmark repositories have emerged (such as the Monash Time Series Forecasting Repository), they remain limited in their coverage of financial markets. The FRED-MD database provides macroeconomic series but focuses on real economic indicators rather than financial market data. Other benchmarks like UCR and UEA archives do not include coverage of time series from the financial domain at all.

### Why Finance-Specific Benchmarks Matter

According to the "No Free Lunch" Theorem, there is no single forecasting method that performs best for all time series. To improve financial forecasting, we need to evaluate methods on datasets from the financial domain that reflect how data commonly appears in the relevant finance literature. This means using:
- The same data sources as canonical papers
- The same domain-specific cleaning and normalization procedures established in the literature

### Addressing the Replication Crisis

Finance faces an active debate about a potential "replication crisis." Studies find that predictors' average strength is only 54% of the original strength outside the original sample, with 32% becoming insignificant. While much of this involves data snooping, some involves coding bugs and lack of standardization. Standardized, open-source data infrastructure helps prevent simple errors from invalidating years of research.

## What Datasets Are Included

The repository provides **25 datasets** organized into three main categories:

### Returns Data (11 datasets)
Asset return series spanning multiple asset classes:
- **Equities**: CRSP stock returns, Fama-French 25 portfolios (size and book-to-market)
- **Fixed Income**: Treasury bonds and portfolios, corporate bonds and portfolios
- **Credit**: CDS contracts and portfolios
- **Other**: Commodity futures, foreign exchange, SPX options portfolios

### Basis Spread Data (5 datasets)
Arbitrage basis spreads that serve as critical early warning indicators of stress in the financial system:
- CDS-bond basis
- Covered interest parity (CIP) deviations
- TIPS-Treasury spreads
- Treasury spot-futures basis
- Treasury-swap spreads

### Other Financial Data (9 datasets)
Specialized datasets critical for financial stability monitoring:
- Bank and bank holding company (BHC) cash liquidity and leverage from Call Reports
- HKM intermediary risk factors (daily and monthly)
- Treasury yield curves (Nelson-Siegel-Svensson zero-coupon yields)

## Why the Codebase is Useful

### A Real-World Example of Task Runner Automation

The FTSFR codebase demonstrates exactly the kind of complex, multi-stage data science workflow that task runners like PyDoit are designed to manage. The project uses PyDoit to automate:

1. **Data Collection**: Pulling data from multiple sources (WRDS, Bloomberg, FRED, OptionMetrics)
2. **Data Cleaning**: Applying canonical cleaning procedures from seminal finance papers
3. **Data Transformation**: Converting raw data into analysis-ready formats
4. **Validation**: Replicating key tables and figures from original papers to verify correctness
5. **Forecasting**: Running baseline forecasting models across all datasets

### Reproducible Research Infrastructure

The repository provides:
- **Automated ETL pipeline** that streamlines data retrieval from multiple sources
- **Validated implementations** of canonical data cleaning procedures from seminal papers
- **Virtual environments** ensuring perfect reproducibility across different computing environments
- **Open-source scripts** that automate the download, cleaning, and assembly of datasets

### Managing Complex Dependencies

Financial data requires specialized treatment reflecting market microstructure, regulatory requirements, and established academic conventions. The task runner manages dependencies between:
- Raw data downloads
- Cleaning scripts specific to each asset class
- Portfolio construction
- Validation against published results
- Forecasting experiments

This is precisely the kind of complex dependency management that makes task runners essential for research workflows.

## Key Findings from Baseline Forecasting

The repository includes baseline forecasting results using 12 methods ranging from classical statistical models (ARIMA, ETS, Theta) to modern deep learning architectures (Transformer variants, N-BEATS, TimesFM). Key findings include:

- **Model effectiveness varies by asset class**: The answer to "which model works best?" depends on the task
- **Returns remain difficult to forecast**: Even the best models achieve out-of-sample R-squared values near zero for asset returns, consistent with decades of empirical finance
- **ML-based global models show gains for non-return series**: Machine learning approaches yield meaningful accuracy improvements for basis spreads, liquidity metrics, and other supervisory indicators where classical baselines fall short

## Connection to Course Material

The FTSFR project exemplifies why task runners matter for data science research:

1. **Workflow Management**: The `dodo.py` file documents the entire pipeline from raw data to forecasting results
2. **Reproducibility**: Anyone with access to the data sources can reproduce the exact datasets and results
3. **Data Integrity**: Changes to cleaning procedures automatically trigger re-runs of dependent tasks
4. **Collaboration**: The standardized workflow enables researchers worldwide to contribute and validate results

When you examine the FTSFR codebase, pay attention to how the `dodo.py` file structures the dependencies between data collection, cleaning, and analysis tasks. This is exactly the pattern we discussed in the task runners section of this course.


```{admonition} Discussion
:class: tip 
Let's open up the FTSFR repository and take a look at the structure of the `dodo.py` file. Then, let's open up a simpler version of one of it's modules. For example, let's open up 
```
