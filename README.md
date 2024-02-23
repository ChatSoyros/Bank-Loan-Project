# Bank-Loan-Anlysis

## Project Overview


Bank loans are vital for individuals and businesses, but borrowers must understand loan terms and responsibilities. Banks collect loan data from applications, credit reports, internal records, online portals, and third-party sources. The loan process involves application review, identity and credit checks, income verification, risk assessment, approval or denial, agreement, funds disbursement, repayment, and ongoing monitoring.
Banks analyze loan data for risk assessment, decision-making, portfolio management, fraud detection, compliance, customer insights, profitability, market research, credit risk management, and customer retention. This analysis informs lending decisions, portfolio management, risk mitigation, regulatory compliance, and customer service improvements

## Tools

- SQL - Data Analysis

- Tableau - Creating reports

### Fields Used in Data

•	Loan ID: Loan ID is a unique identifier for loan applications or accounts, facilitating efficient tracking and management. Banks use Loan IDs to organize records, monitor repayments, and handle customer inquiries effectively.

•	Address State: Address State shows borrower's location for assessing regional risk, state regulations compliance, and default probabilities estimation. Use for Banks: Banks use it to spot regional loan demand trends, adapt marketing, and manage risk across regions.

•	Employee Length:  Employee Length indicates borrower's job stability. Longer tenure suggests greater security. Banks use this to gauge repayment capacity, with stable employment lowering default risk.

•	Employee Title: Employee Title indicates borrower's occupation, aiding lenders in understanding income sources. Banks use it to verify income, assess financial capacity, and customize loan offers.

•	Grade: Grade classifies loan risk based on creditworthiness. Higher grades mean lower risk. Banks use grades to price loans and manage risk. Higher grades get lower rates, appealing to investors.

•	Sub Grade: Sub Grade refines risk assessment within a grade for more precise differentiation.  Sub Grades aid in tailoring interest rates and lending terms to match borrower risk profiles.

•	Home Ownership: Ownership shows borrower's housing status, reflecting financial stability. Banks use it to assess collateral and borrower stability, with homeowners potentially having lower default rates.

•	Issue Date: Issue Date marks loan origination, vital for tracking and maturity calculations. Banks track loan aging, calculate interest, and manage portfolios using Issue Dates.

•	Last Credit Pull Date: Last Credit Pull Date tracks the last credit report access, aiding creditworthiness monitoring. Banks use it to update credit history, assess risk, and inform lending decisions.

•	Last Payment Date: Last Payment Date marks recent loan payment, tracking payment history. Banks assess payment behavior, delinquency, and project future payments using this date.

•	Loan Status: Loan Status shows current loan state (e.g., paid, current, default), tracking performance. Banks monitor loan health, categorize for risk analysis, and determine provisioning using Loan Status.

•	Next Payment Date: Next Payment Date estimates next loan payment, aiding cash flow forecasting. Banks use it for liquidity planning and revenue projection from loan portfolios.

•	Term:  Purpose: Term sets loan duration in months, defining repayment period. Banks structure agreements, calculate interest, and manage maturities with the term.

•	Verification Status: Verification Status shows if borrower's financial info is verified, assessing data accuracy. Banks gauge data reliability, verify income, and evaluate loan application credibility using this.

•	Annual Income: Annual Income shows borrower's yearly earnings, assessing repayment capacity. Banks determine loan eligibility, debt-to-income ratios, and creditworthiness using this figure.

•	DTI (Debt-to-Income Ratio): DTI measures borrower's debt relative to income, assessing capacity for more debt. Banks use DTI to gauge payment handling and make lending decisions.

•	Instalment: Instalment is the fixed monthly payment covering principal and interest.  Banks structure loan terms, calculate schedules, and assess affordability using this.

•	Interest Rate: Interest Rate is the annual borrowing cost as a percentage, determining loan cost. Banks price loans, manage margins, and attract investors using interest rates.

•	Loan Amount: Loan Amount is the total borrowed sum. It defines the principal amount. Banks use Loan Amount to determine loan size.

## PROBLEM STATEMENT

"In order to monitor and assess our bank's lending activities and performance, we need to create a comprehensive Bank Loan Report. This report aims to provide insights into key loan-related metrics and their changes over time. The report will help us make data-driven decisions, track our loan portfolio's health, and identify trends that can inform our lending strategies.

### Key Performance Indicators (KPIs) Requirements


•	Total Loan Applications: It is essential to monitor the Month-to-Date (MTD) Loan Applications and track changes Month-over-Month (MoM).

•	Total Funded Amount: We want to keep an eye on the MTD Total Funded Amount and analyze the Month-over-Month (MoM) changes in this metric.

•	Total Amount Received: We should analyze the Month-to-Date (MTD) Total Amount Received and observe the Month-over-Month (MoM) changes.

•	Average Interest Rate: Monitoring the Month-over-Month (MoM) variations in interest rates will provide insights into our lending portfolio's overall cost.

