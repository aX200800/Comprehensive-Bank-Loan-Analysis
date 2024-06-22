## Project Title
**Comprehensive Bank Loan Analysis**

## Project Description
This project involves a comprehensive analysis of bank loan data visualized through a Power BI dashboard. The dashboard provides key insights into various loan metrics, including total loan applications, funded amounts, received amounts, interest rates, and debt-to-income ratios. It categorizes data based on different dimensions such as loan status, purpose, and borrower attributes to help stakeholders make data-driven decisions.

## Installation / Prerequisites
- **Power BI Desktop:** Ensure you have Power BI Desktop installed.
- **Data Source:** Access to the hotel's revenue and occupancy data.
- **Figma and Adobe Photoshop:** Used for designing the dashboard background and visual elements.

## Project Structure
### DAX Calculations
1. **Total Loan Applications:**
   ```DAX
    Total_Loan_Applications = COUNT(Loan_DATA[id])
    MTD_Loan_Applications = CALCULATE(TOTALMTD([Total_Loan_Applications],'Date_Table'[Date]))
    PMTD_Loan_applications = CALCULATE([Total_Loan_Applications],DATESMTD(DATEADD('Date_Table'[Date],-1,MONTH)))
    MOM_Loan_Applications = ([MTD_Loan_Applications] - [PMTD_Loan_applications]) / [PMTD_Loan_applications]
   ```

2. **Total Funded Amount:**
   ```DAX
    Total_Funded_Amount = SUM(Loan_DATA[loan_amount])
    MTD_Funded_Amount = CALCULATE(TOTALMTD([Total_Funded_Amount],'Date_Table'[Date]))
    PMTD_Funded_Amount = CALCULATE([Total_Funded_Amount],DATESMTD(DATEADD('Date_Table'[Date],-1,MONTH)))
    MOM_Funded_Amount = ([MTD_Funded_Amount] - [PMTD_Funded_Amount]) / [PMTD_Funded_Amount]
   ```

3. **Total Amount Received:**
   ```DAX
    Total_Amount_Received = SUM(Loan_DATA[total_payment])
    MTD_Received_Amount = CALCULATE(TOTALMTD([Total_Amount_Received],'Date_Table'[Date]))
    PMTD_Received_Amount = CALCULATE([Total_Amount_Received],DATESMTD(DATEADD('Date_Table'[Date],-1,MONTH)))
    MOM_Received_Amount = ([MTD_Received_Amount] - [PMTD_Received_Amount]) / [PMTD_Received_Amount]
   ```

4. **Average Interest Rate:**
   ```DAX
    Avg_Interest_Rate = AVERAGE(Loan_DATA[int_rate])
    MTD_Avg_Interest_Rate = CALCULATE(TOTALMTD([Avg_Interest_Rate],'Date_Table'[Date]))
    PMTD_Avg_Interest_Rate = CALCULATE([Avg_Interest_Rate],DATESMTD(DATEADD('Date_Table'[Date],-1,MONTH)))
    MOM_Avg_Interest_Rate = ([MTD_Avg_Interest_Rate] - [PMTD_Avg_Interest_Rate]) / [PMTD_Avg_Interest_Rate]
   ```

5. **Average Debt-to-Income (DTI) Ratio:**
   ```DAX
    Avg_DTI = AVERAGE(Loan_DATA[dti])
    MTD_Avg_DTI = CALCULATE(TOTALMTD([Avg_DTI],'Date_Table'[Date]))
    PMTD_Avg_DTI = CALCULATE([Avg_DTI],DATESMTD(DATEADD('Date_Table'[Date],-1,MONTH)))
    MOM_Avg_DTI = ([MTD_Avg_DTI] - [PMTD_Avg_DTI]) / [PMTD_Avg_DTI]
   ```

6. **Good Loans vs Bad Loans:**
   
   **DAX Calculations for Good Loans:**   

        Goodloan% = CALCULATE([Total_Loan_Applications], 'Loan_DATA'[loan_status] = "Good") / [Total_Loan_Applications]
        Goodloan_Applications = CALCULATE([Total_Loan_Applications], 'Loan_DATA'[loan_status] = "Good")
        Goodloan_Funded_Amount = CALCULATE([Total_Funded_Amount], 'Loan_DATA'[loan_status] = "Good")
        Goodloan_Total_Received_Amount = CALCULATE([Total_Amount_Received], 'Loan_DATA'[loan_status] = "Good")


   **DAX Calculations for Bad Loans:**
   
        Badloan% = CALCULATE([Total_Loan_Applications], 'Loan_DATA'[loan_status] = "Bad") / [Total_Loan_Applications]
        Badloan_Applications = CALCULATE([Total_Loan_Applications], 'Loan_DATA'[loan_status] = "Bad")
        Badloan_Funded_Amount = CALCULATE([Total_Funded_Amount], 'Loan_DATA'[loan_status] = "Bad")
        Badloan_Total_Received_Amount = CALCULATE([Total_Amount_Received], 'Loan_DATA'[loan_status] = "Bad")


## Project Background

   **Figma**: Used for initial layout and design planning to ensure a user-friendly dashboard interface.   
   **Adobe Photoshop**: Utilized for creating custom visuals to enhance the dashboard's aesthetic appeal.

## Summary
The Comprehensive Bank Loan Analysis dashboard is designed to provide in-depth insights into various loan metrics. Using advanced DAX calculations and a visually appealing interface, the dashboard helps in understanding loan distribution, funding, and repayment trends, empowering stakeholders to make informed decisions.
