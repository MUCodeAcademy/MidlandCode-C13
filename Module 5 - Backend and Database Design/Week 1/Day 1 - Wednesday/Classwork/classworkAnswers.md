# Time to put some of the SQL Work into Practice

Head on over to the [SQL Practice Site](https://www.w3schools.com/sql/trysql.asp?filename=trysql_desc). This site has prebuilt tables that will work out quite nicely for what we want to do.

Rather than have you try to hop back and forth, here's an overview of each of the tables:

| CUSTOMERS  |              |             |         |      |            |         |
| ---------- | ------------ | ----------- | ------- | ---- | ---------- | ------- |
| CustomerID | CustomerName | ContactName | Address | City | PostalCode | Country |

| CATEGORIES |              |             |
| ---------- | ------------ | ----------- |
| CategoryID | CategoryName | Description |

| EMPLOYEES  |          |           |           |       |       |
| ---------- | -------- | --------- | --------- | ----- | ----- |
| EmployeeID | LastName | FirstName | BirthDate | Photo | Notes |

| ORDERDETAILS  |         |           |          |
| ------------- | ------- | --------- | -------- |
| OrderDetailID | OrderID | ProductID | Quantity |

| ORDERS  |            |            |           |           |
| ------- | ---------- | ---------- | --------- | --------- |
| OrderID | CustomerID | EmployeeID | OrderDate | ShipperID |

| PRODUCTS  |             |            |            |      |       |
| --------- | ----------- | ---------- | ---------- | ---- | ----- |
| ProductID | ProductName | SupplierID | CategoryID | Unit | Price |

| SHIPPERS  |             |       |
| --------- | ----------- | ----- |
| ShipperID | ShipperName | Phone |

| SUPPLIERS  |              |         |      |            |         |     |
| ---------- | ------------ | ------- | ---- | ---------- | ------- | --- |
| SupplierID | SupplierName | Address | City | PostalCode | Country |

## Now that we know our Schema, let's do the following (making sure that the table returns all useful data, not just the bare minimum)

1. Find all Customers in the USA or Mexico ordered Alphabetically by Contact Name

```SQL
SELECT * FROM Customers 
WHERE Country = 'Mexico' 
OR Country = 'USA'
ORDER BY ContactName ASC;
```

2. Find all Products that cost more than 40

```SQL
SELECT * FROM Products
WHERE Price > 40
```

3. Find all Employees born before 1960.
<!-- 
SOMETHING IS WRONG WITH THE TABLE ON THE WEBSITE
THIS SHOULD BE HOW IT'S WRITTEN
 -->
```SQL
SELECT * FROM Employees
WHERE BirthDate < '1960-01-01';
```

4. Find all Products that are Beverages

```SQL
SELECT * FROM Products
JOIN Categories ON Products.CategoryID = Categories.CategoryID
WHERE Categories.CategoryID = 1;
```

5. Find all Employees who have ordered something that shipped to Spain

```SQL
SELECT * FROM Employees
JOIN Orders ON Orders.EmployeeID = Employees.EmployeeID
JOIN Customers ON Customers.CustomerID = Orders.CustomerID
WHERE Customers.Country = "Spain";
```

6. Find all Orders with a total price over 2000 sorted from most expensive to least expensive.

```SQL
SELECT OrderDetails.OrderID, 
SUM(OrderDetails.Quantity * Products.Price) AS Total
FROM OrderDetails
JOIN Products ON Products.ProductID = OrderDetails.ProductID
GROUP BY OrderDetails.OrderID
HAVING Total > 2000
ORDER BY Total DESC;
```
