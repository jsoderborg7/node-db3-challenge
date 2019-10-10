# Database Queries

### Display the ProductName and CategoryName for all products in the database. Shows 76 records.

select p.productName, c.categoryName 
from [products] as p 
join categories as c 
on p.categoryId = c.categoryId

### Display the OrderID and ShipperName for all orders placed before January 9, 1997. Shows 161 records.

select o.orderId, s.shipperName
from [orders] as o
join shippers as s
on o.shipperId = s.shipperId
where o.orderDate < '1997-01-09'

### Display all ProductNames and Quantities placed on order 10251. Sort by ProductName. Shows 3 records.

select p.productName, od.quantity
from [orderDetails] as od
join products as p
on od.productId = p.productId
where od.orderId = 10251
order by p.productName

### Display the OrderID, CustomerName and the employee's LastName for every order. All columns should be labeled clearly. Displays 196 records.

select o.orderId, c.customerName, e.lastName
from [orders] as o
join customers as c
on o.customerId = c.customerId
join employees as e
on o.employeeId = e.employeeId

### (Stretch)  Displays CategoryName and a new column called Count that shows how many products are in each category. Shows 9 records.

select c.categoryName, c.categoryId, Count(p.productId)
as [Count] from products as p
join categories as c 
on p.categoryId = c.categoryId
group by c.categoryId

### (Stretch) Display OrderID and a  column called ItemCount that shows the total number of products placed on the order. Shows 196 records. 

select orderId, Sum(quantity)
as [ItemCount] 
from orderDetails
group by orderId