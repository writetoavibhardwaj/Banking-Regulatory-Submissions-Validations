# Banking-Regulatory-Submissions-Validations

An **Excel Office 365** Power Query–based solution for importing, processing, and validating **financial, regulatory, and liquidity submissions** from the **Prudential Regulation Authority (PRA)** and the **European Banking Authority (EBA)**.
The solution supports multiple formats and validates submissions against **internal company rules** as well as **mandated regulatory requirements**.

---

## Project Overview

This project addresses two main technical challenges:

### 1. **Diverse and Numerous Data Sources**

We had to handle \~100 different input sources, including:

* **FINREP submissions** (Balance Sheet, Profit & Loss, Assets, Liabilities, Other Comprehensive Income, disclosures by product, counterparty, and instrument)
* **Liquidity submissions** such as:

  * LCR (Liquidity Coverage Ratio)
  * NSFR (Net Stable Funding Ratio)
  * PRA110
  * Additional Monitoring Metrics (AMM)
* **COREP disclosures** including:

  * Own Funds (Capital)
  * **C 47.00** – Leverage Ratio
  * Large Exposures
  * **C 07.00** – Credit & Counterparty Credit Risk
  * **C 18.00** – Market Risk
  * **C 17.00** – Operational Risk

The goal was to **design one unified Power Query process** capable of importing all this data seamlessly.

---

### 2. **Extensive Power Query Function Library**

We built a modular set of functions and sub-functions to process and validate data.
Below are examples from the **20 custom functions** developed:

* **`udf_GetNumericElements`**
  *Extracts only numeric elements from a list.*
  Example:
  Input → `{ "0","0","1","0","0","0","2","0","A","B" }`
  Output → `{ "0", "0", "1", "0", "0", "0", "2", "0", "2" }`

* **`udf_ReplaceColumnsWith0`**
  *Takes a table and a list of columns, replaces all missing/null values in those columns with 0.*

* **`udf_UnpivotDigitNamedColumns`**
  *Unpivots all digit-named columns (e.g., 0010, 0020) into two columns: `Col` and `Value`.*

* **`udf_MultipleReplacements`**
  *Performs bulk string replacements based on two lists (`from` and `to`), often used to replace references in validation formulas and evaluate pass/fail status.*

* **`udf_DropFirstNColumnsOfTable`**
  *Drops the first N blank columns from a table.*

* **`udf_AddColumnsInTableIfMissing`**
  *Adds mandatory columns to a table if they are missing.*

* **`udf_TransformFile`**
  *Automatically processes multiple files and sheets in a folder.*

---

## Non-Technical Challenge

An equally critical aspect was **gaining deep process knowledge** from Subject Matter Experts (SMEs) with domain expertise.
This understanding allowed us to:

* Interpret regulatory requirements correctly.
* Build validation rules that reflect both **regulatory intent** and **business context**.
* Create a holistic, automated reporting solution.
