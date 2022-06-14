Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

a.  How many orders were shipped by Speedy Express in total?

SELECT *

FROM Orders

LEFT JOIN Shippers

ON Orders.ShipperID = Shippers.ShipperID

WHERE ShipperName = "Speedy Express"


b.	What is the last name of the employee with the most orders?

SELECT Employees.LastName, Count(Orders.OrderID) As NumberOfOrders From Orders

INNER Join Employees ON Orders.EmployeeID = Employees.EmployeeID

Group by LastName Order by NumberOfOrders ASC

Limit 10;


c.	What product was ordered the most by customers in Germany?

SELECT p.ProductName, SUM(Quantity) AS TotalQuantity

FROM Orders AS o, OrderDetails AS od, Customers AS c, Products AS p

WHERE c.Country = "Germany" AND od.OrderID = o.OrderID AND od.ProductID = p.ProductID AND c.CustomerID = o.CustomerID

GROUP BY p.ProductID

ORDER BY TotalQuantity DESC

LIMIT 10;

