# KULTRA MEGA STORE INVENTORY(KMS)-SQL-PROJECT
## INFO ABOUT THE COMPANY
Kultra Mega Stores (KMS), headquartered in Lagos, specialises in office supplies and furniture. Its customer base includes individual consumers, small businesses (retail), and large corporate clients (wholesale) across Lagos, Nigeria.
# ANALYSIS OVERVIEW
This project focuses on analyzing the sales performance of Kulta Mega Stores within the Abuja Division, with the goal of uncovering key insights, findings, and actionable recommendations to support informed business decisions. The analysis was conducted using two datasets: KMS SQL Case Study and Order_Status. The KMS SQL Case Study dataset includes comprehensive details on customers, products, shipping methods, and more, while the Order_Status dataset provides information on customers who returned orders, including order statuses and corresponding IDs.
## KEY QUESTOIN OF CONCENTRATION INCLUDES
1. Which product category had the highest sales?
2. What are the Top 3 and Bottom 3 regions in terms of sales?
3. What were the total sales of appliances in Ontario?
4. Advise the management of KMS on what to do to increase the revenue from the bottom 10 customers
5. KMS incurred the most shipping cost using which shipping method?
6. Who are the most valuable customers, and what products or services do they typically purchase?
7. Which small business customer had the highest sales?
8. Which Corporate Customer placed the most number of orders in 2009 – 2012?
9. Which consumer customer was the most profitable one?
10. Which customer returned items, and what segment do they belong to?
11. If the delivery truck is the most economical but the slowest shipping method and Express Air is the fastest but the most expensive one, do you think the company appropriately spent shipping costs based on the Order Priority?

# TOOLS USED FOR THIS ANALYSIS
The primary tool used for this analysis is Microsoft SQL Server Management Studio (SSMS), which can be downloaded via the following link: (https://learn.microsoft.com/en-us/ssms/install/install)
# DATA SOURCE
The dataset used in this project was sourced from the Digital SkillUp Africa (DSA) Learning Management System as part of the final project requirement.

# ETL PROCESS

## Data Extraction
As mentioned earlier, the data was extracted from the Digital SkillUp Africa Learning Management System.
## Data Transformation & Loading
Data transformation was carried out in SQL Server. This included correcting data types—for instance, converting date fields stored as strings back to proper date formats and changing the Order_ID column from Smallint to Int to accommodate larger volumes. Additionally, missing values in the Profit_Base_Margin, Profit, and Unit_Price columns were handled using SQL queries to ensure data completeness and consistency.
# Checking for null values in "PROFIT, PRODUCT BASE MARGIN and UNIT PRICE COLUMNS"
              select * from [KMS Sql Case Study]
              Where Product_Base_Margin Is NULL Or Profit is NULL Or
              Unit_Price is NULL


















