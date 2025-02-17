# LSEG Datastream

LSEG Datastream is a platform that provides access to a wide range of financial
data, including futures data. Datastream is available via WRDS. WRDS does not
provide real-time data access to Datastream, but it is still a valuable source
of data for research. The Datastream data in WRDS is updated monthly. The data
is the same as the data in LSEG Workspace (e.g., via Eikon).

Let's consider first an example of how to search for Treasury Futures data in
Datastream via WRDS.

To effectively search for Treasury Futures data in Datastream via WRDS, follow
these steps based on the available tools and mnemonic conventions:


## 1. Access Futures Data via WRDS Web Query
WRDS provides a structured interface for retrieving futures data:
- Navigate to the **Thomson/Refinitiv** section in WRDS and select
  **Datastream**.
- Use the **Excel Plugin** (if available) to search for futures series. Check
  the box for *"TS for each item in list"* to retrieve time series for all
  relevant contracts.


## 2. Mnemonic Structure for Treasury Futures

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


## 3. Key Treasury Futures Symbols
Common mnemonics for U.S. Treasury futures include:

| **Contract**               | **Base Symbol** | **Example Continuous Series** | **Example Individual Contracts** |
|-----------------------------|-----------------|-------------------------------|-----------------------------------|
| 2-Year Treasury Note        | `TU`            | `TUCS00`                      | `LFUTTUL`, `LFUTTUD`             |
| 5-Year Treasury Note         | `FV`            | `FVCS00`                      | `LFUTFVL`, `LFUTFVD`             |
| 10-Year Treasury Note        | `TY`            | `TYCS00`                      | `LFUTTYL`, `LFUTTYD`             |
| 30-Year Treasury Bond        | `US`            | `USCS00`                      | `LFUTUSL`, `LFUTUSD`             |


## 4. Search and Browse Tips
- **Use WRDS Economic Indicators Filter:** Narrow results by selecting "Futures"
  under asset classes and filtering by keywords like "Treasury" or
  "Bond".
- **Consult Datastream Documentation:** Access mnemonic lists and data
  dictionaries via WRDS’s *Thomson/Refinitiv* resources.
- **Verify Coverage:** WRDS includes futures data but excludes fixed-income
  modules like bonds. For granular bond futures, consider cross-referencing with
  CRSP’s Treasury data.


## 5. Data Retrieval Example
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
