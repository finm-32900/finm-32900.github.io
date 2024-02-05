# List of Potential Final Projects

The project that you are assigned will come from one of the following three categories: papers, data series from "Evidence from Many Asset Classes", or "other".

## Papers

1. [Lewellen (2015), Critical Finance Review. “The Cross-section of Expected Stock Returns”](https://faculty.tuck.dartmouth.edu/images/uploads/faculty/jonathan-lewellen/ExpectedStockReturns.pdf)

    - Replicate Table 1, Table 2, and Figure 1
    - Data used: CRSP and Compustat

2. [Jiang et al (2023). Monetary Tightening and US Bank Fragility in 2023: Mark-to-Market Losses and Uninsured Depositor Runs?. No. w31048. National Bureau of Economic Research, 2023.](https://www.nber.org/papers/w31048)

    - Replicate Table 1
    - Data used: Bank Call Reports. See https://wrds-www.wharton.upenn.edu/pages/get-data/bank-regulatory/

3. [Jiang et al (2023). Monetary Tightening and US Bank Fragility in 2023: Mark-to-Market Losses and Uninsured Depositor Runs?. No. w31048. National Bureau of Economic Research, 2023.](https://www.nber.org/papers/w31048)

    - Replicate Table A1 and Figure A1
    - Data used: Bank Call Reports. See https://wrds-www.wharton.upenn.edu/pages/get-data/bank-regulatory/

4. [Koijen and Yogo, A Demand System Approach to Asset Pricing (2019). Journal of Political Economy](https://ssrn.com/abstract=2537559)

    - Replicate Table D1
    - Data used: Securities and Exchange Commission Form 13F, via Thomson Reuters. See https://wrds-www.wharton.upenn.edu/pages/get-data/thomson-reuters/

5. [Li Wang (2023), Valuation Duration of the Stock Market](https://chenwang.one/publication/dr/)

    - Replicate Table 1
    - Data used: S&P500 Futures (authors use Datastream, you may use the Bloomberg terminal), Fama-Bliss database, CRSP, and S&P Global via Goyal and Welch (2007).

6. [Peng Wang (2023), Factor Demand and Factor Returns](https://chenwang.one/files/fdfr.pdf)

    - Replicate Table 1 and Table 2
    - Data used: CRSP, Securities and Exchange Commission Form 13F, via Thomson Reuters. See https://wrds-www.wharton.upenn.edu/pages/get-data/thomson-reuters/

7. [Li Wang (2023), Rediscover Predictability: Information from the Relative Prices of Long-term and Short-term Dividends](https://chenwang.one/files/pr.pdf)

    - Replicate Table 1 and part of Table 2 (the betas and the R-squared, but not the standard errors)
    - Data used: S&P 500 futures (Source: Bloomberg) and Fama-Bliss database

8. [Nagel, Stefan. "Evaporating liquidity." The Review of Financial Studies 25, no. 7 (2012): 2005-2039](https://bpb-us-w2.wpmucdn.com/voices.uchicago.edu/dist/f/575/files/2020/07/LiqSupply.pdf)

    - Replicate Table 1 and Table 2 
    - Data used: CRSP
    - Some helpful code may be found online: https://voices.uchicago.edu/stefannagel/code-and-data/

9. [Siriwardane, Sunderam, Wallen (2022). Segmented Arbitrage](https://www.nber.org/papers/w30561)

    - Replicate Figure 1 and Table 1
    - Data used: Bloomberg

10. [Bao, Pan, and Wang (2010). The Illiquidity of Corporate Bonds](https://www.mit.edu/~junpan/bond_liquidity.pdf)

    - Replicate Table 1 and Table 2
    - Data used: [FINRA TRACE](https://wrds-www.wharton.upenn.edu/pages/get-data/otc-corporate-bond-and-agency-debt-bond-transaction-data/)
    - Some code is available online. See [here.](https://github.com/Alexander-M-Dickerson/TRACE-corporate-bond-processing/blob/main/TRACE/MakeIlliquidity.py)

11. [Dickerson, Alexander and Robotti, Cesare and Rossetti, Giulio, Noisy Prices and Return-based Anomalies in Corporate Bonds (September 19, 2023)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4575879)

    - Replicate Table 1
    - Data used: [FINRA TRACE](https://wrds-www.wharton.upenn.edu/pages/get-data/otc-corporate-bond-and-agency-debt-bond-transaction-data/)
    - Coda and data is available online: https://openbondassetpricing.com/code/ 
    - Since code and data is available, part of this project is cleaning up the code and making it as presentable and well-documented as possible.

12. [He, Zhiguo, Bryan Kelly, and Asaf Manela. "Intermediary asset pricing: New evidence from many asset classes." Journal of Financial Economics 126, no. 1 (2017): 1-35.](https://zhiguohe.net/wp-content/uploads/2023/12/jfepublishedversion.pdf)

    - Replicate Table 1 (just typeset it in LaTeX), Table A1 (just typeset it in LaTeX), Table 2, and Table 3 (Panel A only, but Panel B for bonus)
    - Data used: CRSP, Compustat, Datastream
    - Some code and data is available online [here](https://zhiguohe.net/publications/research/) and [here](https://zhiguohe.net/data-and-empirical-patterns/intermediary-capital-ratio-and-risk-factor/).

## Data Series from "Evidence from Many Asset Classes"

[He, Kelly, and Manela (2017)](https://zhiguohe.net/wp-content/uploads/2023/12/jfepublishedversion.pdf) above is a  well known paper that examines the effects that intermediaries' balance sheets have on asset prices. This paper happens to test this theory on a variety of asset classes, going beyond just debt and equity. The projects in this section will be to replicate the test asset returns across this variety of asset classes. Each project below focuses on a different asset class. 
The returns of these tests assets are provided [here](https://asafmanela.github.io/papers/hkm/intermediarycapitalrisk/He_Kelly_Manela_Factors.zip). The data provided in that file goes up until 2012. Your project will be to replicate that data up until 2012 and then provide updated returns going as close to the present as possible. The derivation of the returns is defined by a separate paper. These are listed below.


13. [Nozawa, Yoshio. "What Drives the Cross‐Section of Credit Spreads?: A Variance Decomposition Approach." The Journal of Finance 72, no. 5 (2017): 2045-2072.](https://onlinelibrary.wiley.com/doi/epdf/10.1111/jofi.12524)

    - Replicate the corporate bond columns from [He_Kelly_Manela_Factors_And_Test_Assets_monthly.csv](https://asafmanela.github.io/papers/hkm/intermediarycapitalrisk/He_Kelly_Manela_Factors.zip)
    - Data used: [Bond Returns by WRDS](https://wrds-www.wharton.upenn.edu/pages/get-data/wrds-bond-returns/), but maybe also [FINRA TRACE](https://wrds-www.wharton.upenn.edu/pages/get-data/otc-corporate-bond-and-agency-debt-bond-transaction-data/), Mergent FISD/NAIC, TRACE, Lehman Brothers Fixed Income Database.
    - You may use data from [openbondassetpricing.com/](https://openbondassetpricing.com/) and [here](https://github.com/Alexander-M-Dickerson/TRACE-corporate-bond-processing/blob/main/WRDS/MakeCreditSpreads.py) if it's helpful.


14. [Constantinides, George M., Jens Carsten Jackwerth, and Alexi Savov. "The puzzle of index option returns." Review of Asset Pricing Studies 3, no. 2 (2013): 229-257.](https://academic.oup.com/raps/article/3/2/229/1508435)

    - Replicate Table 2 and Table B1. Table 3 or 4 may be difficult, but may be attempted as a stretch goal.
    - Data used: [OptionMetrics](https://wrds-www.wharton.upenn.edu/pages/get-data/optionmetrics/). [CBOE Options data](https://wrds-www.wharton.upenn.edu/pages/get-data/cboe-indexes/) or [Option Suite by WRDS](https://wrds-www.wharton.upenn.edu/pages/get-data/option-suite-wrds/) may be helpful.

15. [Palhares, Diogo. Cash-flow maturity and risk premia in CDS markets. The University of Chicago, 2013.](https://www.proquest.com/docview/1426387803?pq-origsite=gscholar&fromopenview=true&sourcetype=Dissertations%20&%20Theses)

    - Replicate the Credit Default Swap columns from [He_Kelly_Manela_Factors_And_Test_Assets_monthly.csv](https://asafmanela.github.io/papers/hkm/intermediarycapitalrisk/He_Kelly_Manela_Factors.zip)
    - These columns are described in [He, Kelly, and Manela. (2017)](https://zhiguohe.net/wp-content/uploads/2023/12/jfepublishedversion.pdf), but the definition of returns on CDS contracts comes from Palhares (2013).
    - Data used: [Markit](https://wrds-www.wharton.upenn.edu/pages/get-data/markit/)
    
16. [Borri and Verdelhan (2011), "Sovereign Risk Premia"](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=1343746)

    - Replicate Table 1 and the Sovereign Bond Columns from [He_Kelly_Manela_Factors_And_Test_Assets_monthly.csv](https://asafmanela.github.io/papers/hkm/intermediarycapitalrisk/He_Kelly_Manela_Factors.zip)
    - Data used: [Datastream](https://wrds-www.wharton.upenn.edu/pages/get-data/thomson-reuters/datastream/) or Bloomberg

17. [Lettau, Martin, Matteo Maggiori, and Michael Weber. "Conditional risk premia in currency markets and other asset classes." Journal of Financial Economics 114, no. 2 (2014): 197-225.](https://www.sciencedirect.com/science/article/pii/S0304405X14001378)

    - Replicate Table 1 and the first 6 FX columns in [He_Kelly_Manela_Factors_And_Test_Assets_monthly.csv](https://asafmanela.github.io/papers/hkm/intermediarycapitalrisk/He_Kelly_Manela_Factors.zip)
    - Data used: [Datastream](https://wrds-www.wharton.upenn.edu/pages/get-data/thomson-reuters/datastream/) or Bloomberg

18. [Yang, Fan. "Investment shocks and the commodity basis spread." Journal of Financial Economics 110, no. 1 (2013): 164-184.](https://www.sciencedirect.com/science/article/pii/S0304405X13001360?via%3Dihub)

    - Replicate Table 1. It may be difficult to replicate the commodities columns in [He_Kelly_Manela_Factors_And_Test_Assets_monthly.csv](https://asafmanela.github.io/papers/hkm/intermediarycapitalrisk/He_Kelly_Manela_Factors.zip), but you may try.
    - Data used: Futures Contract data from [Datastream](https://wrds-www.wharton.upenn.edu/pages/get-data/thomson-reuters/datastream/futures-data/)


## Other

19. [Monash Time Series Forecasting Archive](https://openreview.net/pdf?id=wEc1mgAjU-)

    - Replicate Table 1 and Table 2
    - Code and data are already available online. (See [here](https://forecastingdata.org/) and [here](https://github.com/rakshitha123/TSForecasting).) This project is to refactor the code of the archive so that it all runs via PyDoit (i.e., the data is automatically downloaded and the tables are all automatically generated).
    - Some prior familiarity with the R programming language would be helpful for this project.

20. **Do short sellers respond to ESG ratings?** (extra credit available)

    - Work with sponsoring adviser to explore the following question: "There has been a recent focus on ESG (Environmental, Social, and Governance) risks in finance, and several papers have studied the relationship between a firm’s ESG rating and its subsequent stock returns. This project aims to study whether short sellers appear to incorporate information in ESG ratings in their investment decisions, which has not been studied. The project will involve merging and analyzing data from 2 main sources: S&P Global / Markit Securities Lending data and RepRisk ESG data."
    - Merge Markit securities lending data with RepRisk Data Feed (Risk Incidents)
    - For each ESG incident/severity/novelty/news’ reach, produce summary statistics of the following variables: short interest ratio (short interest shares / shares outstanding), loan supply ratio (shares available to be lent / shares outstanding), loan utilization, and loan fee.
    - Data used: [Markit securities lending](https://wrds-www.wharton.upenn.edu/pages/get-data/markit/) and [RepRisk](https://wrds-www.wharton.upenn.edu/pages/get-data/reprisk/)

21. [Replicate several portfolios in in Ken French's Data Library](https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html)

    - Reconstruct the "bivariate sorts on size, e/p, cf/p, and d/p". these are the portfolios formed on size and earnings/price, size and cashflow/price, and size and dividend yield. Use the unaggregated CRSP and Compustat data and reconstruct the portfolios that match. 
    - Reconstruct the "bivariate sorts on Operating Profitability and Investment". This consists of three files, each with 25 portfolios in it. Reconstruct these from unaggregated CRSP and Compustat data.
    - Reconstruct each of the "5 industry portfolios" and "49 industry portfolios" from "scratch." That is, use the unaggregated CRSP data and reconstruct the portfolios that match.
    