# CTE - Common Table Expression
Subqueries receive an identifier and can be used in multiple places throughout the query.

## Use Cases
- make queries easier to read (refactor subqueries to create more readable code)
- create a temporary view or table
- create reusable modules

> CTEs can also be referenced in other CTEs that are written down later

## Creating CTEs
```sql
    -- create CTEs using the 'WITH' statement
    WITH cteName AS (
        -- select query goes here (no semi-colon)
    )

    -- use CTEs like a common table
    SELECT * FROM cteName;
```
## Writing more than one CTE
```sql
    WITH cteName AS (

    ), cteName2 AS (

    )
    -- don't forget the comma
    -- don't use the 'WITH' keyword a second time
```

## Example: Reusable Module
```sql
    WITH currentProducts AS (
      SELECT ProductName, CategoryName, UnitPrice, UnitsInStock FROM Products
        JOIN Categories ON Products.CategoryID = Categories.ID
        WHERE Products.Discontinued = 0
    )

    SELECT CategoryName, COUNT(1) AS productCount, SUM(UnitsInStock) AS productStock
      FROM currentProducts
      GROUP BY CategoryName
      ORDER BY productCount;
```

## Example: Refactored Subqueries
```sql
    WITH all_orders AS (
        SELECT EmployeeID, COUNT(*) AS order_count
        FROM Orders
        GROUP BY EmployeeID
    ), late_orders AS (
        SELECT EmployeeID, COUNT(*) AS order_count
        FROM Orders
        WHERE RequiredDate <= ShippedDate
        GROUP BY EmployeeID
    )

    SELECT Employees.ID, LastName,
      all_orders.order_count AS totalOrders,
      late_orders.order_count AS lateOrders
      FROM Employees
      JOIN all_orders ON Employees.ID = all_orders.EmployeeID
      JOIN late_orders ON Employees.ID = late_orders.EmployeeID;
```

## Example: Using CTEs inside of CTEs
```sql
    WITH all_sales AS (
      SELECT
          Orders.ID AS OrderID,
          Orders.EmployeeID,
          SUM(OrderDetails.UnitPrice * OrderDetails.Quantity) AS invoice_total
        FROM Orders
        JOIN OrderDetails ON Orders.ID = OrderDetails.OrderID
        GROUP BY Orders.ID
    ), revenue_by_employee AS (
      SELECT EmployeeID, ROUND(SUM(invoice_total), 2) AS total_revenue
        FROM all_sales
        GROUP BY EmployeeID
    ), sales_by_employee AS (
      SELECT EmployeeID, COUNT(1) AS sales_count FROM all_sales
        GROUP BY EmployeeID
    )

    SELECT Employees.LastName,
        s.*,
        r.total_revenue,
        ROUND(r.total_revenue / s.sales_count, 2) AS average_revenue_per_order
      FROM sales_by_employee AS s
      JOIN revenue_by_employee AS r ON r.EmployeeID = s.EmployeeID
      JOIN Employees ON r.EmployeeID = Employees.Id
      ORDER BY r.total_revenue DESC;
```
