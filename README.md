#  UPI Transactions Analysis

##  Project Overview
This Power BI project analyzes **UPI (Unified Payments Interface) transaction data for the year 2024**.  
The dashboard provides insights into transaction amounts, remaining balances, customer demographics, device usage, bank-wise transfers, and city-wise financial trends.

The goal of this project is to visualize digital payment behavior and banking transaction patterns using interactive Power BI reports.

---

##  Dataset Description

**File Name:** `UPI Transactions.xlsx`  
**Total Records:** 999+ transactions  
**Time Period:** January 2024 – December 2024  

###  Key Columns

| Column Name | Description |
|-------------|-------------|
| TransactionID | Unique ID for each transaction |
| TransactionDate | Date of transaction |
| Amount | Transaction amount |
| RemainingBalance | Balance left after transaction |
| BankNameSent | Bank from which money is sent |
| BankNameReceived | Bank which receives money |
| City | City where transaction occurred |
| Gender | Customer gender |
| AgeGroups | Customer age category |
| DeviceType | Device used (Mobile, Tablet, etc.) |
| PaymentMethod | Mode of payment (Phone Number, QR, etc.) |
| TransactionType | Type of transaction (Transfer, Payment, etc.) |
| Status | Transaction status (Success / Failed) |
| MerchantName | Merchant involved (if any) |
| Purpose | Purpose of transaction |

---

##  Data Cleaning & Transformation (Power Query)

Steps performed in Power Query Editor:
- Promoted first row as headers
- Changed data types for numerical and date columns
- Split columns where needed
- Removed unnecessary columns
- Renamed columns for clarity
- Ensured text formatting for account numbers

---

##  Dashboard Features

### 🔹 Page 1 – Monthly Balance Overview
- Column Chart: **Balance by Month (2024)**
- Displays total remaining balance trend across months
- Interactive slicers:
  - BankNameSent
  - BankNameReceived
  - City
  - DeviceType
  - Gender
  - Age Groups
  - MerchantName
  - PaymentMethod
  - Purpose
  - TransactionType

### 🔹 Page 2 – City & Currency Matrix
- Matrix table:
  - Rows: Month
  - Columns: City (Bangalore, Delhi, Hyderabad, Mumbai)
  - Measures:
    - Total Amount
    - Remaining Balance
- Currency mapping per city:
  - Bangalore → EUR  
  - Delhi → USD  
  - Hyderabad → GBP  
  - Mumbai → INR  

---

##  Key Measures (DAX)

```DAX
Total Amount = SUM('UPI Transactions'[Amount])

Total Remaining Balance = SUM('UPI Transactions'[RemainingBalance])

Monthly Amount = 
CALCULATE(
    [Total Amount],
    MONTH('UPI Transactions'[TransactionDate])
)

Monthly Balance = 
CALCULATE(
    [Total Remaining Balance],
    MONTH('UPI Transactions'[TransactionDate])
)
