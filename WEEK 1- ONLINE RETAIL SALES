# AnalystLab Africa Data Analytics Internship Program – Batch B

## Week 1 Project Summary Report

### Project Title

**Data Cleaning and Exploratory Data Analysis of the Online Retail Dataset**

### Project Overview

This project focused on cleaning and exploring the Online Retail dataset using SQL. The objective was to transform the raw transactional data into a clean, structured, and analysis-ready dataset while identifying meaningful business insights through exploratory data analysis.

### Data Cleaning Challenges Encountered

Several data quality issues were identified during the cleaning process, including:

* Missing values in the **CustomerID** and **Description** columns.
* Duplicate transaction records.
* Invalid records containing negative or zero quantities and unit prices.
* Cancelled orders identified by invoice numbers beginning with **"C"**.
* Inconsistent text formatting in categorical fields.
* Date fields requiring standardization for time-based analysis.

### Cleaning Actions Performed

To improve data quality, the following steps were carried out:

* Removed records with missing CustomerID and Description values.
* Removed duplicate records using SQL window functions.
* Deleted invalid transactions where Quantity or UnitPrice was less than or equal to zero.
* Excluded cancelled orders from the analysis.
* Standardized text fields by trimming extra spaces and converting values to uppercase.
* Converted the InvoiceDate column into a consistent SQL DATETIME format.

These cleaning steps produced a reliable dataset suitable for exploratory analysis.

### Key Exploratory Data Analysis Findings

The cleaned dataset was analyzed using SQL aggregate functions, grouping operations, and window functions. The analysis included:

* Identification of the top-selling products based on total quantity sold.
* Revenue analysis across different countries.
* Monthly sales trend analysis.
* Customer purchasing behaviour based on transaction frequency and total spending.
* Product performance based on generated revenue.

### Top Insights

1. A relatively small number of products generated a significant proportion of total sales, indicating high customer demand for specific items.

2. The United Kingdom accounted for the largest share of revenue, making it the company's primary market.

3. Monthly sales patterns suggested seasonal fluctuations, with certain months recording noticeably higher revenue than others.

4. Customer spending was unevenly distributed, with a small group of loyal customers contributing a substantial portion of total revenue.

5. Removing cancelled and invalid transactions resulted in more accurate sales and revenue reporting.

### Conclusion

The project demonstrated the importance of data cleaning before conducting analysis. By addressing missing values, duplicates, invalid records, and inconsistent formatting, the dataset became suitable for business intelligence reporting. The exploratory analysis provided valuable insights into customer behaviour, product performance, and revenue trends that can support strategic business decisions.

