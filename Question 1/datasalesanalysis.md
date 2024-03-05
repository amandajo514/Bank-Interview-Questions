### CNB BANK

----

##### Pre-Hire problem solving 
##### You may use any coding language you are comfortable with. Please provide the code and any supporting  documentation you feel necessary. You may format your submission in a document or via email. 

1. Problem: Sales Data Analysis 

----

**Scenario:**



You've been provided with two tables: Sales and Products. 

Sales Table: 

SaleID ProductID SaleDate Quantity Amount 

1 101 2023-01-05 2 120.50 

2 103 2023-01-07 1 75.20 

3 102 2023-01-10 3 180.00 

... ... ... ... ... 

Products Table: 

ProductID ProductName Category 

101 Widget A Electronics 

102 Widget B Home 

103 Widget C Electronics 

----

**Tasks:**

1) Write a command to retrieve the total number of sales and the total amount of sales made

```sql
SELECT COUNT(SaleID) AS TotalSales, SUM(Amount) AS TotalSalesAmount
FROM Sales;
```

🡆 This SQL query retrieves the count of SaleID (total number of sales) and the sum of Amount (total sales amount) from the Sales table.

2) Create a command that lists the total sales amount for each product category.

```sql
SELECT p.Category, SUM(s.Amount) AS TotalSalesAmount
FROM Sales s
INNER JOIN Products p ON s.ProductID = p.ProductID
GROUP BY p.Category;
```
    
🡆 This SQL query joins the Sales and Products tables on ProductID and then calculates the sum of Amount for each product category.


3) Find the total sales amount for each month in the year 2023. Display the results with month  names. 

```sql
SELECT 
    CASE 
        WHEN MONTH(SaleDate) = 1 THEN 'January'
        WHEN MONTH(SaleDate) = 2 THEN 'February'
        WHEN MONTH(SaleDate) = 3 THEN 'March'
        WHEN MONTH(SaleDate) = 4 THEN 'April'
        WHEN MONTH(SaleDate) = 5 THEN 'May'
        WHEN MONTH(SaleDate) = 6 THEN 'June'
        WHEN MONTH(SaleDate) = 7 THEN 'July'
        WHEN MONTH(SaleDate) = 8 THEN 'August'
        WHEN MONTH(SaleDate) = 9 THEN 'September'
        WHEN MONTH(SaleDate) = 10 THEN 'October'
        WHEN MONTH(SaleDate) = 11 THEN 'November'
        ELSE 'December'
    END AS MonthName,
    SUM(Amount) AS TotalSalesAmount
FROM Sales
WHERE YEAR(SaleDate) = 2023
GROUP BY MONTH(SaleDate);

```

🡆 This SQL query calculates the sum of Amount for each month in the year 2023 and displays the results with month names instead of month numbers.

4) Identify the top 3 best-selling products based on the total quantity sold. 

```sql
SELECT ProductID, SUM(Quantity) AS TotalQuantitySold 
FROM Sales  
GROUP BY ProductID  
ORDER BY TotalQuantitySold DESC  
LIMIT 3;
```

🡆 This SQL query calculates the total quantity sold for each product, orders the results by total quantity sold in descending order, and limits the output to the top 3 best-selling products.

5) Insert a new product into the Products table with the following details: 
ProductID: 104 
ProductName: Widget D 
Category: Office 

```sql
INSERT INTO Products (ProductID, ProductName, Category) 
VALUES (104, 'Widget D', 'Office');
```

🡆 This SQL command inserts a new record into the Products table with ProductID 104, ProductName 'Widget D', and Category 'Office'.

----

Please provide the commands for each task along with any necessary explanations or assumptions. 

