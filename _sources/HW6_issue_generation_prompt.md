# Prompt for LLM: Generate GitHub Issues for finm Package

## Context

I am creating 60 GitHub issues for a student assignment where each student will contribute one function to an open-source Python package for quantitative finance. The package is located at: https://github.com/jmbejara/finm

Each issue should describe a single function to implement. The function should be:
1. Practically useful in quantitative finance
2. Achievable for a graduate student in 4-8 hours of work
3. Testable with unit tests
4. Well-scoped (not too broad, not too trivial)

## Requirements

Generate 60 issues with the following distribution:

- **30 issues (50%)**: Functions that replicate QuantLib functionality
- **25 issues (42%)**: Functions that replicate Bloomberg Terminal functionality
- **5 issues (8%)**: Data access/utility functions for WRDS or other financial data sources

## Issue Categories and Examples

### Category 1: QuantLib Replications (30 issues)

These should replicate functionality available in QuantLib. Examples:

**Example 1: Black-Scholes Option Pricing**
```
Title: Implement Black-Scholes option pricer for OptionMetrics data

Description:
Create a function that calculates Black-Scholes option prices that can be used with WRDS OptionMetrics data.

Requirements:
- Function signature: `black_scholes_price(S: float, K: float, T: float, r: float, sigma: float, option_type: str) -> float`
- Support both 'call' and 'put' options
- Include input validation (e.g., positive prices, valid option_type)
- Return the theoretical option price

Unit tests should include:
- Known values from QuantLib or other reliable sources
- Both call and put options
- Edge cases (e.g., T=0, at-the-money, deep in/out of money)

References:
- QuantLib: BlackScholesProcess
- Black-Scholes formula: https://en.wikipedia.org/wiki/Black%E2%80%93Scholes_model
```

**Example 2: Bond Pricing with Day Count Conventions**
```
Title: Implement bond price calculator with multiple day count conventions

Description:
Create a function that prices a fixed-rate bond using different day count conventions.

Requirements:
- Function signature: `bond_price(face_value: float, coupon_rate: float, ytm: float, periods: int, day_count: str) -> float`
- Support day count conventions: '30/360', 'ACT/365', 'ACT/360', 'ACT/ACT'
- Calculate present value of cash flows
- Include accrued interest calculation

Unit tests should include:
- Verification against QuantLib bond pricing examples
- Different day count conventions
- Various maturities and coupon frequencies

References:
- QuantLib: FixedRateBond
- Day count conventions: https://en.wikipedia.org/wiki/Day_count_convention
```

### Category 2: Bloomberg Terminal Replications (25 issues)

These should replicate common Bloomberg Terminal functions. Examples:

**Example 1: Implied Repo Rate for Treasury Futures**
```
Title: Calculate implied repo rate for Treasury futures

Description:
Replicate Bloomberg's implied repo rate calculation for Treasury futures contracts.

Requirements:
- Function signature: `implied_repo_rate(futures_price: float, ctd_price: float, ctd_coupon: float, days_to_delivery: int, accrued_interest: float) -> float`
- Calculate the implied financing rate
- Handle conversion factor adjustments
- Return annualized rate

Unit tests should include:
- Known examples from Bloomberg or Treasury market data
- Different time periods
- Various CTD bonds

References:
- Bloomberg function: DLV <GO>
- Treasury futures mechanics documentation
```

**Example 2: Bond Yield-to-Maturity Calculator**
```
Title: Implement yield-to-maturity calculator matching Bloomberg YAS screen

Description:
Calculate bond yield-to-maturity using iterative methods, replicating Bloomberg's YAS screen.

Requirements:
- Function signature: `ytm(price: float, face_value: float, coupon_rate: float, periods_remaining: int, frequency: int = 2) -> float`
- Use Newton-Raphson or bisection method for solving
- Handle semi-annual, quarterly, and annual coupons
- Convergence tolerance of 1e-6

Unit tests should include:
- Comparison with Bloomberg YAS examples
- Par bonds (YTM = coupon rate)
- Premium and discount bonds
- Edge cases (zero-coupon bonds)

References:
- Bloomberg: YAS screen
- Bond mathematics references
```

