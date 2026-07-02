# List of Potential Final Projects

The project that you are assigned will come from one of several categories below. Each of these projects involves replicating a well-known finance paper.
If you can't access the papers below, you can find a link to them here: https://drive.google.com/drive/folders/1uaFsV1nn9MeO_XIRcolBnKcbkHKCEHu8?usp=drive_link

Not sure what a finished replication looks like? See the [Project Previews](project_previews.md) page, which walks through three of the papers below (#1, #2, and #4) with the actual figures and tables you would reproduce.

## Machine Learning and Return Prediction

### 1. [The Virtue of Complexity in Return Prediction](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3984925)

Conventional wisdom says market-return forecasting models should be small and simple. This paper proves the opposite: "simple models severely understate return predictability compared to 'complex' models in which the number of parameters exceeds the number of observations." The authors forecast the monthly excess return of the CRSP value-weighted index using random Fourier features built from the 15 Goyal–Welch predictors, and show that out-of-sample forecasting and market-timing performance *improves* as model complexity grows—even with as few as 12 training observations and up to 12,000 parameters.

The pipeline: build and volatility-standardize the Goyal–Welch predictors (1926–2020), generate random Fourier features, run recursive out-of-sample ridge regressions across a grid of model sizes and shrinkage values, and trace out the "virtue of complexity" curves for prediction accuracy and market-timing performance.

*This paper is featured on the [Project Previews](project_previews.md) page.*

- **Tasks**:
  - **Predictor summary statistics**: construct the 15 predictors, apply the paper's volatility standardization (Section V.A), and produce a summary-statistics table and time-series overview plot (this is the data-cleaning deliverable)
  - **Replicate Figure 7 (out-of-sample market timing performance, T = 12)**: out-of-sample R², coefficient norm, expected return, and volatility as functions of model complexity and ridge shrinkage
  - **Replicate Figure 8 (Sharpe ratio, alpha, information ratio, T = 12)**: the crux result—market-timing performance rising with complexity
  - **Replicate Figure 11 (variable importance)**: change in out-of-sample R² and Sharpe ratio from dropping each predictor one at a time
- **Data sources**: Amit Goyal's website (the updated Goyal–Welch predictor dataset, free and public); CRSP (value-weighted index returns, via WRDS)
- **Notes**:
  - The computational burden is the main challenge. When the feature count P far exceeds the training window T, solve the ridge regression in its dual (kernel) form, which only requires inverting a T × T matrix. You may use a coarser grid of P values and fewer random-feature repetitions than the paper's 1,000 (e.g., 50–100), which preserves the shape of the curves.
  - The paper is available on SSRN and published in the *Journal of Finance* (2024); use whichever version is convenient.
- **Citation**: Kelly, Bryan, Semyon Malamud, and Kangying Zhou. "The Virtue of Complexity in Return Prediction." The Journal of Finance 79, no. 1 (2024): 459–503. Available at SSRN: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3984925
- **Paper PDF**: [KellyMalamudZhou2024VirtueOfComplexity.pdf](project_papers/KellyMalamudZhou2024VirtueOfComplexity.pdf)

## Credit Cycles and Financial Crises

### 2. [Predictable Financial Crises](https://onlinelibrary.wiley.com/doi/abs/10.1111/jofi.13105)

Using a panel of 42 countries from 1950 to 2016, this paper shows that "crises are substantially predictable": when rapid credit growth coincides with rapid asset price growth—the "R-zone"—the probability of a financial crisis within three years rises to 40% or more. The predictability challenges the conventional view that crises arrive as unforecastable shocks and implies policymakers have time to act.

The project is a cross-country panel-data assembly exercise: merge the Baron–Verner–Xiong crisis chronology with credit growth for households and businesses (BIS Total Credit Statistics, IMF Global Debt Database) and real equity and house price growth (BIS, OECD, JST Macrohistory, IMF IFS), then compute crisis probabilities conditional on credit and price growth quantiles.

*This paper is featured on the [Project Previews](project_previews.md) page.*

- **Tasks**:
  - **Replicate Table 1 (summary statistics)**: crisis counts by country and decade compared across chronologies, plus summary statistics of credit growth and asset price growth (this and Figure 1 are the data-cleaning deliverables)
  - **Replicate Figure 1 (event history)**: the timeline of financial crises across countries in the sample
  - **Replicate Table 3 (crisis probabilities by price and debt growth quantiles)**: the R-zone result—crisis probabilities in the double-sort of credit growth against asset price growth, for the business and household sectors
  - **Replicate Table 4 (regression version)**: predictive regressions of crisis onset on the R-zone indicators, with the paper's standard-error treatment
  - **Replicate Figure 3 (fraction of countries in the R-zone)**: time series showing global credit-market overheating, peaking before 1929, 2008, and other crisis waves
- **Data sources** (all free and public): Baron–Verner–Xiong (2021) crisis chronology (posted online); BIS Total Credit Statistics and Residential Property Price database; IMF Global Debt Database and International Financial Statistics (share price indices); OECD Housing Prices; Jordà–Schularick–Taylor Macrohistory database; World Bank WDI (inflation)
- **Notes**:
  - The paper's primary equity-index source is Global Financial Data, which we do not have. Use the IMF IFS share price indices and the JST Macrohistory equity data instead—the paper itself uses these as supplementary sources, and coverage is adequate for nearly all country-years in the sample.
  - Use the working paper version (HBS Working Paper 20-130) for table and figure numbering.
- **Citation**: Greenwood, Robin, Samuel G. Hanson, Andrei Shleifer, and Jakob Ahm Sørensen. "Predictable Financial Crises." The Journal of Finance 77, no. 2 (2022): 863–921. https://onlinelibrary.wiley.com/doi/abs/10.1111/jofi.13105
- **Paper PDF**: [GreenwoodHansonShleiferSorensen2022PredictableFinancialCrises.pdf](project_papers/GreenwoodHansonShleiferSorensen2022PredictableFinancialCrises.pdf) (HBS working paper version)

### 3. [Credit-Market Sentiment and the Business Cycle](https://academic.oup.com/qje/article/132/3/1373/3787666)

Using U.S. data from 1929 to 2015, this paper shows that "elevated credit-market sentiment in year t−2 is associated with a decline in economic activity in years t and t+1." The mechanism is "predictable mean reversion in credit-market conditions": when credit risk is aggressively priced—narrow spreads, a high junk-bond share of issuance—spreads subsequently widen, and the widening coincides with the onset of a contraction. Investor sentiment in credit markets, not just financial frictions, emerges as a driver of business cycles.

The pipeline is a two-step time-series exercise: first forecast annual changes in the Baa–Treasury spread using the year t−2 sentiment proxies (the log credit spread and the Greenwood–Hanson high-yield issuance share), then regress real GDP-per-capita growth on the predicted spread change. Nearly a century of annual data, all from public sources.

- **Tasks**:
  - **Construct the dataset and replicate Figure I (the Baa–Treasury spread, 1929–2015)**: assemble the credit spread, the high-yield share, GDP per capita, inflation, and Treasury yields, with a summary-statistics table (this is the data-cleaning deliverable)
  - **Replicate Table I (forecasting growth with credit spreads and stock prices)**: OLS regressions of real GDP-per-capita growth on lagged spread changes and S&P 500 returns, with Newey–West standard errors
  - **Replicate Table II (the two-step sentiment results)**: the first-stage spread-change forecasting regressions and the second-stage effect of predicted spread changes on growth—the paper's central result
  - **Replicate Figure II (credit-market sentiment and economic growth)**: the fitted relationship over the full 1929–2015 sample
  - **Update**: extend the dataset and Tables I–II through the most recent available year—the post-2015 period (COVID, the 2022 tightening) is an interesting out-of-sample test
- **Data sources** (free and public unless noted): FRED (Moody's Baa yield, long-term Treasury yields, real GDP per capita, CPI); Robert Shiller's website (S&P 500 returns and P/E); Greenwood–Hanson high-yield share (posted with their paper's data; can be extended from Mergent FISD on WRDS); Federal Reserve Board website (excess bond premium, for the EBP robustness variant)
- **Notes**:
  - The high-yield share is the one input not on FRED. Use the series posted with Greenwood and Hanson (2013) ("Issuer Quality and Corporate Bond Returns," data on Robin Greenwood's HBS page) and extend it using Mergent FISD ratings and issuance data if you take on the update task.
- **Citation**: López-Salido, David, Jeremy C. Stein, and Egon Zakrajšek. "Credit-Market Sentiment and the Business Cycle." The Quarterly Journal of Economics 132, no. 3 (2017): 1373–1426. https://academic.oup.com/qje/article/132/3/1373/3787666
- **Paper PDF**: [LopezSalidoSteinZakrajsek2017CreditMarketSentiment.pdf](project_papers/LopezSalidoSteinZakrajsek2017CreditMarketSentiment.pdf)

## Corporate Events and Anomalies

### 4. [Predictable Corporate Distributions and Stock Returns](https://academic.oup.com/rfs/article/28/4/1199/1929063)

Firms tend to announce distributions—dividend increases, special dividends, stock dividends, and stock splits—"on the anniversary of a like announcement at the same firm." The market underreacts to this predictability: "a simple strategy that involves purchasing firms with high predicted probabilities of distribution announcements earns significant abnormal monthly returns," distinct from earnings-announcement and seasonality effects.

The pipeline: identify the four event types from the CRSP distribution master file (1963–2012) using the paper's filters, estimate a Cox proportional hazard model of follow-on announcements (elapsed time plus firm characteristics), then form monthly portfolios of stocks with the highest predicted event probabilities and measure their four-factor alphas. The hazard estimation is rolling and out-of-sample, exactly the kind of point-in-time discipline this course emphasizes.

*This paper is featured on the [Project Previews](project_previews.md) page.*

- **Tasks**:
  - **Replicate Table 1 and Figure 1 (event occurrence and recurrence)**: event counts by year and the probability of each event conditional on prior occurrence, including the frequency distribution by months since the previous event (this is the data-cleaning deliverable)
  - **Replicate Figure 5 (baseline hazard rates)**: the estimated hazard function showing the spikes at 12, 24, and 36 months—the paper's key descriptive fact
  - **Replicate Table 3 (hazard model estimates)**: Cox model coefficients for each of the four event types
  - **Replicate Table 5 (portfolio returns)**: raw returns and Fama–French–Carhart alphas for portfolios of stocks with high predicted probabilities of any distribution event
- **Data sources** (all available on WRDS): CRSP distribution master file (`crsp.msedist`; e.g., special dividends are distribution codes 5533/5538) and monthly/daily stock files; Compustat (ROA, cash balances); Fama–French–Carhart factors (`ff.factors_monthly`)
- **Notes**:
  - The Cox proportional hazard model is available in Python via the `lifelines` package (`CoxPHFitter`).
  - Follow the paper's sample filters carefully (share codes 10/11, the 5% dividend-increase threshold, and the 20–90 trading-day spacing rule for prior dividends)—getting the event sample right is most of the battle.
- **Citation**: Bessembinder, Hendrik, and Feng Zhang. "Predictable Corporate Distributions and Stock Returns." The Review of Financial Studies 28, no. 4 (2015): 1199–1241. https://academic.oup.com/rfs/article/28/4/1199/1929063
- **Paper PDF**: [BessembinderZhang2015PredictableCorporateDistributions.pdf](project_papers/BessembinderZhang2015PredictableCorporateDistributions.pdf)

## Options and Crash Risk

### 5. [Forecasting Crashes with a Smile](https://personal.lse.ac.uk/martiniw/oib_martin_shi_latest.pdf)

This paper derives "option-implied bounds on the probability of a crash in an individual stock" from the prices of options on the stock and on the S&P 500 index, using the Fréchet–Hoeffding copula bounds to handle any correlation structure between the two. The lower bound "successfully forecasts crashes both in and out of sample" and, unlike risk-neutral crash probabilities, avoids "crying wolf" during crisis periods.

The pipeline: pull month-end OptionMetrics volatility surfaces for the S&P 500 index and its constituent firms (1996–2022), filter and interpolate the smiles, recover risk-neutral CDFs via Breeden–Litzenberger, and combine the stock and index marginals into the crash-probability bounds. Section 2 and Appendix D spell out the computational steps.

- **Tasks**:
  - **Replicate Table 1 (summary statistics)**: realized crash frequencies, the upper and lower crash-probability bounds, and risk-neutral crash probabilities, averaged across firms and across time
  - **Replicate Figure 1 (Apple and AIG)**: time series of upper and lower bounds on the probability of a 20% one-month crash for Apple and AIG
  - **Replicate Figure 2 (cross-sectional medians)**: time series of the cross-sectional median upper and lower bounds, together with the crash probability of the S&P 500 index itself
  - **Replicate Table 2 (regression tests)**: in-sample regressions of realized crash indicators on the lower bound, the upper bound, and the risk-neutral crash probability
- **Data sources** (all available on WRDS):
  - OptionMetrics IvyDB US: volatility surfaces (`optionm_all.vsurfd{year}`; the S&P 500 index is `secid = 108105`) and the zero-coupon yield curve (`optionm_all.zerocd`)
  - CRSP: stock prices, returns, volume, shares outstanding, and S&P 500 constituent membership (`crsp.msp500list`)
  - CRSP–OptionMetrics link table (`wrdsapps_link_crsp_optionm`)
- **Notes**:
  - Use the OptionMetrics volatility surface file rather than raw option quotes—the surface already accounts for the early-exercise premium in American-style single-name options, which is why the paper (and the related literature) works from it. Only out-of-the-money options are used to compute the risk-neutral marginals.
- **Citation**: Martin, Ian W. R., and Ran Shi. "Forecasting Crashes with a Smile." Working paper, September 2025. https://personal.lse.ac.uk/martiniw/oib_martin_shi_latest.pdf
- **Paper PDF**: [MartinShi2025ForecastingCrashesWithASmile.pdf](project_papers/MartinShi2025ForecastingCrashesWithASmile.pdf)

### 6. [Information in Derivatives Markets: Forecasting Prices with Prices](https://personal.lse.ac.uk/martiniw/ARFE_published.pdf)

This survey covers "work that uses information in derivative and other asset prices to forecast movements in financial markets." Its centerpiece is the SVIX index—the risk-neutral variance of the S&P 500 return, computed from index option prices—which measures the equity premium in real time: for a log investor, the expected excess return on the market equals $R_f \cdot \text{SVIX}^2$. The survey updates the forecasting regressions of Martin (2017) through December 2022 and shows they hold up out of sample.

The pipeline: pull S&P 500 index option prices from OptionMetrics, compute the SVIX integral of out-of-the-money put and call prices over strikes (Equation 19), and run forecasting regressions of realized excess returns on SVIX². Figures 1 and 2 extend this from log utility to power utility using the risk-neutral moment formula in Equation 49.

- **Tasks**:
  - **Construct the SVIX index** at 1-, 3-, 6-, and 12-month horizons, daily from January 1996 to the present; plot the series and report summary statistics (this is the data-cleaning deliverable; compare with the plots in Martin (2017))
  - **Replicate Table 1 (forecasting the market)**: regressions of realized excess returns on SVIX² at 1-, 3-, 6-, and 12-month horizons, with Newey–West standard errors, for both the full 1996–2022 sample and the 2012–2022 subsample
  - **Replicate Figures 1 and 2 (the equity premium under power utility)**: the 1-month and 1-year equity premium for risk aversion γ = 1, 2, 3, computed from risk-neutral moments of the market return
  - **Update**: extend Table 1 and the SVIX series from the paper's end date (December 2022) through the most recent available data
- **Data sources** (all available on WRDS): OptionMetrics IvyDB US for S&P 500 index options (`secid = 108105`) and the zero-coupon yield curve; CRSP for S&P 500 total returns
- **Notes**:
  - Do not attempt Table 2 (currency forecasting with quanto contracts): the quanto forward data from Kremens and Martin (2019) is proprietary (Markit Totem) and not available on WRDS. Table 3 is from Martin and Wagner (2019) and is out of scope for this project.
  - S&P 500 (SPX) options are European style, so no early-exercise adjustment is needed—raw option prices can be used directly in the SVIX integral.
- **Citation**: Martin, Ian W. R. "Information in Derivatives Markets: Forecasting Prices with Prices." Annual Review of Financial Economics 17 (2025): 295–319. https://doi.org/10.1146/annurev-financial-082123-105811
- **Paper PDF**: [Martin2025InformationInDerivativesMarkets.pdf](project_papers/Martin2025InformationInDerivativesMarkets.pdf)

## Predicting the Equity Premium: The Classics

### 7. [A Comprehensive Look at the Empirical Performance of Equity Premium Prediction](https://doi.org/10.1093/rfs/hhm014)

This is the classic skeptic's paper on market-return forecasting—and the source of the predictor dataset used in the "Virtue of Complexity" project above. The authors "comprehensively reexamine the performance of variables that have been suggested by the academic literature to be good predictors of the equity premium" (dividend ratios, earnings ratios, book-to-market, interest rates and spreads, inflation, net issuance, and more) and find that "by and large, these models have predicted poorly both in-sample and out-of-sample for 30 years"; most would not have helped a real-time investor time the market.

The heart of the project is constructing the predictor variables from primary sources and then comparing in-sample fit against honest out-of-sample forecasts, following the paper's recursive estimation scheme. Amit Goyal posts the finished dataset (updated annually) on his website—you should use it to *validate* your construction, not as your data source.

- **Tasks**:
  - **Construct the annual predictor dataset from primary sources** (CRSP, Compustat, FRED, and Robert Shiller's website), and produce a summary-statistics table plus a validation table showing correlations between your series and Goyal's posted series (this is the data-cleaning deliverable and the bulk of the work)
  - **Replicate Table 1 (annual predictive performance)**: in-sample and out-of-sample R² for each individual predictor, following the paper's recursive out-of-sample procedure
  - **Replicate Figures 1 and 2 (cumulative squared-error plots)**: the paper's signature graphs showing cumulative out-of-sample performance of each predictor relative to the historical-mean benchmark over time
  - **Update**: extend Table 1 and the figures through the most recent available year and compare with the follow-up paper by Goyal, Welch, and Zafirov (2024)
- **Data sources**: CRSP (market returns, T-bill/risk-free rates), Compustat (book values, corporate issuance), FRED (interest rates, inflation), Robert Shiller's website (long-history dividends and earnings); Amit Goyal's website for validation
- **Notes**:
  - You do not need to replicate every row of Table 1—cover the main price-based predictors (dp, dy, ep, b/m), the interest-rate variables (tbl, lty, ltr, tms, dfy, dfr), inflation, and net equity issuance. The corporate-issuance and cross-sectional-premium variables may be skipped.
  - This project pairs naturally with the "Virtue of Complexity" project above: same data, opposite conclusion.
- **Citation**: Welch, Ivo, and Amit Goyal. "A Comprehensive Look at the Empirical Performance of Equity Premium Prediction." The Review of Financial Studies 21, no. 4 (2008): 1455–1508. https://doi.org/10.1093/rfs/hhm014
- **Paper PDF**: [WelchGoyal2008EquityPremiumPrediction.pdf](project_papers/WelchGoyal2008EquityPremiumPrediction.pdf)

### 8. [Predictive Regressions](https://www.sciencedirect.com/science/article/pii/S0304405X99000410)

This is the classic paper on the econometrics of return forecasting—the source of the "Stambaugh bias." When a return is regressed on a persistent lagged regressor like the dividend yield, "the regression disturbance is correlated with the regressor's innovations," so the OLS slope is biased upward in finite samples: for 1927–1996, "the bias equals one-third of the OLS estimate." The paper characterizes the finite-sample distribution of the predictive slope and contrasts frequentist p-values with Bayesian posteriors under different priors.

The data work is light (monthly value-weighted NYSE returns and dividend yields from CRSP), so the heart of this project is simulation: Monte Carlo evaluation of the finite-sample distribution of the OLS estimator and posterior simulation for the Bayesian analysis. This is a project for a group that wants to go deep on econometrics rather than data engineering.

- **Tasks**:
  - **Construct the data**: monthly value-weighted NYSE excess returns and the dividend-price ratio (dividends over the trailing 12 months), 1927–1996 and extended to the present; report OLS estimates of the predictive slope and the dividend yield's autocorrelation for each of the paper's four subsamples (this is the data-cleaning deliverable)
  - **Replicate Table 1 (finite-sample properties of the OLS slope)**: simulate the bias, skewness, and true p-values of the OLS estimator across the four sample periods
  - **Replicate Table 2 (Bayesian posterior moments)**: posterior mean, standard deviation, and P(β ≤ 0) for the predictive slope under the paper's prior and conditioning specifications
  - **Replicate Figure 1 (estimates of β and ρ)**: compare OLS, bias-adjusted, and Bayesian estimates across subperiods
  - **Update**: re-run Table 1 and Table 2 on a sample extended through the most recent available year
- **Data sources**: CRSP monthly stock file (value-weighted NYSE returns with and without dividends; one-month T-bill rate)
- **Citation**: Stambaugh, Robert F. "Predictive Regressions." Journal of Financial Economics 54, no. 3 (1999): 375–421. https://www.sciencedirect.com/science/article/pii/S0304405X99000410
- **Paper PDF**: [Stambaugh1999PredictiveRegressions.pdf](project_papers/Stambaugh1999PredictiveRegressions.pdf)

### 9. [Predicting Returns with Financial Ratios](https://www.sciencedirect.com/science/article/pii/S0304405X04000686)

This paper is the rejoinder to Stambaugh (1999) above: small-sample corrections that treat the dividend yield's persistence as a free parameter "can substantially understate forecasting power." Because the yield's autocorrelation ρ cannot exceed one (prices would explode), imposing ρ ≈ 1 gives a conservative but far more powerful test. With it, "dividend yield predicts market returns during the period 1946–2000, as well as in various subsamples," and book-to-market and the earnings-price ratio predict returns over 1963–2000.

The project builds the aggregate financial ratios from CRSP and Compustat, then implements three estimators side by side: standard OLS, the Stambaugh bias adjustment, and the paper's ρ ≈ 1 bound. This pairs naturally with the Stambaugh project above—same data, opposite conclusion.

- **Tasks**:
  - **Replicate Table 1 (summary statistics)**: moments and autocorrelations of equal- and value-weighted NYSE returns, dividend yield, book-to-market, and the earnings-price ratio, for the full sample and both halves (this is the data-cleaning deliverable)
  - **Replicate Table 2 (dividend yield predictability, 1946–2000)**: monthly predictive regressions of nominal, real, and excess NYSE returns on log dividend yield, reporting OLS, Stambaugh-adjusted, and ρ ≈ 1 estimates with p-values
  - **Replicate Table 3 (subsample results)**: the same regressions for 1946–1972 and 1973–2000
  - **Replicate Table 5 (book-to-market) or Table 6 (earnings-price ratio)**: predictive regressions for 1963–1994 and 1963–2000 using the same three estimators
  - **Update**: extend Tables 1 and 2 through the most recent available year
- **Data sources**: CRSP (equal- and value-weighted NYSE index returns, dividends, one-month T-bill rate); Compustat (book equity and operating earnings for the aggregate ratios); CPI from FRED for real returns
- **Citation**: Lewellen, Jonathan. "Predicting Returns with Financial Ratios." Journal of Financial Economics 74, no. 2 (2004): 209–235. https://www.sciencedirect.com/science/article/pii/S0304405X04000686 (free copy: https://web.mit.edu/lewellen/www/Documents/FinancialRatios.pdf)
- **Paper PDF**: [Lewellen2004PredictingReturnsFinancialRatios.pdf](project_papers/Lewellen2004PredictingReturnsFinancialRatios.pdf)

### 10. [Consumption, Aggregate Wealth, and Expected Stock Returns](https://doi.org/10.1111/0022-1082.00347)

This classic paper introduces *cay*, the deviation of log consumption from its shared trend with log asset wealth and log labor income. The authors find that "fluctuations in the consumption-wealth ratio are strong predictors of both real stock returns and excess returns," beating the dividend yield and other popular forecasters at short and intermediate horizons. The economic logic: when consumers expect returns to fall, they let consumption drift below its long-run relationship with wealth and income, so *cay* reveals expectations in real time.

The pipeline: assemble quarterly consumption, labor income, and household net worth from NIPA and the Flow of Funds, estimate the cointegrating relationship by dynamic least squares (Stock–Watson), construct *cay* as the estimated trend deviation, and run forecasting regressions of S&P Composite and CRSP value-weighted returns on it. All data is free and publicly available; only the CRSP returns require WRDS.

- **Tasks**:
  - **Construct *cay***: build the consumption, labor income, and wealth series (the paper's appendix describes the NIPA and Flow of Funds components), estimate the cointegrating regression by DLS, and validate your series against the updated *cay* posted on Sydney Ludvigson's website; report Table II (summary statistics of *cay* and the financial variables) as the data-cleaning deliverable
  - **Replicate Figure 1 (excess returns and trend deviations)**: the standardized *cay* series plotted against excess returns with NBER recession shading
  - **Replicate Table III (one-quarter-ahead forecasting regressions)**: real and excess returns on the S&P Composite and CRSP value-weighted indexes regressed on lagged *cay* and competitor predictors
  - **Replicate Table VI (long-horizon regressions)**: consumption growth (Panel A) and excess returns (Panel B) at horizons of 1 to 24 quarters regressed on lagged *cay*, the dividend yield, and other forecasters
  - **Update**: extend *cay* and the forecasting regressions through the most recent available quarter
- **Data sources**: BEA NIPA tables via FRED (consumption, labor income components); Federal Reserve Z.1 Financial Accounts via FRED (household net worth); CRSP (value-weighted returns, 30-day T-bill); Robert Shiller's website (S&P Composite prices, dividends, earnings); Sydney Ludvigson's website (updated *cay* for validation)
- **Notes**:
  - NIPA and Flow of Funds data have been heavily revised since 2001, so your point estimates will differ somewhat from the paper's—matching the qualitative patterns and validating against Ludvigson's posted series is the standard for success.
- **Citation**: Lettau, Martin, and Sydney Ludvigson. "Consumption, Aggregate Wealth, and Expected Stock Returns." The Journal of Finance 56, no. 3 (2001): 815–849. https://doi.org/10.1111/0022-1082.00347
- **Paper PDF**: [LettauLudvigson2001ConsumptionAggregateWealth.pdf](project_papers/LettauLudvigson2001ConsumptionAggregateWealth.pdf)

### 11. [Are Dividends and Stock Returns Predictable? New Evidence Using M&A Cash Flows](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2578393)

Aggregate dividend growth is famously unpredictable by the dividend-price ratio—Cochrane's "the dog that did not bark." This paper argues that result is "due to the mismeasurement of dividends used in empirical work": the standard CRSP index-extracted dividend measure misses cash paid to shareholders in M&A transactions. Once M&A cash dividends are included, "the adjusted R² from a regression of dividend growth on the lagged dividend-price ratio goes from being negative (−1.07%) to positive (17.47%)."

The pipeline is a bottom-up aggregation exercise: sum dividends security-by-security from the CRSP monthly stock file—ordinary (distribution codes 1xxx), liquidation (2xx2/2xx8), and M&A cash dividends (codes 3000–3400)—into aggregate dividend growth and dividend-price series, then run the classic predictability regressions with and without the M&A component.

- **Tasks**:
  - **Replicate Table 1 and Figure 1 (the dividend measures)**: descriptive statistics of the comprehensive dividend measure versus the standard CRSP index-extracted measures, and the time series of aggregate cash flows split by type (this is the data-cleaning deliverable)
  - **Replicate Figures 3 and 4 (dividend growth and dividend-price ratios)**: time-series comparison of the new and traditional measures
  - **Replicate Table 3 (annual predictability regressions)**: dividend growth and returns regressed on the lagged dividend-price ratio, showing the reversal of the "dog that did not bark" result
  - **Replicate Table 6 (VAR estimates and long-run coefficients)**: the Campbell–Shiller/Cochrane present-value decomposition with the corrected dividend measure
  - **Update**: extend the dividend series and Table 3 through the most recent available year
- **Data sources**: CRSP monthly stock file and distribution events (via WRDS); Robert Shiller's website (CPI); Amit Goyal's website (risk-free rate); BEA NIPA (personal consumption expenditure)
- **Notes**:
  - This is a newer working paper rather than an established classic—but that cuts both ways: it is a live research question, and the replication itself (bottom-up dividend aggregation from CRSP distribution codes) is exactly the kind of careful data construction this course is about.
- **Citation**: Sabbatucci, Riccardo. "Are Dividends and Stock Returns Predictable? New Evidence Using M&A Cash Flows." Working paper, November 2022. Available at SSRN: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2578393
- **Paper PDF**: [Sabbatucci2022DividendsMACashFlows.pdf](project_papers/Sabbatucci2022DividendsMACashFlows.pdf)

## Equity Term Structures

### 12. [Equity Term Structures without Dividend Strips Data](https://ssrn.com/abstract=3533486)

Traded dividend strips directly reveal the term structure of equity risk premia, but the data only start around 2004 and cover few assets. This paper estimates "a rich affine model of equity prices, dividends, returns, and their dynamics" from a large cross-section of anomaly portfolios and shows that the model "prices dividend strips of the market and equity portfolios without using strips data in the estimation." The result is a synthetic equity term structure extending back to the 1970s.

The data work is a classic cross-sectional asset pricing pipeline: build 102 value-weighted portfolios (terciles on 51 characteristics) from CRSP and Compustat following Kozak, Nagel, and Santosh (2020), compute portfolio dividend yields, and extract principal components. The author's website (https://www.serhiykozak.com/data) posts the portfolio data and the model-implied yields, so you can validate each step of your pipeline.

- **Tasks**:
  - **Replicate Table I (variance explained by anomaly PCs)**: the factor structure of the 51 long-short anomaly portfolios and the 102 underlying legs
  - **Replicate Figures 1 and 2 (factor yields and factor returns)**: time series of the market and the three PC factors that make up the state vector (this plus Table I is the data-cleaning deliverable)
  - **Replicate Figure 7 (model-implied forward equity yields for the market)**: estimate the model and plot forward equity yields across maturities, 1973–2020
  - **Replicate Figure 8 (term structures conditional on NBER recessions)**: average term structures in recessions versus expansions—the cyclicality result at the heart of the equity term structure literature
  - **Validate** your model-implied yields against the estimates posted on the author's website
- **Data sources**: CRSP and Compustat (WRDS); one-year risk-free rate and Gürkaynak–Sack–Wright Treasury yields (Federal Reserve, free); benchmark data and code from https://www.serhiykozak.com/data
- **Notes**:
  - Skip Figures 3–6 and Table IV: they compare the model to traded dividend strip and futures data (van Binsbergen–Koijen, Bansal et al.), which is proprietary and not on WRDS. The validation step against the author's posted yields plays that role instead.
- **Citation**: Giglio, Stefano, Bryan Kelly, and Serhiy Kozak. "Equity Term Structures without Dividend Strips Data." Journal of Finance 79, no. 6 (2024): 4143–4196. Available at SSRN: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3533486
- **Paper PDF**: [GiglioKellyKozak2024EquityTermStructures.pdf](project_papers/GiglioKellyKozak2024EquityTermStructures.pdf)

### 13. [Equity Duration and Predictability](https://www.sciencedirect.com/science/article/pii/S0304405X25001229)

Why do expected returns—rather than dividend growth—dominate stock price movements in postwar data, when the opposite held for the previous three centuries? This paper's answer is rising equity duration: as firms cut payout ratios after 1945, the market became a longer-duration asset, and "expected returns vary more for payouts further into the future." The authors document this in three datasets: S&P 500 dividend strips (a short-duration version of the market), the aggregate market from 1629 to 2022, and payout-sorted stock portfolios. "Between 1629 and 1945, expected returns explain around 35% of the variation in the dividend-to-price ratio. In the post-1945 period, this increases to 90%."

The method is the same throughout: predictive regressions of returns and dividend growth on the dividend-to-price ratio, with the R²-style decomposition ER + EDG = 1. The authors post their data and code (Mendeley Data, linked from the article), the dividend strip series is on Benjamin Golez's webpage, and the 1629–2015 historical series comes from Golez and Koudijs (2018).

- **Tasks**:
  - **Replicate Tables 1, 4, and 6 (summary statistics)** and **Figure 1 (total payout, 1871–2022)**: the three datasets' summary statistics and the payout-ratio decline that drives the paper (this is the data-cleaning deliverable)
  - **Replicate Table 2 (strips versus market)**: predictive regressions for dividend strips and the market, 1996–2022, showing expected returns matter more for the longer-duration claim
  - **Replicate Table 5 (subperiod predictability, 1629–2022)**: the ER/EDG decomposition across the four historical subperiods—the paper's central result
  - **Replicate Table 7 and Figure 3 (payout-sorted portfolios)**: predictability results for low/medium/high payout portfolios built from CRSP and Compustat, and the summary plot of ER against payout ratios
  - **Skip** Tables 8 and 9 (the calibrated present-value model)
- **Data sources**: paper's data and code package (Mendeley Data); dividend strip series from Benjamin Golez's webpage; Golez–Koudijs (2018) historical series (1629–2015, included in the package); CRSP and Compustat (WRDS) for the cross-section; Davis–Fama–French book equity from Kenneth French's website; S&P 500 total returns from CRSP
- **Notes**:
  - The paper uses Datastream for the S&P 500 price and total return indexes; CRSP's S&P 500 series is an equivalent substitute.
- **Citation**: Golez, Benjamin, and Peter Koudijs. "Equity Duration and Predictability." Journal of Financial Economics 171 (2025): 104114. https://www.sciencedirect.com/science/article/pii/S0304405X25001229
- **Paper PDF**: [GolezKoudijs2025EquityDurationPredictability.pdf](project_papers/GolezKoudijs2025EquityDurationPredictability.pdf) (companion data paper: [GolezKoudijs2018FourCenturiesReturnPredictability.pdf](project_papers/GolezKoudijs2018FourCenturiesReturnPredictability.pdf))

## Macro-Finance and Fiscal Policy

### 14. [Debt and Deficits: Fiscal Analysis with Stationary Ratios](https://personal.lse.ac.uk/martiniw/Debt%20and%20Deficits%20250806.pdf)

This paper asks how governments ultimately deal with a weak fiscal position: do taxes rise, does spending fall, or do the returns to holders of government debt adjust? The debt-GDP ratio is nonstationary in long historical data, so the authors instead construct a stationary "fiscal position" measure—a loglinear combination of tax revenue, government spending, and the market value of government debt. They find that "fiscal adjustment, particularly through changes in spending, is the empirically relevant channel" for resolving weak fiscal positions.

This project involves assembling long historical time series (US 1841–2022, UK 1727–2022) by splicing together data from several public sources—a valuable exercise in data cleaning and documentation. All data is free and publicly available; no WRDS subscriptions are needed. The internet appendix (section IA.1) describes the data sources in detail.

- **Tasks**:
  - **Replicate the summary statistics table** (internet appendix, section IA.5): means, standard deviations, and autocorrelations of debt returns, tax growth, spending growth, and the key ratios, for US and UK
  - **Replicate Figure 1** (debt-GDP ratio in US and UK): the visual demonstration that debt-GDP is nonstationary
  - **Replicate Figure 2** (tax-debt and spending-debt ratios in US and UK): the two ratios are individually nonstationary but cointegrated
  - **Replicate Figure 3** (the fiscal position and surplus-debt ratio in US and UK): construct the paper's loglinear fiscal position measure and show it is stationary
  - **Replicate Table 1** (local projections, US and UK): regressions of cumulative future debt returns, tax growth, and spending growth on the fiscal position—the paper's central result
- **Data sources** (all free and public):
  - US: OMB total receipts, outlays, and interest payments (FRED, since 1901); market value of marketable federal debt from the Federal Reserve Bank of Dallas (from 1942) spliced with [Hall and Sargent (2021)](https://www.tomsargent.com/) data for earlier years; GDP and GDP deflator from BEA and [MeasuringWorth](https://www.measuringworth.com/)
  - UK: [OBR historical public finances database](https://obr.uk/data/) (tax revenue and spending); market value of central government debt from the Bank of England's [A Millennium of Macroeconomic Data](https://www.bankofengland.co.uk/statistics/research-datasets) (1727–2016) spliced with BIS data (2017–2022); UK GDP and deflator from MeasuringWorth
- **Citation**: Campbell, John Y., Can Gao, and Ian W. R. Martin. "Debt and Deficits: Fiscal Analysis with Stationary Ratios." Working paper, August 2025. https://personal.lse.ac.uk/martiniw/Debt%20and%20Deficits%20250806.pdf
- **Paper PDF**: [CampbellGaoMartin2025DebtAndDeficits.pdf](project_papers/CampbellGaoMartin2025DebtAndDeficits.pdf)
