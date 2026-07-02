# List of Potential Final Projects

The project that you are assigned will come from one of several categories below. Each of these projects involve replicating a well-known finance paper.
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


### 3. [Predictive Regressions: A Present‐Value Approach](https://doi.org/10.1111/j.1540-6261.2010.01575.x)

This paper reframes classic return- and dividend-growth predictability through a present-value model. Instead of running reduced-form predictive regressions, the authors treat expected returns and expected dividend growth as latent AR(1) state variables, tie them to the price–dividend ratio using the Campbell–Shiller log-linear identity, and estimate the state-space system by maximum likelihood / Kalman filtering.

A key practical point is that the measured predictability of dividend growth depends on the dividend reinvestment convention (reinvesting dividends in T-bills vs. in the market). Market-reinvested dividend growth is mechanically much more volatile, which shows up clearly in the summary stats and the time-series plot.

- Task: Replicate Table 1 (dividend-growth summary stats), Table 3 (OLS predictive regressions using the price–dividend ratio), Table 4 (reduced-form specs for market-reinvested dividend growth), and Figure 1 (dividend-growth series under the two reinvestment strategies).
- Update: Extend the sample from the paper’s end date (2007) through the most recent available year and re-run the same four outputs.
- Data sources: CRSP (value-weighted market returns with/without dividends; 30-day T-bills) and (optionally) S&P 500 index levels/returns; construct annual dividends/prices and both reinvestment-based dividend series as in the paper’s data section.
- Citation: Van Binsbergen, Jules H., and Ralph S. J. Koijen. “Predictive Regressions: A Present‐Value Approach.” *The Journal of Finance* 65(4), 2010, 1439–1471.

### 4. **[Holding Period Effects in Dividend Strip Returns](https://academic.oup.com/rfs/article/37/10/3188/7588885)**

Dividend strips isolate claims on future dividends, cleanly separating cash-flow expectations from discount-rate risk. For practitioners, they are useful for hedging or trading long-run cash-flow risk and for forming direct market-based forecasts of dividend growth at different horizons. Academically, dividend strips provide a rare observable object tied closely to present-value relations, making them central to work that decomposes return predictability into cash-flow news versus discount-rate news.

This paper measures dividend strip prices from SPX options via put–call parity using option-implied interest rates.

- Task: Replicate Table 1 (monthly return summary stats) and Figures 1, 2, and 3 (Sharpe ratio vs holding period, market vs strips, etc.)
- Update: Extend the sample from the paper’s end date through the most recent available month and re-run the same table + figure
- Data sources: SPX index options (OptionMetrics IvyDB or CBOE), SPX index levels/returns (CRSP or CBOE), risk-free rate (1M T-bill from FRED/WRDS), Treasury returns (CRSP, if needed for excess-return definitions)
- Citation: Golez, Benjamin, and Jens Jackwerth. "Holding period effects in dividend strip returns." The Review of Financial Studies 37, no. 10 (2024): 3188-3215.

## AI and Quantitative Finance

### 5. [Can ChatGPT Forecast Stock Price Movements? Return Predictability and Large Language Models](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4412788)

This paper demonstrates the capability of large language models (LLMs) like ChatGPT to predict stock market reactions from news headlines. See the abstract:

> We document the capability of large language models (LLMs) like ChatGPT to predict stock market reactions from news headlines without direct financial training. Using postknowledge-cutoff headlines, GPT-4 captures initial market responses, achieving approximately 90% portfolio-day hit rates for the non-tradable initial reaction. GPT-4 scores also significantly predict the subsequent drift, especially for small stocks and negative news. Forecasting ability generally increases with model size, suggesting that financial reasoning is an emerging capacity of complex LLMs. Strategy returns decline as LLM adoption rises, consistent with improved price efficiency. To rationalize these findings, we develop a theoretical model that incorporates LLM technology, information-processing capacity constraints, underreaction, and limits to arbitrage.

Also, from their paper,

> "Our key finding is that GPT-4 demonstrates a strong ability to predict the immediate market reaction to news headlines, achieving daily portfolio hit rates of approximately 90% for correctly identifying the direction of the initial price response. This result is notable for two reasons. First, it is not obvious that a general-purpose language model trained without explicit financial supervision should excel at this task. The fact that it does suggests that sophisticated financial reasoning—understanding not just whether news is positive or negative, but also how markets will interpret it—emerges naturally from the model’s general language training."

