
                    ********************** Financial Transaction Reconciliation Engine ************************************
                    
🔍 Project Overview
This project automates the reconciliation process between a company's cashbook and bank statement using Python and Pandas.
The reconciliation engine compares financial transactions recorded in two independent ledgers 

Objective

Compare:
📒 Cashbook Ledger
🏦 Bank Ledger

and identifies:
✅ Matched transactions
✅ Transactions present only in the bank statement
✅ Transactions present only in the cashbook
✅ Reconciliation statistics

The solution replicates a real-world Bank Reconciliation Statement (BRS) process commonly performed by finance and accounting teams.
________________________________________

🔍 Business Problem

Organizations maintain two separate records of financial transactions:

1.	Company Cashbook
2.	Bank Statement

Due to timing differences, bank charges, direct debits, delayed cheque clearances, or missing entries, the two ledgers often do not match.

Manual reconciliation is time-consuming and error-prone.

This project automates the identification of:
•	Reconciled transactions
•	Outstanding transactions
•	Missing entries
•	Reconciliation summaries
________________________________________

🔍 Dataset

Dataset: Financial Transaction Records – Dual Ledger Dataset(Kaggle)

Sheets:
•	CashBook
•	Bank Statement

Key fields:
•	Transaction Date
•	Description
•	Credit
•	Debit
•	Balance
•	Currency
________________________________________

🔍Technologies Used
•	Python
•	Pandas
•	OpenPyXL
•	Jupyter Notebook
________________________________________

🔍 Reconciliation Logic
The reconciliation process follows these steps:

1. Data Cleaning
•	Convert dates into datetime format
•	Convert debit and credit columns to numeric values
•	Standardize transaction descriptions
•	Remove invalid values

2. Transaction Matching
   
Transactions are matched using:
•	Transaction Date
•	Description
•	Credit Amount
•	Debit Amount

A full outer join is performed using Pandas.
pd.merge(
    bank_stmt,
    cashbook,
    on=[
        "Transaction Date",
        "Description",
        "Credit",
        "Debit"
    ],
    how="outer",
    indicator=True
)
________________________________________

🔍 Understanding the Output

📌 Matched Transactions
Transactions found in both the Cashbook and Bank Statement.
These transactions are considered reconciled.
________________________________________

📌 W-1: Bank → Cashbook
Transactions that appear in the Bank Statement but do not exist in the Cashbook.
Examples:
•	Bank charges
•	Interest income
•	Direct debits
•	Automatic deductions
________________________________________

📌W-2: Cashbook → Bank
Transactions that appear in the Cashbook but not in the Bank Statement.
Examples:
•	Outstanding cheques
•	Deposits in transit
•	Delayed bank processing
________________________________________

🔍 Output Files
The solution generates the following sheets:

Sheet Name	                   Description
Matched	                Reconciled transactions
W1 Bank Only	          Transactions found only in bank records
W2 Cashbook Only	      Transactions found only in cashbook
Summary	                Reconciliation statistics
________________________________________

🔍 Reconciliation Results
Metric	                       Value
Cashbook Entries	             3,715
Bank Entries	                 3,739
Matched Transactions	         3,415
Bank Only Transactions	       328
Cashbook Only Transactions	   303
________________________________________

🔍 Key Insights
•	More than 90% of transactions were successfully reconciled.
•	Outstanding items indicate timing differences between ledgers.
•	Bank-only transactions highlight missing accounting entries.
•	Cashbook-only transactions indicate pending bank clearance.
________________________________________

🔍 Business Value

This project demonstrates:
•	Financial reconciliation automation
•	Data cleaning and transformation
•	Transaction matching logic
•	Exception reporting
•	Financial analytics
•	Python automation for accounting processes

The solution can significantly reduce manual reconciliation effort while improving accuracy and auditability.

