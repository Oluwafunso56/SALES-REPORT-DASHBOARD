# SALES-REPORT-DASHBOARD SQL 
---Seasonality of Sales:
---To identify peak sales months, you can use SQL to 
---group the data by month and year and calculate the total sales for each month.
SELECT 
    FORMAT(Order_Date, 'yyyy-MM') AS YearMonth,
    Ship_Mode,
    round(SUM(Sales),2) AS TotalSales,
    round(SUM(Profit),2) AS TotalProfit
FROM 
    sales_data
GROUP BY 
    FORMAT(Order_Date, 'yyyy-MM'), Ship_Mode
ORDER BY 
    FORMAT(Order_Date, 'yyyy-MM'), Ship_Mode;

---Product Categories Profit Margins:
---To calculate profit margins by product category over time, 
--you can use SQL to group the data by category and calculate average profit margins
SELECT Category, round(AVG(Profit / Sales),2) AS AvgProfitMargin
FROM Sales_Data
GROUP BY Category;

---Regional Performance:
----To assess regional performance, you can group 
--the data by region or city and calculate total sales and profit.

SELECT Region, round(SUM(Sales),2) AS TotalSales, round(SUM(Profit),2) AS TotalProfit
FROM Sales_Data
GROUP BY Region;

---SUB_CATEGORY by Sales and Profit:

SELECT sub_category, round(SUM(Sales),2) AS TotalSales, round(SUM(Profit),2) AS TotalProfit
FROM Sales_Data
GROUP BY sub_category
ORDER BY TotalSales DESC;

---Product Category by Sales and Profit:

SELECT Category, round(SUM(Sales),2) AS TotalSales, round(SUM(Profit),2) AS TotalProfit
FROM Sales_Data
GROUP BY Category;

----Shipping Mode Impact:
---To analyze the impact of shipping modes on customer satisfaction, 
---sales, and profit, you can group the data by shipping mode and calculate relevant metrics.
SELECT Ship_Mode, AVG(CustomerSatisfaction) AS AvgSatisfaction, SUM(Sales) AS TotalSales, SUM(Profit) AS TotalProfit
FROM Sales_Data
GROUP BY Ship_Mode;