•	Average Debt-to-Income Ratio (DTI): We need to compute the average DTI for all loans, MTD, and track Month-over-Month (MoM) fluctuations.


### Good Loan v Bad Loan KPI’s



 In order to evaluate the performance of our lending activities and assess the quality of our loan portfolio, we need to create a comprehensive report that distinguishes between 'Good Loans' and 'Bad Loans' based on specific loan status criteria.



 #### Good Loan KPIs:
 

 •	Good Loan Application Percentage
 
•	Good Loan Applications

•	Good Loan Funded Amount

•	Good Loan Total Received Amount



#### Bad Loan KPIs:



•	Bad Loan Application Percentage

•	Bad Loan Applications

•	Bad Loan Funded Amount

•	Bad Loan Total Received Amount


# Data Analysis

Total Loan Applications
```sql
SELECT COUNT(id) AS Toatl_Loan_Applications FROM `project-spyrxat.Bank_Loan.bank_loan_data`
```
MTD Loan applications
```sql
SELECT COUNT(id) AS MTD_Toatl_Loan_Applications FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE EXTRACT(MONTH FROM issue_date)=12 
AND EXTRACT(YEAR FROM issue_date)=2021
```
PMTD Loan Applications
```sql
SELECT COUNT(id) AS PMTD_Toatl_Loan_Applications FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE EXTRACT(MONTH FROM issue_date)=11 AND EXTRACT(YEAR FROM issue_date)=2021
```
Total Funded Amount
```sql
SELECT SUM(loan_amount)AS Toatl_Funded_Amount FROM `project-spyrxat.Bank_Loan.bank_loan_data`
```
MTD Total Funded Amount
```sql
SELECT SUM(loan_amount)AS MTD_Toatl_Funded_Amount FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE EXTRACT( MONTH FROM issue_date)=12 
AND EXTRACT( YEAR FROM issue_date)=2021
```
PMTD Total Funded Amount
```sql
SELECT SUM(loan_amount)AS PMTD_Toatl_Funded_Amount FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE EXTRACT( MONTH FROM issue_date)=11
AND EXTRACT( YEAR FROM issue_date)=2021
```
Total Amount Received 
```sql
SELECT SUM(total_payment)AS Toatl_Amount_Received FROM `project-spyrxat.Bank_Loan.bank_loan_data`
```
MTD Total Amount Received 
```sql
SELECT SUM(total_payment)AS MTD_Toatl_Amount_Received FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE EXTRACT( MONTH FROM issue_date)=12
AND EXTRACT( YEAR FROM issue_date)=2021
```
PMTD Total Amount Received 
```sql
SELECT SUM(total_payment)AS PMTD_Toatl_Amount_Received FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE EXTRACT( MONTH FROM issue_date)=11
AND EXTRACT( YEAR FROM issue_date)=2021
```
Average Interest Rate
```sql
SELECT ROUND(AVG(int_rate),5) * 100 AS Avg_Interest_Rate FROM `project-spyrxat.Bank_Loan.bank_loan_data`
```
MTD Average Interest Rate
```sql
SELECT ROUND(AVG(int_rate),5) * 100 AS MTD_Avg_Interest_Rate FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE EXTRACT( MONTH FROM issue_date)=12
AND EXTRACT( YEAR FROM issue_date)=2021
```
PMTD Average Interest Rate
```sql
SELECT ROUND(AVG(int_rate),5) * 100 AS PMTD_Avg_Interest_Rate FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE EXTRACT( MONTH FROM issue_date)=11
AND EXTRACT( YEAR FROM issue_date)=2021
```
Average Debt-to-Income Ratio (DTI)
```sql
SELECT ROUND(AVG(dti),4)* 100 AS Avg_DTI FROM `project-spyrxat.Bank_Loan.bank_loan_data`
```
MTD Average Debt-to-Income Ratio (DTI)
```sql
SELECT ROUND(AVG(dti),5)* 100 AS MTD_Avg_DTI FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE EXTRACT( MONTH FROM issue_date)=12
AND EXTRACT( YEAR FROM issue_date)=2021
```
PMTD Average Debt-to-Income Ratio (DTI)
```sql
SELECT ROUND(AVG(dti),5)* 100 AS PMTD_Avg_DTI FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE EXTRACT( MONTH FROM issue_date)=11
AND EXTRACT( YEAR FROM issue_date)=2021
```
#### Good Loan v Bad Loan KPI’s

