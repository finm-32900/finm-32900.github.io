# Case Study: Atlanta Fed Wage Growth Tracker

## Introduction

Wages at the aggregate level have been found to rise during the last two recessions (or at least not decline). This is surprising given that aggregate labor conditions were so weak. Many economists have viewed this as a puzzle. The goal in this question is to assess whether this is a puzzle, given that the composition of workers are changing over time. We begin by establishing the facts from which this puzzle arises.  For now, let's focus on the Great Recession. We'll then discuss the Covid-19 recession afterwards.

The great recession is generally defined as having lasted from December 2007 to June 2009. For example, see the corresponding article on Wikipedia: https://en.wikipedia.org/wiki/Great_Recession_in_the_United_States

> The Great Recession in the United States was a severe financial crisis combined with a deep recession. While the recession officially lasted from December 2007 to June 2009, it took several years for the economy to recover to pre-crisis levels of employment and output.


Consider the following graph. This graph plots the median weekly real earnings for wage and salary workers ages 16 years and older. The shaded areas in the plots denote officially defined periods of recession, as defined by NBER. Notice that wages during the period of the great recession appear to be increasing. In this document we will be investigating this fact.

![Median Real Earnings](./assets/median_real_earnings_FRED.png)

## Demographic data from US Current Population Survey

To study this puzzling fact, we will analyze how changing demographics might affect our aggregate measures of wages. One of our biggest concerns is that as employment rates fell, they fell more for low educated workers than high educated workers. That means the average wages we are measuring will actually be comparing different types of workers in 2010 relative to 2006. This could potentially explain why wages are rising. We will attempt to compensate for this by constructing a demographically adjusted time series for wages. 

### Game Plan

Here is a summary of what we will do. I will give you more specific instructions afterwards to walk you through this.

Use data from the 2000-2017 March CPS (downloaded from IPUMS CPS web site) to examine the time series (annual) trend in both nominal and real wages for 25-54 year old men not living in group quarters. (We do this to keep things simple for now.)  (FYI, You need to download the group quarters variable).  Wages will be defined as annual earnings (last year) divided by annual hours (last year).  Annual hours can be computed by multiplying weeks worked last year by usual hours worked (last year). You should do this for a sample of all workers with a positive wage last year. Typically, you can convert to real wages using any deflator you wish. Here, I will require using the CPI99 variable to convert to 1999 dollars. (Note: Many economists like to use the June CPI-U. June is in the middle of the year and, for that reason, avoids some issues with seasonality. The choice of year doesn't matter.)

#### Note about ASEC

Be sure to download **only** the ASEC samples. The ASEC supplement *is* the March CPS. The ASEC includes extra variables that are not included in the basic monthly CPS survey. From [Wikipedia, the ASEC is described as the following:](https://en.wikipedia.org/wiki/Current_Population_Survey#CPS_Annual_Social_and_Economic_Supplement_(ASEC)-_the_March_Supplement),

> Since 1948, the CPS has included supplemental questions (at first, in April; later, in March) on income received in the previous calendar year, which are used to estimate the data on income and work experience. These data are the source of the annual Census Bureau report on income, poverty, and health insurance coverage...

Downloading the March samples from the "Basic Monthly" samples doesn't give us what we need. See the included screenshot. The arrow points out the fact that these variables are missing in the March basic monthly samples but are available in the ASEC samples.

![asec_v_basic_monthly](./assets/ipums_cps_query_form.png)

## An update for the Covid-19 Recession

See here: https://www.stlouisfed.org/on-the-economy/2022/feb/relationship-wage-growth-inflation-one-recession-later

## Atlanta Wage Growth Tracker

See here: https://www.atlantafed.org/chcs/wage-growth-tracker.aspx?panel=1

