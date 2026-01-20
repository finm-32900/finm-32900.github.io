# List of Potential Final Projects

The project that you are assigned will come from one of several categories below. Each of these projects involve replicated a well known finance paper.
If you can't access the papers below, you can find a link to them here: https://drive.google.com/drive/folders/1uaFsV1nn9MeO_XIRcolBnKcbkHKCEHu8?usp=drive_link

## Financial Forecasting

### 1.	[Market Expectations in the Cross-Section of Present Values](https://doi.org/10.1111/jofi.12060)

This paper demonstrates that returns and cash flows for the aggregate US stock market are highly predictable. It demonstrates this by constructing a univariate predictor from the cross section of stocks. See the abstract:

 > Returns and cash flow growth for the aggregate U.S. stock market are highly and robustly predictable. Using a single factor extracted from the cross-section of book-to market ratios, we find an out-of-sample return forecasting R2 of 13% at the annual frequency (0.9% monthly). We document similar out-of-sample predictability for returns on value, size, momentum, and industry portfolios. We present a model linking aggregate market expectations to disaggregated valuation ratios in a latent factor system. Spreads in value portfolios’ exposures to economic shocks are key to identifying predictability and are consistent with duration-based theories of the value premium.

Also, from their paper, 

 > “Our approach attacks a challenging problem in empirical asset pricing: how does one exploit a wealth of predictors in relatively short time series? If the predictors number near or more than the number of observations, the standard ordinary least squares (OLS) forecaster will be poorly behaved or nonexistent (see Huber (1973)). Our solution is to use partial least squares (PLS; Wold (1975)), which is a simple regression-based procedure designed to parsimoniously forecast a single time series using a large panel of predictors. We use it to construct a univariate forecaster for market returns (or dividend growth) that is a linear combination of assets’ valuation ratios.”

 - Task: Replicate Table 1
 - Data sources: CRSP and Compustat
 - Citation: KELLY, B. and PRUITT, S. (2013), Market Expectations in the Cross-Section of Present Values. THE JOURNAL OF FINANCE, 68: 1721-1756. https://doi.org/10.1111/jofi.12060

### 2. [Man vs. Machine Learning: The Term Structure of Earnings Expectations and Conditional Biases](https://ssrn.com/abstract=3625279)

This paper studies analysts’ earnings forecasts and shows that they are *conditionally biased* relative to a statistically optimal machine-learning benchmark. The authors use random forests to construct real-time forecasts of firm earnings using public information (firm fundamentals, macro data, and analyst forecasts), and define **earnings forecast bias** as the difference between analysts’ forecasts and the ML benchmark. Stocks with overly optimistic earnings expectations earn significantly lower future returns, and firms with higher optimism issue more equity.

From the abstract:

> “We introduce a real-time measure of conditional biases to firms’ earnings forecasts. The measure is defined as the difference between analysts’ expectations and a statistically optimal unbiased machine-learning benchmark. Analysts’ conditional expectations are, on average, biased upwards, a bias that increases in the forecast horizon. These biases are associated with negative cross-sectional return predictability, and the short legs of many anomalies contain firms with excessively optimistic earnings forecasts.”

This project gives students hands-on experience with machine learning for cash-flow forecasting, interpretability tools (partial dependence plots), and cross-sectional asset pricing tests. You might only consider this project if you have some experience with machine learning.