Good Loan Application Percentage
```sql
SELECT 
   (COUNT(CASE WHEN loan_status= 'Fully Paid' OR loan_status='Current' THEN id END)* 100)
   /
   COUNT(id) AS Good_loan_percentage
FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
```
Good Loan Applications
```sql
SELECT COUNT(id) AS Good_Loan_Applications FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE loan_status ='Fully Paid'OR loan_status = 'Current'
```
Good Loan Funded Amount
```sql
SELECT SUM(loan_amount) AS Good_Loan_Funded_Amount FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE loan_status ='Fully Paid'OR loan_status = 'Current'
```
Good Loan Total Received Amount
```sql
SELECT SUM(total_payment) AS Good_Loan_Received_amount FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE loan_status ='Fully Paid'OR loan_status = 'Current'
```
Bad Loan Application Percentage
```sql
SELECT 
   (COUNT(CASE WHEN loan_status = 'Charged Off' THEN id END)* 100)/
   COUNT(id) AS Bad_Loan_percentage
FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
```
Bad Loan Applications
```sql
SELECT COUNT(id) AS Bad_Loan_Applications FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE loan_status='Charged Off'
```
Bad Loan Funded Amount
```sql
SELECT SUM(loan_amount) AS Bad_loan_Funded_amount FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE loan_status='Charged Off'
```
Bad Loan Total Received Amount
```sql
SELECT SUM(total_payment) AS Bad_Loan_amount_Received FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE loan_status='Charged Off'
```
##### LOAN STATUS
```sql
SELECT
   loan_status,
   COUNT(id) AS Total_Loan_Applications,
   SUM(total_payment) AS Total_Amount_Received,
   SUM(loan_amount) AS Total_Funded_Amount,
   AVG(int_rate * 100) AS Interest_Rate,
   AVG(dti * 1000) AS DTI
FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
GROUP BY loan_status
```
```sql
SELECT
   loan_status,
    SUM(total_payment) AS MTD_Total_Amount_Received,
   SUM(loan_amount) AS MTD_Total_Funded_Amount
FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
WHERE EXTRACT(MONTH FROM issue_date)=12
GROUP BY loan_status
```
##### BANK LOAN REPORT 
Monthly Trends by Issue Date
```sql
SELECT
   EXTRACT(MONTH FROM issue_date) AS month_number,
   FORMAT_DATE('%B',issue_date) AS Month_Name,
   COUNT(id) AS Total_Loan_Applications,
   SUM(loan_amount) AS Total_Funded_Amount,
   SUM(total_payment) AS Total_Received_Amount
FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
GROUP BY month_number,Month_Name
ORDER BY month_number 
```
Regional Analysis by State
```sql
SELECT
   address_state,
   COUNT(id) AS Total_Loan_Applications,
   SUM(loan_amount) AS Total_Funded_Amount,
   SUM(total_payment) AS Total_Received_Amount
FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
GROUP BY address_state
ORDER BY COUNT(id) DESC
```
Loan Term Analysis
```sql
SELECT
   term,
   COUNT(id) AS Total_Loan_Applications,
   SUM(loan_amount) AS Total_Funded_Amount,
   SUM(total_payment) AS Total_Received_Amount
FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
GROUP BY term
ORDER BY term
```
Employee Length Analysis
```sql
SELECT
   emp_length,
   COUNT(id) AS Total_Loan_Applications,
   SUM(loan_amount) AS Total_Funded_Amount,
   SUM(total_payment) AS Total_Received_Amount
FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
GROUP BY emp_length
ORDER BY emp_length
```
Loan Purpose Breakdown
```sql
SELECT
   purpose,
   COUNT(id) AS Total_Loan_Applications,
   SUM(loan_amount) AS Total_Funded_Amount,
   SUM(total_payment) AS Total_Received_Amount
FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
GROUP BY purpose
ORDER BY COUNT(id) DESC
```
Home Ownership Analysis
```sql
SELECT
   home_ownership,
   COUNT(id) AS Total_Loan_Applications,
   SUM(loan_amount) AS Total_Funded_Amount,
   SUM(total_payment) AS Total_Received_Amount
FROM `project-spyrxat.Bank_Loan.bank_loan_data` 
GROUP BY  home_ownership
ORDER BY COUNT(id) DESC
```

# DATA VISUALIZATION 
   (WITH TABLEAU)



### DASHBOARD 1 : SUMMARY

📊 Explore key metrics like total loan applications, funded amounts, borrower repayments, and performance indicators for 'Good Loans' vs. 'Bad Loans'.

[SUMMARY.pdf](https://github.com/ChatSoyros/Bank-Loan-Project/files/14386667/SUMMARY.pdf)

### DASHBOARD 2 : OVERVIEW


- Monthly Trends by Issue Date (Line Chart)
- Regional Analysis by State (Filled Map)
- Loan Term Analysis (Donut Chart)
- Employee Length Analysis (Bar Chart)
- Loan Purpose Breakdown (Bar Chart)
- Home Ownership Analysis (Tree Map)
   
[OVERVIEW.pdf](https://github.com/ChatSoyros/Bank-Loan-Project/files/14386856/OVERVIEW.pdf)


### DASHBOARD 3 : DETAILS

The primary objective of the Details Dashboard is to provide a comprehensive and user-friendly interface for accessing vital loan data

[DETAILS.pdf](https://github.com/ChatSoyros/Bank-Loan-Project/files/14386875/DETAILS.pdf)






