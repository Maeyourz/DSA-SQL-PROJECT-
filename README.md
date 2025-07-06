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

<img width="1511" height="834" alt="Image" src="https://github.com/user-attachments/assets/8ad549fb-9c4b-4860-8ad7-777fb679a535" />
# Replacing the Null Values with Mean

              update [KMS Sql Case Study]
              Set Profit = 181.18
              where Profit is NULL
              
              update [KMS Sql Case Study]
              Set Unit_Price = 89.35
              where Unit_Price is NULL
              
              update [KMS Sql Case Study]
              Set Product_Base_Margin = 0.51
              where Product_Base_Margin is NULL

# MAIN ANALYSIS 
# 1.0 Finding the Product Category with the Highest Sales
technology has the highest sales 

<img width="1491" height="853" alt="Image" src="https://github.com/user-attachments/assets/f7c13ecf-3805-436a-a56f-a05ffac8dfdc" />
Select top 1 Product_Category, Sum(Sales) As TotalSales
From [KMS Sql Case Study]
Group By Product_Category
Order By TotalSales Desc

# 1.1 Top 3 Product Category with the highest Sales

<img width="1455" height="861" alt="Image" src="https://github.com/user-attachments/assets/845a43cd-b00c-4bdc-a2e8-fdb11de08b8d" />
Select top 3 Product_Category, Sum(Sales) As TotalSales
From [KMS Sql Case Study]
Group By Product_Category
Order By TotalSales Desc

# 2.0 Finding the TOP 3 and BOTTOM 3 Region in Terms of Sales

<img width="1482" height="863" alt="Image" src="https://github.com/user-attachments/assets/df6507c2-099b-4495-a987-736ff5d0b579" />

----Top 3 Region by Sales----
Select top 3 Region, Sum(Sales) As TotalSales
From [KMS Sql Case Study]
Group By Region
Order By TotalSales Desc

# 2.1 Bottom 3 Region by Sales
bottom 3

<img width="1470" height="822" alt="Image" src="https://github.com/user-attachments/assets/1b5f1373-a033-4bfb-b4e0-b8804e584ef0" />

Select top 3 Region, Sum(Sales) As TotalSales
From [KMS Sql Case Study]
Group By Region
Order By TotalSales Asc

# 3.0 Determining the Total sales of appliances in Ontario
Select Sum(Sales) As TotalSales
From [KMS Sql Case Study]
where Product_Category = 'Appliances'
And Region = 'Ontario'

# 4.0 Determining the bottom 10 customers by Sales

<img width="1529" height="798" alt="Image" src="https://github.com/user-attachments/assets/a5a53216-4124-435d-8cfb-ea4d5f07da1b" />
SELECT Top 10 customer_name, SUM(sales) AS total_sales
FROM [KMS Sql Case Study]
GROUP BY customer_name
ORDER BY total_sales ASC

# 5.0 Determining the Highest shipping cost in a particular shipping method
<img width="1243" height="648" alt="Image" src="https://github.com/user-attachments/assets/2de2d8b9-ead3-462b-8722-ee565923ba9a" />


Select Ship_Mode, Shipping_Cost
From [KMS Sql Case Study]
Order by Shipping_Cost Desc

# 5.1 Top 1 highest shpping cost by shipping method
<img width="1170" height="898" alt="Image" src="https://github.com/user-attachments/assets/e9766bda-57a2-4da1-a622-0627cef9314d" />
Select Top 1 Ship_Mode, Shipping_Cost
From [KMS Sql Case Study]
Order by Shipping_Cost Desc

# 6.0 The Most valuable Customers and the product or Services there purchase
<img width="629" height="666" alt="Image" src="https://github.com/user-attachments/assets/38dfa4c4-cecf-4fd8-9ae3-f65fa34f85c1" />
Select * from [KMS Sql Case Study]

Select Top 10 Customer_Name, Product_Name, Sum(Sales) As Total_Spent
From [KMS Sql Case Study]
Group By Customer_Name, Product_Name
Order By Total_Spent Desc