- Task: Replicate Table 2 (forecast accuracy and bias summary) and Figure 1 or Figure 3 (partial dependence plots showing nonlinearities) (Hyperparameters can be fixed; full cross-validation is not required.)
- Data sources: I/B/E/S (analyst earnings forecasts and actual EPS), CRSP (prices, returns, split adjustments), WRDS Financial Ratios Suite (firm fundamentals), FRED macro data (can substitute for real-time vintages)
- Citation: van Binsbergen, Jules H., Xiao Han, and Alejandro Lopez-Lira. *Man vs. Machine Learning: The Term Structure of Earnings Expectations and Conditional Biases*. Review of Financial Studies (forthcoming). Available at SSRN: [https://ssrn.com/abstract=3625279](https://ssrn.com/abstract=3625279)


### 3. [Lewellen (2015), Critical Finance Review. “The Cross-section of Expected Stock Returns”](https://faculty.tuck.dartmouth.edu/images/uploads/faculty/jonathan-lewellen/ExpectedStockReturns.pdf)

This paper will teach you how to combine many firm characteristics into real-time forecasts of a stock’s expected returns. See the abstract: "This paper studies the cross-sectional properties of return forecasts derived from Fama-MacBeth regressions. These forecasts mimic how an investor could, in real time, combine many firm characteristics to obtain a composite estimate of a stock’s expected return. Empirically, the forecasts vary substantially across stocks and have strong predictive power for actual returns. For example, using ten-year rolling estimates of Fama-MacBeth slopes and a cross-sectional model with 15 firm characteristics (all based on low-frequency data), the expected-return estimates have a cross-sectional standard deviation of 0.87% monthly and a predictive slope for future monthly returns of 0.74, with a standard error of 0.07."

  - Task: Replicate Table 1, Table 2, and Figure 1
  - Data sources: CRSP and Compustat
  - Citation: Lewellen, Jonathan W., The Cross Section of Expected Stock Returns (August 22, 2014). Forthcoming in Critical Finance Review, Tuck School of Business Working Paper No. 2511246, Available at SSRN: https://ssrn.com/abstract=2511246 or http://dx.doi.org/10.2139/ssrn.2511246
  - Notes: I will provide some starter code that partially constructs some of these tables. In this project, you'll have to complete the code.


## AI and Quantitative Finance

### 4. [Can ChatGPT Forecast Stock Price Movements? Return Predictability and Large Language Models](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4412788)

This paper demonstrates the capability of large language models (LLMs) like ChatGPT to predict stock market reactions from news headlines. See the abstract:

> We document the capability of large language models (LLMs) like ChatGPT to predict stock market reactions from news headlines without direct financial training. Using postknowledge-cutoff headlines, GPT-4 captures initial market responses, achieving approximately 90% portfolio-day hit rates for the non-tradable initial reaction. GPT-4 scores also significantly predict the subsequent drift, especially for small stocks and negative news. Forecasting ability generally increases with model size, suggesting that financial reasoning is an emerging capacity of complex LLMs. Strategy returns decline as LLM adoption rises, consistent with improved price efficiency. To rationalize these findings, we develop a theoretical model that incorporates LLM technology, information-processing capacity constraints, underreaction, and limits to arbitrage.

Also, from their paper,

> "Our key finding is that GPT-4 demonstrates a strong ability to predict the immediate market reaction to news headlines, achieving daily portfolio hit rates of approximately 90% for correctly identifying the direction of the initial price response. This result is notable for two reasons. First, it is not obvious that a general-purpose language model trained without explicit financial supervision should excel at this task. The fact that it does suggests that sophisticated financial reasoning—understanding not just whether news is positive or negative, but also how markets will interpret it—emerges naturally from the model’s general language training."

- Task: Replicate Table 1 (Hit Rates) and Table 5 (Long-Short Strategy Returns)
- Data sources: CRSP, RavenPack (or similar news data), and ChatGPT API
- Citation: Lopez-Lira, Alejandro and Tang, Yuehua, Can ChatGPT Forecast Stock Price Movements? Return Predictability and Large Language Models (2023). Available at SSRN: https://ssrn.com/abstract=4412788

## Institutional Monitoring

### 5. [Intermediary Asset Pricing: New Evidence from Many Asset Classes](https://zhiguohe.net/wp-content/uploads/2023/12/jfepublishedversion.pdf)

This project will give you experience in analyzing the balance sheet fundamentals of large broker-dealers, in this case the full set of primary dealers in the US, and how the financial condition of these primary dealers affect the US stock market as a whole.

 - Task: Replicate Table 2, and Table 3 (Panel A and Panel B)
 - Data used: CRSP, Compustat, Datastream
 - Some code and data is available online [here](https://zhiguohe.net/publications/research/) and [here](https://zhiguohe.net/data-and-empirical-patterns/intermediary-capital-ratio-and-risk-factor/).
 - Citation: He, Zhiguo, Bryan Kelly, and Asaf Manela. "Intermediary asset pricing: New evidence from many asset classes." Journal of Financial Economics 126, no. 1 (2017): 1-35.
 - Note: I will provide some code that will help you get started.


### 6. [Monetary Tightening and US Bank Fragility in 2023](https://www.nber.org/papers/w31048)

This paper will teach you how to use bank call reports to construct measures of the financial condition of banks. This is especially useful if you have interest in specializing, for example, in specializing in equities covering the financial sector.

 - Task: Replicate Table 1, Table A1 and Figure A1 and update the numbers through 2025. To do this, you will have to scrape data from FFIEC's website.
 - Citation: Jiang et al (2023). Monetary Tightening and US Bank Fragility in 2023: Mark-to-Market Losses and Uninsured Depositor Runs?. No. w31048. National Bureau of Economic Research, 2023. https://www.nber.org/papers/w31048
 - Data sources: Bank Call Reports. See https://wrds-www.wharton.upenn.edu/pages/get-data/bank-regulatory/
 - Notes: I will actually provide you with code to replicate the tables and figures from the paper, using data from WRDS. The problem is that the data from WRDS is only updated with a lag of nearly a year and a half. So, in order to get more "real-time" data, you will have to scrape data from FFIEC's website. Therefore, this exercise will give you experience with web scraping and data cleaning in order to produce more of a real-time monitor.


### 7. **[A Demand System Approach to Asset Pricing (Working Paper)](https://ssrn.com/abstract=2537559)**

This project studies how institutional investors’ *portfolio demand* shapes asset prices. Rather than inferring demand indirectly from returns, the paper estimates a characteristics-based demand system using institutional holdings data (SEC Form 13F), explicitly imposing market clearing between institutions and households. A key idea is that investment mandates create persistent investment universes, which can be used as instruments to identify demand elasticities.

This project is focused on the descriptive and institutional foundations of the demand-system approach, not on estimating the full nonlinear GMM model.

Students will replicate:

* **Table 1**: Persistence of institutional investment universes (how stable holdings are over the past 11 quarters)
* **Table 2**: Summary statistics of 13F institutions (AUM, number of holdings, market share)
* **Table D1 (Appendix)**: Breakdown of institutional characteristics by institution type

These tables rely primarily on clean construction and aggregation of 13F holdings, and provide a concrete entry point into the broader research agenda on institutional demand, price pressure, and asset-pricing equilibrium.

Additional context and motivation for this research agenda can be found in Ralph Koijen’s lecture here: [https://www.youtube.com/watch?v=x2qxThATszM](https://www.youtube.com/watch?v=x2qxThATszM)

- Task: Replicate Table 1 (investment-universe persistence), Table 2 (institution-level summary statistics), and Appendix Table D1 (institution characteristics by type)
- Data sources: Thomson Reuters / Refinitiv 13F Institutional Holdings (WRDS), CRSP (prices, shares outstanding), Compustat (book equity and firm fundamentals, as needed for merges)
- Code and data: Author-provided replication code and documentation: [https://koijen.net/code-and-data.html](https://koijen.net/code-and-data.html) I will also provide starter code that handles most of the WRDS data extraction and merging.
- Citation: Koijen, Ralph S. J., and Motohiro Yogo. *A Demand System Approach to Asset Pricing*. Working paper, SSRN: [https://ssrn.com/abstract=2537559](https://ssrn.com/abstract=2537559)


## Arbitrage Spreads

### 8. [Segmented Arbitrage: Treasury Spot-Futures](https://www.hbs.edu/ris/Publication%20Files/24-030_1506d32b-3190-4144-8c75-a2326b87f81e.pdf)

This project replicates the Treasury spot-futures spread from the paper "Segmented Arbitrage" by Emil Siriwardane, Adi Sunderam, and Jonathan Wallen. The paper examines various arbitrage trades and observes that the price dynamics of these trades challenge asset pricing models that have been used in the past to explain deviations from no-arbitrage.

The Treasury spot-futures arbitrage trade involves exploiting the price discrepancy between Treasury futures contracts and the underlying Treasury securities in the cash (spot) market. By simultaneously buying (or selling) the mispriced asset and selling (or buying) its equivalent in the other market, arbitrageurs aim to lock in a risk-free profit, accounting for carry costs, accrued interest, and delivery options.

From the [internet appendix](https://www.emilsiriwardane.com/s/Appendix.pdf):

> "The Treasury spot-futures basis is measured as the difference between the market price of a Treasury futures contract and its theoretical price implied by the cost of carry. The theoretical price reflects the cost of financing a position in the underlying Treasury security until the futures delivery date, including accrued interest and any coupon payments received."

 - Task: Replicate the Treasury spot-futures spread construction and reproduce the relevant figures from the paper. I will actually provide you with code to replicate the tables and figures from the paper. The figures are created by pulling the "implied repo rate" from Bloomberg. I will provide you with code that pulls this. However, there is a bug in the way that Bloomberg calculates the implied repo rate. Therefore, your task will be to fix the bug and replicate the figures up to the present with the corrected implied repo rate.
 - As a note, the bug in the Bloomberg terminal doesn't really affect the figures in the paper, since the paper only shows the series up to 2020. The bug only affects the time period after 2020. The bug is that the Bloomberg terminal assumes that deliver of the Treasury into the futures contract is always done at the beginning of the delivery period. However, because of major changes to interest rates after 2020, this assumption was no longer a good approximation.
 - Data sources: Bloomberg (for Treasury futures and cash bond prices)
 - Code and data: One of the authors, [Emil Siriwardane](https://www.emilsiriwardane.com/), makes code and data available online: https://github.com/esiriwardane/arbitrage-spreads-public
 - Additional resources: https://github.com/jmbejara/arb_spreads and https://jeremybejarano.com/arb_spreads/
 - Citation: Siriwardane, Emil N., Adi Sunderam, and Jonathan L. Wallen. "Segmented Arbitrage." Harvard Business School Working Paper, No. 24-030, November 2023.