- Task: Replicate Table 1 (Hit Rates) and Table 5 (Long-Short Strategy Returns)
- Data sources: CRSP, RavenPack (or similar news data), and ChatGPT API
- Since the ChatGPT API is not free, I will provide you with API credits to use for this project so that you don't have to pay for it yourself.
- Citation: Lopez-Lira, Alejandro and Tang, Yuehua, Can ChatGPT Forecast Stock Price Movements? Return Predictability and Large Language Models (2023). Available at SSRN: https://ssrn.com/abstract=4412788

### 6. [The Structure of Economic News: Business News and Business Cycles](https://onlinelibrary.wiley.com/doi/full/10.1111/jofi.13377)

This project studies how textual analysis of business news can be used to measure the state of the economy. The paper constructs topic-level time series from Wall Street Journal articles and shows that attention to specific news topics closely tracks and predicts standard macroeconomic indicators.

Students will download pre-constructed topic attention time series directly from https://structureofnews.com/, avoiding the need to estimate topic models themselves. The task is to replicate one core table and one core figure linking news attention to macroeconomic outcomes, and then update the analysis through the present.

- **Tasks**:
  - **Replicate Table 1 (macroeconomic reconstruction)**: regress industrial production growth and employment growth on selected news topic attention series using lasso or a fixed-topic specification
  - **Replicate Figure 3 (topic attention over time)**: plot monthly attention shares for key topics (e.g., “Recession,” “Federal Reserve,” “Earnings”) and compare them to related macroeconomic time series

- **Primary paper**:
  - Bybee, Leland, Bryan Kelly, Asaf Manela, and Dacheng Xiu. "Business news and business cycles." The Journal of Finance 79, no. 5 (2024): 3105-3147. https://onlinelibrary.wiley.com/doi/full/10.1111/jofi.13377 (use this, the published version for the replication exercise above)

- **Data sources**:
  - News topic attention time series from https://structureofnews.com/
  - Macroeconomic data from FRED (industrial production, employment) or WRDS

- **Notes**:
  - Students do **not** need to re-estimate the topic model. Just use the data from https://structureofnews.com/.
  - The focus is on interpreting news-based state variables and their relationship to standard macroeconomic indicators.


## Institutional Monitoring

### 7. [Intermediary Asset Pricing: New Evidence from Many Asset Classes](https://zhiguohe.net/wp-content/uploads/2023/12/jfepublishedversion.pdf)

