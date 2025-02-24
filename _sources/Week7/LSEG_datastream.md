# LSEG Datastream

LSEG Datastream is a platform that provides access to a wide range of financial
data, including futures data. Datastream is available via WRDS. WRDS does not
provide real-time data access to Datastream, but it is still a valuable source
of data for research. The Datastream data in WRDS is updated monthly. The data
is the same as the data in LSEG Workspace (e.g., via Eikon).

## Getting Started with Documentation

Before searching for specific data, it's recommended to familiarize yourself with
Datastream's documentation:

1. Visit the [WRDS Datastream Documentation Page](https://wrds-www.wharton.upenn.edu/pages/support/manuals-and-overviews/thomson-reuters/datastream/)
2. Log in with your WRDS credentials
3. Review the available manuals and overviews to understand:
   - Data coverage and limitations
   - Search functionality
   - Available data types and formats
   - Mnemonic conventions

This documentation will help you navigate the platform more effectively and
understand the data structure before proceeding with specific queries.

## Finding Variables (in Datastream and in WRDS generally)

WRDS provides a powerful variable search tool that allows you to search across all WRDS datasets, including Datastream. This can be particularly helpful when:
- You're unsure which dataset contains your variable of interest
- You want to compare similar variables across different datasets
- You need to find specific mnemonics or variable names

### Using the WRDS Variable Search

1. Navigate to the [WRDS Variable Search Page](https://wrds-www.wharton.upenn.edu/search/?queryTerms=&activeTab=navVariablesSearchTab)
2. Log in with your WRDS credentials
3. Use the search functionality in several ways:
   - Search by keyword (e.g., "treasury futures")
   - Filter by database (e.g., "Datastream")
   - Browse by category
   - Use advanced search options for more specific queries

### Search Tips
- Use quotation marks for exact phrase matches
- Try different variations of terms (e.g., "Treasury", "T-Note", "Government Bond")
- Check variable definitions carefully as similar variables may exist across different datasets
- Note the update frequency and coverage period for each variable

The variable search tool is particularly valuable when working with Datastream, as it can help you identify the correct mnemonics and understand what data is available before constructing your queries.

## Treasury Futures Example 1

Search https://wrds-www.wharton.upenn.edu/dynamic-query-form/tr_ds_fut/wrds_cseries_info/

## Treasury Futures Example 2

Let's consider first an example of how to search for Treasury Futures data in
Datastream via WRDS.

To effectively search for Treasury Futures data in Datastream via WRDS, follow
these steps based on the available tools and mnemonic conventions:


### 1. Access Futures Data via WRDS Web Query
WRDS provides a structured interface for retrieving futures data:
- Navigate to the **Thomson/Refinitiv** section in WRDS and select
  **Datastream**.


### 2. Mnemonic Structure for Treasury Futures

Datastream uses standardized codes for futures contracts:
- **Continuous series (front contract):**  
  Format: `[Symbol]CS00`  
  Example: `TYCS00` for 10-Year Treasury Note futures (where `TY` represents the
  underlying asset).
  - `CS` indicates "continuous series" (auto-rolls to the next contract at
    expiration).
  - `00` specifies the rollover timing (1st day of the new month).

- **Individual contracts (live or expired):**  
  Format: `LFUT[Symbol][L/D]`  
  Example: `LFUTTYL` for live 10-Year Treasury contracts or `LFUTTYD` for dead
  (expired) ones.
  - `LFUT` = List Futures  
  - `L` = Live, `D` = Dead  


### 3. Key Treasury Futures Symbols
Common mnemonics for U.S. Treasury futures include:

| **Contract**               | **Base Symbol** | **Example Continuous Series** | **Example Individual Contracts** |
|-----------------------------|-----------------|-------------------------------|-----------------------------------|
| 2-Year Treasury Note        | `TU`            | `TUCS00`                      | `LFUTTUL`, `LFUTTUD`             |
| 5-Year Treasury Note         | `FV`            | `FVCS00`                      | `LFUTFVL`, `LFUTFVD`             |
| 10-Year Treasury Note        | `TY`            | `TYCS00`                      | `LFUTTYL`, `LFUTTYD`             |
| 30-Year Treasury Bond        | `US`            | `USCS00`                      | `LFUTUSL`, `LFUTUSD`             |


### 4. Search and Browse Tips
- **Use WRDS Economic Indicators Filter:** Narrow results by selecting "Futures"
  under asset classes and filtering by keywords like "Treasury" or
  "Bond".
- **Consult Datastream Documentation:** Access mnemonic lists and data
  dictionaries via WRDS's *Thomson/Refinitiv* resources.
- **Verify Coverage:** WRDS includes futures data but excludes fixed-income
  modules like bonds. For granular bond futures, consider cross-referencing with
  CRSP's Treasury data.


### 5. Data Retrieval Example
To download 10-Year Treasury Note futures:
1. **Continuous series:** Use `TYCS00` for auto-rolling front-month data.
2. **Individual contracts:** Use `LFUTTYL` to retrieve all live contracts or
   `LFUTTYD` for expired ones.
3. **Export Options:** Output data in `.csv`, `.xlsx`, or SAS formats via WRDS
   web queries.


## Key Limitations
- WRDS updates Datastream data **monthly**, while LSEG Workspace offers
  real-time updates.
- For intraday data or non-U.S. Treasury futures, use LSEG Workspace (access
  varies by institution).

By applying these conventions and tools, you can efficiently locate and extract
Treasury Futures data in Datastream via WRDS.