# 7.0 Small Business Customer with the highest Sales
<img width="1234" height="866" alt="Image" src="https://github.com/user-attachments/assets/5f93350b-158c-4123-8dc1-7e631bfd5f3e" />

SELECT Top 10 Customer_Name, SUM(Sales) AS Total_sales
FROM [KMS Sql Case Study]
WHERE Customer_Segment = 'Small Business'
GROUP BY Customer_Name
ORDER BY Total_sales DESC

# 7.1 Top 1 Small Business Customer with the highest Sales
<img width="1473" height="860" alt="Image" src="https://github.com/user-attachments/assets/02899184-9668-47c0-9fba-3a996304d052" />
SELECT Top 1 Customer_Name, SUM(Sales) AS Total_sales
FROM [KMS Sql Case Study]
WHERE Customer_Segment = 'Small Business'
GROUP BY Customer_Name
ORDER BY Total_sales DESC

# 8.0 Corperate customer that placed the most number of orders in 2009 - 2012
<img width="1435" height="806" alt="Image" src="https://github.com/user-attachments/assets/18eeba7d-5d5a-4b8b-b56a-70cf6ede59b7" />
Select Top 1 Customer_Name, Count(Order_ID) As Total_Orders
From [KMS Sql Case Study]
WHERE Customer_Segment = 'Corporate'
And Order_Date Between '2009-01-01' and '2012-12-31'
Group By Customer_Name
Order By Total_Orders Desc

# 8.1 Top 5 Corperate customer that placed the most number of orders in 2009 - 2012
<img width="1273" height="865" alt="Image" src="https://github.com/user-attachments/assets/6e093486-19f1-4a06-a9c0-70d4be34dfc6" />
Select Top 5 Customer_Name, Count(Order_ID) As Total_Orders
From [KMS Sql Case Study]
WHERE Customer_Segment = 'Corporate'
And Order_Date Between '2009-01-01' and '2012-12-31'
Group By Customer_Name
Order By Total_Orders Desc

# 9.0 Most Profitable Consumer Customer
<img width="1015" height="416" alt="Image" src="https://github.com/user-attachments/assets/d50cd499-043c-4ca7-beb8-286fb43ce09f" />
SELECT Top 1 Customer_Name, SUM(Profit) AS total_profit
FROM [KMS Sql Case Study]
WHERE Customer_Segment = 'Consumer'
GROUP BY Customer_Name
ORDER BY total_profit DESC

# 9.1 Top 5 Most Profitable Consumer Customer
<img width="1304" height="844" alt="Image" src="https://github.com/user-attachments/assets/597cb049-88eb-4a99-ab16-dbdb6838eb61" />
SELECT Top 5 Customer_Name, SUM(Profit) AS total_profit
FROM [KMS Sql Case Study]
WHERE Customer_Segment = 'Consumer'
GROUP BY Customer_Name
ORDER BY total_profit DESC

# 10.0 Customer that returned items, and the segment they belong to
      <img width="974" height="319" alt="Image" src="https://github.com/user-attachments/assets/df4aa715-7b0d-4d4e-91b4-20d30111ef24" />
	  ----Joining the two tables ([KMS Sql Case Study] and Order_Status) together

SELECT DISTINCT [KMS Sql Case Study].customer_name, [KMS Sql Case Study].customer_segment
FROM [KMS Sql Case Study]
JOIN Order_Status 
ON [KMS Sql Case Study].Order_ID = Order_Status.Order_ID
WHERE [Status] = 'Returned'


# 11.0 Shipping Cost by Order Priority and Shipping Method
<img width="1231" height="894" alt="Image" src="https://github.com/user-attachments/assets/70c67714-73fd-4da7-84a2-8e4b3b805af9" />
SELECT 
    Order_Priority,
    Ship_Mode,
    SUM(Shipping_Cost) AS Total_Shipping_Cost
FROM [KMS Sql Case Study]
GROUP BY Order_Priority, Ship_Mode
ORDER BY Order_Priority, Ship_Mode


