This project will give you experience in analyzing the balance sheet fundamentals of large broker-dealers, in this case the full set of primary dealers in the US, and how the financial condition of these primary dealers affect the US stock market as a whole.

 - Task: Replicate Table 2, and Table 3 (Panel A and Panel B)
 - Data used: CRSP, Compustat, Datastream
 - Some code and data is available online [here](https://zhiguohe.net/publications/research/) and [here](https://zhiguohe.net/data-and-empirical-patterns/intermediary-capital-ratio-and-risk-factor/).
 - Citation: He, Zhiguo, Bryan Kelly, and Asaf Manela. "Intermediary asset pricing: New evidence from many asset classes." Journal of Financial Economics 126, no. 1 (2017): 1-35.
 - Note: I will provide some code that will help you get started.


### 8. [Monetary Tightening and US Bank Fragility in 2023](https://www.nber.org/papers/w31048)

This paper will teach you how to use bank call reports to construct measures of the financial condition of banks. This is especially useful if you have interest in specializing, for example, in specializing in equities covering the financial sector.

 - Task: Replicate Table 1, Table A1 and Figure A1 and update the numbers through 2025. To do this, you will have to scrape data from FFIEC's website.
 - Data sources: Bank Call Reports. See https://wrds-www.wharton.upenn.edu/pages/get-data/bank-regulatory/
 - Notes: I will actually provide you with code to replicate the tables and figures from the paper, using data from WRDS. The problem is that the data from WRDS is only updated with a lag of nearly a year and a half. So, in order to get more "real-time" data, you will have to scrape data from FFIEC's website. Therefore, this exercise will give you experience with web scraping and data cleaning in order to produce more of a real-time monitor.

Paper:
  - Jiang, Erica Xuewei, Gregor Matvos, Tomasz Piskorski, and Amit Seru. "Monetary tightening and US bank fragility in 2023: Mark-to-market losses and uninsured depositor runs?." Journal of Financial Economics 159 (2024): 103899. https://doi.org/10.1016/j.jfineco.2024.103899 
  - Jiang, Erica Xuewei, Gregor Matvos, Tomasz Piskorski, and Amit Seru. "Monetary Tightening and US Bank Fragility in 2023: Mark-to-Market Losses and Uninsured Depositor Runs?." NBER Working Paper w31048 (2023). **Use this, the working paper version for the replication exercise above**


### 9. [Exchange Rates and Asset Prices in a Global Demand System](https://www.nber.org/papers/w27342)

Understanding how global capital flows affect exchange rates, interest rates, and equity valuations is one of the most important questions in international finance. This paper develops an asset demand system that connects international portfolio holdings across 37 countries and three asset classes (short-term debt, long-term debt, and equity) to equilibrium prices. The authors estimate demand elasticities that quantify how sensitive investors are to price changes, decompose exchange rate and asset price movements into portfolio flows versus shifts in investor demand, and estimate the "convenience yield" that US assets enjoy due to the dollar's reserve currency status.

This project gives students hands-on experience working with international portfolio holdings data from the IMF Coordinated Portfolio Investment Survey, constructing cross-country asset market data, and understanding the mechanics of demand-based asset pricing. The replication involves merging multiple public datasets (IMF, OECD, BIS, World Bank) and implementing the authors' methodology for restating holdings from residency to nationality accounting. Students will gain practical skills in international finance data construction that are directly applicable to roles in global macro investing, central bank research, and international policy analysis.

- **Task**: Replicate Tables 1 and 2 and Figures 1 and 2
- **Data sources**: IMF Coordinated Portfolio Investment Survey, OECD Financial Accounts, BIS Debt Securities Statistics, World Bank, Datastream, MSCI Country Indexes (Bloomberg), Global Capital Allocation Project
- **Citation**: Koijen, Ralph S.J. and Motohiro Yogo. "Exchange Rates and Asset Prices in a Global Demand System." NBER Working Paper No. 27342.

## Arbitrage Spreads

### 10. [Segmented Arbitrage: Treasury Spot-Futures](https://www.hbs.edu/ris/Publication%20Files/24-030_1506d32b-3190-4144-8c75-a2326b87f81e.pdf)

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


### 11. **Treasury Cash–Futures Basis with Implied Repo and Delivery Option Adjustment**

This project studies the Treasury cash–futures basis using a simplified replication of the methodology in a Federal Reserve FEDS Note. Students construct the basis from first principles using Treasury futures prices and publicly available cash Treasury and repo data, rather than relying on proprietary Bloomberg implied repo series.

The focus is on computing the **implied repo rate**, comparing it to observed financing rates, and understanding how **delivery options** embedded in Treasury futures affect the measured basis.

* **Tasks**:

  * Compute the implied repo rate for a Treasury futures contract using the cheapest-to-deliver bond and optimal delivery date.
  * Construct the Treasury cash–futures basis as implied repo minus a repo financing rate (SOFR or GC proxy).
  * Estimate a simplified delivery option value using futures volatility and CTD-switch risk, and compute an option-adjusted basis.
  * Replicate Figure 1 from the paper (https://www.federalreserve.gov/econres/notes/feds-notes/quantifying-treasury-cash-futures-basis-trades-20240308.html)
  * **Primary paper**: Glicoes, Anthony. *Quantifying Treasury Cash–Futures Basis Trades*. FEDS Notes, 2024.
    https://www.federalreserve.gov/econres/notes/feds-notes/quantifying-treasury-cash-futures-basis-trades-20240308.html

  * **Data sources**: CME Treasury futures info from Bloomberg, Treasury cash prices and characteristics (CRSP or TreasuryDirect), Repo proxy (SOFR from FRED)


### 12. [Segmented Arbitrage: Corporate CDS-Bond Basis](https://www.hbs.edu/ris/Publication%20Files/24-030_1506d32b-3190-4144-8c75-a2326b87f81e.pdf)

This project replicates the corporate CDS-bond basis from the paper "Segmented Arbitrage" by Emil Siriwardane, Adi Sunderam, and Jonathan Wallen. The paper examines various arbitrage trades and observes that the price dynamics of these trades challenge asset pricing models that have been used in the past to explain deviations from no-arbitrage.

The CDS-bond basis represents the difference between the credit spread implied by a corporate bond and the premium on a credit default swap (CDS) referencing the same issuer. In theory, these two measures of credit risk should be equal; deviations create arbitrage opportunities where traders can profit by buying the cheaper instrument and selling the more expensive one.

From the [internet appendix](https://www.emilsiriwardane.com/s/Appendix.pdf):

> "The CDS-bond basis is measured as the difference between the CDS spread and the credit spread on a corporate bond. The credit spread on a bond is typically calculated as the bond's yield minus a risk-free benchmark rate, often interpolated from the Treasury or swap curve to match the bond's maturity."

 - Task: Replicate the CDS-bond basis spread construction. Your numbers should match the `final_cds_bases.xlsx` file in the author's repository nearly precisely: https://github.com/esiriwardane/arbitrage-spreads-public/tree/main/raw
 - Data sources: Markit CDS (credit default swap data), Corporate TRACE (corporate bond transaction data)
 - Code and data: One of the authors, [Emil Siriwardane](https://www.emilsiriwardane.com/), makes code and data available online: https://github.com/esiriwardane/arbitrage-spreads-public
 - Additional resources: I will provide you with code that will help get you most of the way there.
 - Citation: Siriwardane, Emil N., Adi Sunderam, and Jonathan L. Wallen. "Segmented Arbitrage." Harvard Business School Working Paper, No. 24-030, November 2023.
 - Note: Extra credit available if this project is chosen.

### 13. [The CDS-Bond Basis via Bai and Collin-Dufresne (2019)](https://onlinelibrary.wiley.com/doi/10.1111/fima.12252)

This project studies deviations from the arbitrage relation between corporate bond spreads and credit default swap (CDS) spreads. The CDS–bond basis—the difference between CDS spreads and bond-implied credit spreads—became large and negative during the Global Financial Crisis and remains persistently nonzero afterward. The paper argues that these deviations reflect limits to arbitrage rather than mispricing.

Students will use WRDS data to construct CDS–bond bases at daily frequency and replicate one core table and one core figure documenting the time-series and cross-sectional behavior of the basis.

- **Tasks**:
  - **Replicate Table 1 (summary statistics)**: compute summary statistics of the CDS–bond basis across subperiods (pre-crisis, crisis, post-crisis) and credit rating categories
  - **Replicate Figure 1 (basis dynamics by rating)**: plot the time series of the median CDS–bond basis for investment-grade and high-yield firms
  - **Update** both the table and the figure by extending the sample from the paper’s end date through the present

- **Primary paper**:
  - Bai, Jennie, and Pierre Collin‐Dufresne. "The CDS‐bond basis." Financial Management 48, no. 2 (2019): 417-439.

- **Data sources (WRDS)**:
  - LSEG / Markit CDS spreads
  - TRACE corporate bond transactions
  - Mergent Fixed Income (bond characteristics)
  - CRSP (for firm identifiers and equity data, as needed)

- **Notes**:
  - Students do not need to replicate the full structural PECDS model.
  - The focus is on measurement, aggregation, and interpretation of the CDS–bond basis.



## Fixed Income

### 14. [The U.S. Treasury Yield Curve: Construction and Model Comparison](https://www.ecb.europa.eu/pub/pdf/scpsps/ecb.sps27.en.pdf)

This project studies how the U.S. Treasury yield curve is constructed and how different modeling choices affect its shape and interpretation. Students will be given working code that reproduces the Gurkaynak–Sack–Wright (GSW) zero-coupon Treasury yield curve, which is widely used in academic and policy work. The GSW curve is based on the Nelson–Siegel–Svensson parametric framework.

The main task is to extend the provided code by estimating and comparing alternative yield-curve methodologies surveyed in Nymand-Andersen (2018), including spline-based and arbitrage-free approaches used by central banks.

- **Tasks**:
  - Run provided code to reproduce the GSW (Nelson–Siegel–Svensson) U.S. Treasury yield curve
  - Implement and estimate the following yield-curve models:
    - Nelson–Siegel–Svensson (baseline, from GSW)
    - Waggoner-style cubic spline with roughness penalty
    - An arbitrage-free affine term structure model (e.g., Vasicek or Hull–White)
  - Compare models in terms of fit, smoothness, and behavior across maturities

- **Primary papers**:
  - Gürkaynak, Refet S., Brian Sack, and Jonathan H. Wright. *The U.S. Treasury Yield Curve: 1961 to the Present*. Journal of Monetary Economics, 2007.
  - Nymand-Andersen, Per. *Yield Curve Modelling and a Conceptual Framework for Estimating Yield Curves: Evidence from the European Central Bank’s Yield Curves*. ECB Statistics Paper No. 27, 2018.


### 15. [The On-the-Run Liquidity Premium in U.S. Treasuries](https://www.sciencedirect.com/science/article/abs/pii/S0304405X08002080?via%3Dihub)

This project studies pricing and liquidity differences between on-the-run and off-the-run U.S. Treasury securities. On-the-run Treasuries—those most recently issued—trade at higher prices and lower bid–ask spreads than otherwise similar off-the-run securities. Using end-of-day Treasury quotes, this project measures the on-the-run premium and examines how it varies over the auction cycle and around major announcements.

Students will be given starter code that identifies on-the-run and just off-the-run Treasuries using CRSP. The main task is to replicate selected core results from the paper at daily frequency and then update them through the present.

- **Tasks**:
  - **Replicate Table 1 (summary statistics)**: compare on-the-run and off-the-run Treasuries in terms of yields and bid–ask spreads using CRSP end-of-day bid and ask quotes
  - **Replicate Table 3 (daily regressions)**: estimate regressions of on-the-run minus off-the-run yield and bid–ask spread premia on auction-cycle indicators and macro announcement dummies, using daily data
  - **Replicate Figure 2 (auction-cycle dynamics)**: plot the average on-the-run premium as a function of days since auction
  - **Update** all results by extending the sample from the paper’s end date to the present

- **Primary paper**:
  - Pasquariello, Paolo, and Clara Vega. "The on-the-run liquidity phenomenon." Journal of Financial Economics 92, no. 1 (2009): 1-24.

- **Notes**:
  - All liquidity measures are based on **end-of-day** CRSP bid and ask quotes rather than intraday data.
  - The focus is on **pricing premia and their dynamics**, not structural microstructure estimation.


## Other


### 16. [An Anatomy of Commodity Futures Risk Premia](https://doi.org/10.1111/jofi.12096)

This paper decomposes commodity futures returns into spot premia (related to underlying commodity risk) and term premia (related to changes in the basis). Using 21 commodity futures markets, the authors show that sorting on variables like the futures basis, momentum, volatility, and inflation beta produces spot premia of 5–14% per annum and term premia of 1–3% per annum. A key finding is that a single high-minus-low basis factor explains the cross-section of spot premia, while two additional basis factors are needed for term premia. This is a great project for students interested in commodity trading and learning how the commodity futures market works.

- Task: Replicate Table 1 (summary statistics for sector indices showing Short Roll and Excess Holding returns across maturities) and Table 2 (mean returns when futures are sorted on the basis, including high-minus-low spreads)
- Data sources: Commodity Research Bureau (CRB) futures data, CFTC Commitment of Traders reports, FRED
- Citation: Szymanowska, Marta, Frans De Roon, Theo Nijman, and Rob Van Den Goorbergh. "An anatomy of commodity futures risk premia." The Journal of Finance 69, no. 1 (2014): 453-482.


### 17. [Expected Returns and Large Language Models](https://ssrn.com/abstract=4416687)

(_This project was added after assignments. I've added it here so as not to throw off the numbering of the other projects_)

This paper investigates the predictive power of Large Language Models (LLMs) on stock returns. Unlike traditional "bag-of-words" approaches that ignore word order, LLMs capture context and nuance (such as negation) to extract richer information from news text. The authors find that embeddings from models like BERT and ChatGPT significantly improve return prediction accuracy compared to simpler NLP methods.

See the abstract:

> "We leverage state-of-the-art large language models (LLMs) such as ChatGPT and LLaMA to extract contextualized representations of news text for predicting stock returns. Our results show that prices respond slowly to news reports indicative of market inefficiencies and limits-to-arbitrage. Predictions from LLM embeddings significantly improve over leading technical signals (such as past returns) or simpler NLP methods by understanding news text in light of the broader article context."

Also, from the paper:

> "The main benefit of an LLM... is that it provides more sophisticated and well-trained text representations than used in the literature referenced above. This benefit comes from the expressivity of massive nonlinear model parameterizations and from training on extensive language examples across many domains and from throughout human history."

* **Tasks**: For this paper, you will not have access to the same dataset that the authors have. So, instead, we will use something somewhat similar: RavenPack via WRDS. RavenPack is a dataset of news headlines, along with a lot of other metadata associated with the articles (such as linking the articles to stock tickers). So, simply replicate their methods but using the RavenPack News Headlines. Replicate Tables 1, 2, 3, and 5 but with headlines from RavenPack. Since the authors use many models, it will help to simplify. Just use BERT and "text-embedding-3-large" from OpenAI (ChatGPT).
* **Data sources**:
    * **RavenPack** (via WRDS): Use RavenPack data for news headlines. While the paper uses full article text from Thomson Reuters, you will use only the headlines provided by RavenPack. RavenPack also includes Entity Mapping (tickers) which you should use to link news to stock returns.
    * **CRSP**: For stock returns.
* **Notes**:
    * Since the ChatGPT API is not free, I will provide you with API credits to use for this project so that you don't have to pay for it yourself.
    * Focus on the "Headline" analysis since RavenPack data is primarily headline-based.
* **Citation**: Chen, Yifei, Bryan T. Kelly, and Dacheng Xiu. "Expected Returns and Large Language Models." (November 22, 2022). Available at SSRN: [https://ssrn.com/abstract=4416687](https://ssrn.com/abstract=4416687)