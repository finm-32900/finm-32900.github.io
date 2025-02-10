# List of Potential Final Projects

The project that you are assigned will come from one of the following three categories: white papers, data series from "Evidence from Many Asset Classes", or replications of arbitrage spreads from the paper "Segmented Arbitrage".

- If you can't access the papers below, you can find a link to them here: https://drive.google.com/drive/folders/10OvVRXb-G31PHV95smF06HkahRpnCh_d?usp=sharing

## White Papers

### 1. [Lewellen (2015), Critical Finance Review. “The Cross-section of Expected Stock Returns”](https://faculty.tuck.dartmouth.edu/images/uploads/faculty/jonathan-lewellen/ExpectedStockReturns.pdf)

This paper will teach you how to combine many firm characteristics into real-time forecasts of a stock’s expected returns. See the abstract: "This paper studies the cross-sectional properties of return forecasts derived from Fama-MacBeth regressions. These forecasts mimic how an investor could, in real time, combine many firm characteristics to obtain a composite estimate of a stock’s expected return. Empirically, the forecasts vary substantially across stocks and have strong predictive power for actual returns. For example, using ten-year rolling estimates of Fama-MacBeth slopes and a cross-sectional model with 15 firm characteristics (all based on low-frequency data), the expected-return estimates have a cross-sectional standard deviation of 0.87% monthly and a predictive slope for future monthly returns of 0.74, with a standard error of 0.07."

  - Task: Replicate Table 1, Table 2, and Figure 1
  - Data sources: CRSP and Compustat
  - Citation: Lewellen, Jonathan W., The Cross Section of Expected Stock Returns (August 22, 2014). Forthcoming in Critical Finance Review, Tuck School of Business Working Paper No. 2511246, Available at SSRN: https://ssrn.com/abstract=2511246 or http://dx.doi.org/10.2139/ssrn.2511246
  - Notes: I will provide some starter code that partially constructs some of these tables. In this project, you'll have to complete the code.

### 2.	[Monetary Tightening and US Bank Fragility in 2023](https://www.nber.org/papers/w31048)

This paper will teach you how to use bank call reports to construct measures of the financial condition of banks. This is especially useful if you have interest in specializing, for example, in specializing in equities covering the financial sector.

 - Task: Replicate Table 1, Table A1 and Figure A1
 - Citation: Jiang et al (2023). Monetary Tightening and US Bank Fragility in 2023: Mark-to-Market Losses and Uninsured Depositor Runs?. No. w31048. National Bureau of Economic Research, 2023. https://www.nber.org/papers/w31048
 - Data sources: Bank Call Reports. See https://wrds-www.wharton.upenn.edu/pages/get-data/bank-regulatory/
 - Notes: I will provide some starter code that will replicate most of Table 1.


### 3. [Intermediary Asset Pricing: New Evidence from Many Asset Classes](https://zhiguohe.net/wp-content/uploads/2023/12/jfepublishedversion.pdf)

