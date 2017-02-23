# Topic:        Challenge Set 9, part 1
# Subject:      Pandas Challenges
# Date:         02/21/2017
# Name:         Rosie Hoyem

Which customers are from the UK?
```

```

What is the name of the customer who has the most orders?
```
SELECT CustomerName, COUNT(*) AS order_count
FROM Orders
JOIN Customers ON Orders.CustomerID = Customers.CustomerID
GROUP BY CustomerName
ORDER BY order_count DESC;
```

### Which supplier has the highest average product price?
```
SELECT SupplierName, AVG(Price) AS mean_unit_price
FROM Products
JOIN Suppliers ON Products.SupplierID = Suppliers.SupplierID
GROUP BY SupplierName
ORDER BY mean_unit_price DESC;
```

### How many different countries are all the customers from? (Hint: consider DISTINCT.)
```
SELECT COUNT(DISTINCT Country) AS 'Distinct Countries'
FROM Customers

### What category appears in the most orders?
```
SELECT CategoryID, COUNT(OrderDetails.OrderID) AS cat_count
FROM OrderDetails
JOIN Orders ON OrderDetails.OrderID = Orders.OrderID
JOIN Products ON OrderDetails.ProductID = Products.ProductID
GROUP BY CategoryID
ORDER BY cat_count DESC;
```

### What was the total cost for each order?
```
SELECT OrderID, Products.Price AS tot_cost
FROM OrderDetails
JOIN Products ON OrderDetails.ProductID = Products.ProductID
GROUP BY OrderID
```

### Which employee made the most sales (by total cost)?
```

```

### Which employees have BS degrees? (Hint: look at the LIKE operator.)
```
SELECT FirstName, LastName
FROM Employees
WHERE Notes LIKE "%BS%";
```

### Which supplier of three or more products has the highest average product price? (Hint: look at the HAVING operator.)
```
SELECT SupplierName, AVG(Products.Price) AS avg_price
FROM Suppliers
Join Products ON Suppliers.SupplierID = Products.SupplierID
GROUP BY Products.SupplierID
HAVING COUNT(ProductID) > 3
ORDER BY avg_price DESC;
```
