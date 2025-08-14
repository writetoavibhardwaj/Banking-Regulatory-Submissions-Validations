# Banking-Regulatory-Submissions-Validations
An Excel Office 365–based Power Query solution for importing and processing financial, regulatory, and liquidity submissions from the PRA and EBA in various formats, and validating them against internal and mandated regulatory rules.
Main technical challanges in this project was two fold:
- there were around 100 input sources e.g. finrep submissions including balance sheet, profit and loss, assets, liabilities, other comprehensive income, other disclosured by product, counterparty and instrument, liquidity submissions like LCR, NSFR, PRA110 and other additional monitering metrics (AMM) and different corep disclosures like Own Funds (Capital), C 47.00 – Leverage ratio, Large Exposures, C 07.00 – Credit and counterparty credit risk, C 18.00 – Market risk, C 17.00 – Operational risk etc. We needed to design one power query using which all data can be imported
- We designed lot of functions and sub functions in power query to achieve the objective i.e.
- Functions [20]

fx  udf_GetNumericElements
     // Function: GetNumericElements
    // Usage: GetNumericElements({"0","0","1","0","0","0","2","0","A","B"})
    // Result: { "0", "0", "1", "0", "0", "0", "2", "0", "2" }

fx  udf_ReplaceColumnsWith0
     Take a table and a list of columns as argument and return a table replace all missing or null values with 0

fx  udf_UnpivotDigitNamedColumns
     Take a table and optional 2 column names for unpivoting all numeric columns e.g. 0010, 0020 etc and naming them Col and Value and returning a table

fx  udf_MultipleReplacements
     This function takes a string and two lists (one from and second to) and carries a replacement in loop and then returns a string after replacement. essentially replacing all references in formula validation with values, evaluating it and returning true or false i.e. weather validation passes or fails

fx  udf_DropFirstNColumnsOfTable
     Function to drop blank columns in a table

fx  udf_AddColumnsInTableIfMissing
     Bring mandatory columns in a table, in case they are missing

fx  udf_TransformFile
     Self generated for pulling data from multiple files and sheets in a folder