This project will give you experience in analyzing the balance sheet fundamentals of large broker-dealers, in this case the full set of primary dealers in the US, and how the financial condition of these primary dealers affect the US stock market as a whole.

 - Task: Replicate Table 2, and Table 3 (Panel A only, but Panel B for bonus)
 - Data used: CRSP, Compustat, Datastream
 - Some code and data is available online [here](https://zhiguohe.net/publications/research/) and [here](https://zhiguohe.net/data-and-empirical-patterns/intermediary-capital-ratio-and-risk-factor/).
 - Citation: He, Zhiguo, Bryan Kelly, and Asaf Manela. "Intermediary asset pricing: New evidence from many asset classes." Journal of Financial Economics 126, no. 1 (2017): 1-35.
 - Note: I will provide some code that will help you get started.

### 4.	[Dividend growth expectations from changes in dividend strips, from “Coronavirus: Impact on Stock Prices and Growth Expectations”](https://ssrn.com/abstract=3555917)

This paper will teach you how to construct forecasts of the cash flows of stocks. That is, you will separate out the effects of changes in discount rates from changes in dividend growth. From the abstract, “Dividend futures, which are claims to dividends on the aggregate stock market in a particular year, can be used to directly compute a lower bound on growth expectations across maturities or to estimate expected growth using a forecasting model. We show how the actual forecast and the bound evolve over time.”

 - Task: Replicate Figure 1, Figure 5, and Table 1
 - Citation: Gormsen, Niels Joachim and Koijen, Ralph S. J., Coronavirus: Impact on Stock Prices and Growth Expectations (August 3, 2020). University of Chicago, Becker Friedman Institute for Economics Working Paper No. 2020-22, Available at SSRN: https://ssrn.com/abstract=3555917 or http://dx.doi.org/10.2139/ssrn.3555917 
 - Data source: Bloomberg

### 5.	[Forward Return Expectations](https://ssrn.com/abstract=4565351)

This paper deals with extracting return expectations from option prices. More than simply measuring return expectations as a whole, this paper constructs expectations as different horizons. See the abstract: “We measure investors' short- and long-term stock-return expectations using both options and survey data. These expectations at different horizons reveal what investors think their own short-term expectations will be in the future, or forward return expectations. While contemporaneous short-term expectations are not countercyclical across all data sources, we find that forward expectations are consistently countercyclical, and excessively so: in bad times, forward expectations are higher than justified by investors' own subsequent short-term return expectations. This excess volatility in forward expectations helps account for excess volatility in prices, inelastic demand for equities, and stylized facts about the equity term structure.”

 - Task: Replicate Table 1 and Figure 1
 - Data: OptionMetrics
 - Citation: Gandhi, Mihir and Gormsen, Niels Joachim and Lazarus, Eben, Forward Return Expectations (September 7, 2023). Available at SSRN: https://ssrn.com/abstract=4565351 or http://dx.doi.org/10.2139/ssrn.4565351

### 6.	[Market Expectations in the Cross-Section of Present Values](https://doi.org/10.1111/jofi.12060)

This paper demonstrates that returns and cash flows for the aggregate US stock market are highly predictable. It demonstrates this by constructing a univariate predictor from the cross section of stocks. See the abstract:

 > Returns and cash flow growth for the aggregate U.S. stock market are highly and robustly predictable. Using a single factor extracted from the cross-section of book-to market ratios, we find an out-of-sample return forecasting R2 of 13% at the annual frequency (0.9% monthly). We document similar out-of-sample predictability for returns on value, size, momentum, and industry portfolios. We present a model linking aggregate market expectations to disaggregated valuation ratios in a latent factor system. Spreads in value portfolios’ exposures to economic shocks are key to identifying predictability and are consistent with duration-based theories of the value premium.

Also, from their paper, 

 > “Our approach attacks a challenging problem in empirical asset pricing: how does one exploit a wealth of predictors in relatively short time series? If the predictors number near or more than the number of observations, the standard ordinary least squares (OLS) forecaster will be poorly behaved or nonexistent (see Huber (1973)). Our solution is to use partial least squares (PLS; Wold (1975)), which is a simple regression-based procedure designed to parsimoniously forecast a single time series using a large panel of predictors. We use it to construct a univariate forecaster for market returns (or dividend growth) that is a linear combination of assets’ valuation ratios.”

 - Task: Replicate Table 1
 - Data sources: CRSP and Compustat
 - Citation: KELLY, B. and PRUITT, S. (2013), Market Expectations in the Cross-Section of Present Values. THE JOURNAL OF FINANCE, 68: 1721-1756. https://doi.org/10.1111/jofi.12060


## Replications of data series from “Evidence from Many Asset Classes”

He, Kelly, and Manela (2017) is a well known paper that examines the effects that intermediaries’ balance sheets have on asset prices. This paper happens to test this theory on a variety of asset classes, going beyond just debt and equity. The projects in this section will be to replicate the test asset returns across this variety of asset classes. Each project below focuses on a different asset class. The returns of these tests assets are provided here. The data provided in that file goes up until 2012. Your project will be to replicate that data up until 2012 and then provide updated returns going as close to the present as possible. The derivation of the returns is defined by a separate paper. These are listed below.

### 7.	Corporate Bond Portfolio Returns
This will give you experience in working with corporate bonds.

 - Task: Replicate the corporate bond columns from He_Kelly_Manela_Factors_And_Test_Assets_monthly.csv (https://asafmanela.github.io/papers/hkm/intermediarycapitalrisk/He_Kelly_Manela_Factors.zip )
 - Data used: Bond Returns by WRDS (https://wrds-www.wharton.upenn.edu/pages/get-data/wrds-bond-returns/), but maybe also FINRA TRACE (https://wrds-www.wharton.upenn.edu/pages/get-data/otc-corporate-bond-and-agency-debt-bond-transaction-data/) , Mergent FISD/NAIC, TRACE, and Lehman Brothers Fixed Income Database.
 - Citation: Nozawa, Yoshio. “What Drives the Cross‐Section of Credit Spreads?: A Variance Decomposition Approach.” The Journal of Finance 72, no. 5 (2017): 2045-2072.
 - Note: You may use data from openbondassetpricing.com/ and here (https://github.com/Alexander-M-Dickerson/TRACE-corporate-bond-processing/blob/main/WRDS/MakeCreditSpreads.py) if it’s helpful.

### 8. 	Credit Default Swap Returns

This replication will give you experience using the Markit data source for Credit Default Swaps. If you’re interested in CDS, this is the canonical paper you should know for constructing returns on these instruments.

 - Task: Replicate the Credit Default Swap columns from He_Kelly_Manela_Factors_And_Test_Assets_monthly.csv (https://asafmanela.github.io/papers/hkm/intermediarycapitalrisk/He_Kelly_Manela_Factors.zip )
 - These columns are described in He, Kelly, and Manela. (2017), but the definition of returns on CDS contracts comes from Palhares (2013).
 - Data used: Markit
 - Citation: Palhares, Diogo. Cash-flow maturity and risk premia in CDS markets. The  University of Chicago, 2013.



### 9. Commodity Futures Returns

This replication will give you experience in working with commodity futures and constructing return series from them. 

 - Task: Replicate Table 1. It may be difficult to replicate the commodities columns in He_Kelly_Manela_Factors_And_Test_Assets_monthly.csv (https://asafmanela.github.io/papers/hkm/intermediarycapitalrisk/He_Kelly_Manela_Factors.zip ), but you may try.
 - Data used: Futures Contract data from Datastream
 - Citation: Yang, Fan. “Investment shocks and the commodity basis spread.” Journal of Financial Economics 110, no. 1 (2013): 164-184.


## Replicate Arbitrage Spreads from “Segmented Arbitrage”

The projects in this section will have students replicate various arbitrage spreads studied in the paper “Segmented Arbitrage” https://www.hbs.edu/ris/Publication%20Files/24-030_1506d32b-3190-4144-8c75-a2326b87f81e.pdf by Emil Siriwardane, Adi Sunderam, and Jonathan Wallen.

This paper examines various so-called arbitrage trades and makes the observation that the price dynamics of these trades challenges various asset pricing models that have been used in the past to explain deviations from no-arbitrage.
The internet appendix gives more detail as to how each trade works: https://www.emilsiriwardane.com/s/Appendix.pdf 

One of the authors, Emil Siriwardane https://www.emilsiriwardane.com/, makes code and data available for these trades online: https://github.com/esiriwardane/arbitrage-spreads-public However, much of the code is in Stata. Your goal will be to rewrite these in Python and automate the pulls of the data (to the extent possible).

**Tasks**
 
 - For each of the following, you should replicate the associated panel in Figure A1 in the Appendix (See https://www.emilsiriwardane.com/s/Appendix.pdf)
 - Replicate the series shown in the paper, but also compute the series up to the present (so that the reporting of the size of the arbitrage spread can be automated)
 - In each case that Bloomberg is used, please try to use Datastream as an alternative if possible

### 10. FX Covered Interest Parity Spread

This trade is based off of the covered interest parity (CIP). A CIP deviation is a spread between a cash riskless rate and a synthetic riskless rate. The synthetic rate is local currency borrowing swapped into a foreign denominated rate using cross-currency derivatives.

 - Data used: Bloomberg, maybe Datastream


### 11. Equity Spot Futures
“We construct arbitrage implied forward rates using the nearby and first deferred futures contracts for the S&P 500, Dow Jones, and Nasdaq 100 indices.”

 - Data used: Bloomberg

### 12. Treasury Spot-Futures
Replicate the data pull and the construction of the Treasury-Spot Futures spread. The Treasury spot-futures arbitrage trade involves exploiting the price discrepancy between Treasury futures contracts and the underlying Treasury securities in the cash (spot) market. By simultaneously buying (or selling) the mispriced asset and selling (or buying) its equivalent in the other market, arbitrageurs aim to lock in a risk-free profit, accounting for carry costs, accrued interest, and delivery options.

 - Data used: Bloomberg

### 13. Treasury Swap

In an interest rate swap, one counterparty agrees to pay a series of predetermined payments based on the so-called fixed rate (or swap rate) prevailing at the swap’s inception. In return, the counterparty receives a series of stochastic floating payments that is determined based on the future realization of a short-term reference rate.

 - Data used: Bloomberg

### 14. TIPS Treasury

“In the market for US sovereign debt, there is a no-arbitrage condition between inflation-swapped Treasury Inflation-Protected Securities (TIPS) and Treasuries (Fleckenstein et al., 2014). TIPS are US Treasury obligations for which the principal amount (and coupons) are adjusted for the Consumer Price Index (CPI). These inflation adjustments may be undone using an inflation swap, yielding fixed cash flows. The arbitrage spread is the difference in yield between this synthetic nominal Treasury constructed from TIPS and inflation swaps and a nominal Treasury”

 - Data sources: Bloomberg, and the Federal Reserve’s Yield Curve data (for zero coupon bond yields: https://www.federalreserve.gov/data/yield-curve-tables/feds200628_1.html )

### 15. Corporate CDS-Bond Spread

Replicate the data pull and construction of the series using the Markit Credit Default Swap data in conjunction with the Corporate Bond data on wrds.

 - Replicate the final CDS-Bond basis spread given in final_cds_bases.xlsx here: https://github.com/esiriwardane/arbitrage-spreads-public/tree/main/raw Your numbers should match theirs nearly precisely.
 - Extra credit available if this is chosen. 
 - Data used: Markit CDS, Corporate TRACE



