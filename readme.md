# **Expense Analysis and Optimization Using Google BigQuery**

## **Introduction:**
This project involves the analysis of an expense dataset to identify patterns, optimize spending, and provide actionable insights into expense management. Using Google BigQuery, a cloud-based data warehouse, we efficiently processed and analyzed the data, making use of SQL queries to uncover trends and insights across various spending categories.

## **Project Overview:**
- **Dataset**: The dataset comprises expenses categorized by companies, expense categories (rent, groceries, entertainment, etc.), and costs over multiple months. The dataset was uploaded to BigQuery for analysis.
- **Objective**: Analyze expenses to identify spending trends, calculate totals for different categories, and provide recommendations for optimizing future budgets.
- **Tool Used**: Google BigQuery for storage, querying, and analysis of large datasets.

## **Google BigQuery Setup:**

### **1. Creating the Dataset in Google BigQuery:**
   - Navigate to the BigQuery console.
   - Click on your project and select **"Create Dataset"**.
   - Provide a name for the dataset and configure the location and expiration settings as needed.
   
### **2. Uploading the Expense Data:**
   - Within your dataset, click on **"Create Table"**.
   - Select **"Upload CSV"** as the source.
   - Select your CSV file containing the expense data.
   - Provide the table name and schema (columns for Date, Company, CategoryID, and Cost).
   - Click **Create Table**. The data will now be available in BigQuery for querying.

### **3. Querying the Data:**
   - In the BigQuery editor, SQL queries were executed to answer specific business questions such as identifying the highest expense, unique categories, monthly patterns, and much more.
   - Examples of queries used in this project:
     - **Find unique categories**: `SELECT DISTINCT CategoryID FROM dataset.table`
     - **Calculate total expenses per category per month**:  
       ```sql
       SELECT FORMAT_DATE('%Y-%m', Date) AS YearMonth, CategoryID, SUM(Cost) AS TotalCost
       FROM dataset.table
       GROUP BY YearMonth, CategoryID
       ```
     - **Find spending patterns for a specific store (e.g., Rewe)**:  
       ```sql
       SELECT Company, FORMAT_DATE('%Y-%m', Date) AS YearMonth, SUM(Cost) AS TotalCost
       FROM dataset.table
       WHERE Company = 'Rewe'
       GROUP BY Company, YearMonth
       ```

## **Analysis and Insights:**
- **Category-wise Spending**: A detailed breakdown of expenses across all categories revealed significant trends, with grocery and restaurant expenses taking a major portion of the budget.
- **Highest Expense Companies**: The project identified companies with the highest total spending, such as Rewe and Prima, and explored month-wise spending trends.
- **Grocery vs. Restaurant Spending**: A comparative analysis showed that restaurant expenses were significant but varied less month-to-month, while grocery expenses fluctuated, especially during certain months.
  
## **Project Structure:**
1. **Expense Dataset**: The main table containing all expense-related information.
2. **SQL Queries**: A series of SQL queries executed on the dataset to provide actionable insights.
3. **BigQuery Integration**: A step-by-step process to upload and query the dataset on BigQuery.

---