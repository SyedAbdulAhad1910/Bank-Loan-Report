# Bank-Loan-Report
Here is a step-by-step **README** for your **Bank Loan Report Dashboard** project using **SQL** and **Power BI**:

---

## **Bank Loan Report Dashboard**

### **Project Overview**
This project is a comprehensive dashboard built in **Power BI** using data imported from **SQL Server**. The dashboard provides key insights into loan applications, funding, and loan performance across various dimensions, such as time, loan status, and client information. It enables decision-making based on KPIs like total loan applications, total funded amount, total amount received, and other metrics.

### **Prerequisites**
1. **SQL Server**: You need access to a SQL Server instance where the bank loan data is stored.
2. **Power BI**: Download and install Power BI Desktop.
3. **Basic understanding of SQL** for data extraction and DAX for calculations in Power BI.

---

### **Step 1: Data Source - SQL Server**
1. **Connect to SQL Server**:
   - Open **Power BI Desktop**.
   - Click on **Get Data** > **SQL Server**.
   - Enter the server name and database name where the `bank_loan_data` table is stored.
   - Select **Direct Query** or **Import** based on your needs.

2. **Extract Data** using SQL queries to retrieve necessary metrics for the dashboard. Here are some key queries used:

- Total Loan Applications:
   SQL
   SELECT COUNT(id) AS Total_Loan_Applications 
   FROM bank_loan_data
   ```

- Month-to-Date (MTD) Applications**:
   SQL
   SELECT COUNT(id) AS MTD_Applications 
   FROM bank_loan_data 
   WHERE MONTH(issue_date) = 12 AND YEAR(issue_date) = 2021
   `

- Previous Month-to-Date (PMTD) Applications:
   SQL
   SELECT COUNT(id) AS PMTD_Applications 
   FROM bank_loan_data 
   WHERE MONTH(issue_date) = 11 AND YEAR(issue_date) = 2021
   ```

- Total Funded Amount:
   SQL
   SELECT SUM(loan_amount) AS Total_Funded_Amount 
   FROM bank_loan_data
   WHERE MONTH(issue_date) = 12 AND YEAR(issue_date) = 2021
   

- Good Loan Applications:
   SQL
   SELECT COUNT(id) AS Good_Loan_Applications 
   FROM bank_loan_data 
   WHERE loan_status = 'Fully Paid' OR loan_status = 'Current'
   



### Step 2: Data Transformation in Power BI
1. Power Query Editor:
   - After importing the data, transform it in Power BI using Power Query Editor.
   - Apply necessary data cleaning and transformations to ensure all fields are in the correct format (e.g., date, numerical).
   
2. Create a Date Table:
   - Use Power Query Editor to create a date table for time-based DAX calculations.



### Step 3: Key Metrics and KPIs
Here are some of the key performance indicators (KPIs) included in the dashboard:

1. **Total Loan Applications**
2. **Month-to-Date (MTD) Applications**
3. **Previous Month-to-Date (PMTD) Applications**
4. **Total Funded Amount**
5. **Total Amount Received**
6. **Good Loan Percentage**
7. **Bad Loan Percentage**

These KPIs were calculated using SQL and DAX in Power BI.



### **Step 4: DAX Calculations**
Some important DAX formulas for key metrics include:

- **Total Loan Applications**:
   DAX
   Total_Loan_Applications = COUNT('bank_loan_data'[id])
   

- **MTD Loan Applications**:
   DAX
   MTD_Applications = CALCULATE(
       COUNT('bank_loan_data'[id]),
       DATESBETWEEN('Date'[Date], STARTOFMONTH(TODAY()), TODAY())
   )
   

- **PMTD Loan Applications**:
   DAX
   PMTD_Applications = CALCULATE(
       COUNT('bank_loan_data'[id]),
       DATESBETWEEN('Date'[Date], STARTOFMONTH(PREVIOUSMONTH(TODAY())), TODAY())
   )
   



### **Step 5: Visualization in Power BI**
1. Create a Filled Map:
   - Import the data and use a **Filled Map** to visualize loan applications by state. Ensure that the `address_state` field is available.
   
2. Add Key Visualizations:
   - **KPIs**: Add KPI cards for metrics like Total Loan Applications, MTD Loan Applications, etc.
   - **Bar Charts**: Show loan applications and amounts by loan status, term, or purpose.
   - **Line Charts**: Track loan applications over time (month-by-month).
   - **Pie Charts**: Visualize loan statuses like **Good Loan Percentage** and **Bad Loan Percentage**.

---

### Step 6: Final Touches
1. **Formatting**:
   - Ensure all charts and tables are properly formatted, including axis titles, labels, and color schemes.
   
2. **Interactive Filters**:
   - Add slicers for **date**, **loan status**, and other key fields to make the dashboard interactive.

---

### **Conclusion**
This **Bank Loan Report Dashboard** provides a comprehensive view of loan applications and performance metrics. With the ability to filter by loan status, term, and more, users can derive actionable insights from the data.