### Category 3: Data Access Functions (5 issues)

These should facilitate accessing financial data from WRDS or other sources. Examples:

**Example 1: WRDS OptionMetrics Data Fetcher**
```
Title: Create utility function to fetch options data from WRDS OptionMetrics

Description:
Build a convenience function for pulling options data from WRDS that handles authentication and common queries.

Requirements:
- Function signature: `get_options_data(ticker: str, start_date: str, end_date: str, option_type: str = 'both') -> pd.DataFrame`
- Authenticate using .pgpass file (following WRDS best practices)
- Return standardized DataFrame with columns: date, strike, expiration, type, bid, ask, volume, open_interest, impl_volatility
- Handle connection errors gracefully

Unit tests should include:
- Mock WRDS connection for testing without credentials
- Validation of date formats
- Proper DataFrame structure
- Error handling (invalid tickers, connection failures)

References:
- WRDS Python package documentation
- OptionMetrics database schema
```

**Example 2: Treasury Futures CTD Identification**
```
Title: Identify cheapest-to-deliver bond for Treasury futures

Description:
Create a function that identifies the cheapest-to-deliver (CTD) bond from a basket of deliverable securities.

Requirements:
- Function signature: `find_ctd(futures_price: float, deliverable_bonds: pd.DataFrame) -> dict`
- Input DataFrame should contain: cusip, price, coupon, maturity, conversion_factor
- Return dict with CTD cusip and implied repo rate
- Calculate basis (spot - futures × conversion factor) for all bonds

Unit tests should include:
- Mock data representing a delivery basket
- Verification of CTD selection logic
- Edge cases (single deliverable bond, tied basis)

References:
- CME Treasury futures documentation
- CTD selection methodology
```

## Issue Template Format

For each issue you generate, use this structure:

```markdown
**Title:** [Clear, concise title]

**Category:** [QuantLib | Bloomberg | Data Access]

**Difficulty:** [Easy | Medium | Hard]

**Description:**
[2-3 sentences explaining what should be implemented]

**Requirements:**
- Function signature with type hints
- Key functionality points (3-5 bullet points)
- Input validation requirements
- Expected output format

**Unit Test Requirements:**
- [3-5 specific test cases to implement]
- Edge cases to consider
- Validation requirements

**References:**
- [Links to relevant documentation, formulas, or examples]
- [Bloomberg function codes if applicable]
- [QuantLib class/function names if applicable]

**Acceptance Criteria:**
- [ ] Function implemented with proper type hints
- [ ] Docstring with parameter descriptions and examples
- [ ] All unit tests pass
- [ ] Code follows PEP 8 style guidelines
- [ ] No hardcoded values (use parameters)
```

## Additional Guidelines

1. **Avoid duplication**: Each issue should be unique. Don't create multiple issues for the same calculation with minor variations.

2. **Appropriate scope**: Each function should be completable in one PR. Avoid issues requiring multiple interdependent functions.

3. **Real-world relevance**: Functions should be things a quant researcher might actually use.

4. **Testability**: All functions must be deterministic and testable with unit tests.

5. **Difficulty distribution**:
   - 20 issues: Easy (basic calculations, single formulas)
   - 30 issues: Medium (iterative methods, multiple steps)
   - 10 issues: Hard (complex algorithms, multiple interdependencies)

6. **Variety**: Include functions covering:
   - Options (Black-Scholes, binomial trees, Greeks)
   - Fixed income (bonds, duration, convexity, YTM)
   - Derivatives (futures, forwards, swaps)
   - Risk metrics (VaR, volatility, correlation)
   - Portfolio analytics (Sharpe ratio, drawdowns, performance attribution)
   - Market microstructure (VWAP, TWAP, trade classification)

## Your Task

Please generate all 60 issues following the template and guidelines above. Organize them by category and include a variety of difficulty levels and topic areas.

For each issue:
1. Provide a clear title
2. Specify the category and difficulty
3. Write a detailed description
4. List specific requirements with function signature
5. Describe unit test requirements
6. Include relevant references
7. List acceptance criteria

Output the issues in markdown format, numbered sequentially (Issue 1 through Issue 60).
