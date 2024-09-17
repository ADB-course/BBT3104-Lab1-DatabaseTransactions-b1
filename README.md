[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/r-tQZu0l)
# BBT3104-Lab1of6-DatabaseTransactions


| **Key**                                                               | Value                                                                                                                                                                              |
|---------------|---------------------------------------------------------|
| **Group Name** 
B1                                                              | ? |
| **Semester Duration**                                                 | 19<sup>th</sup> August - 25<sup>th</sup> November 2024                                                                                                                       |

## Flowchart
start 
set isolation level: SERILAZABLE
select database: classicmodels
start transaction
Calculate Order Number
Calculate New Order
create SAVEPOINT before product 1
insert product 1 
create SAVEPOINT before product 2
insert product 2  
update stock for product 2 
Rollback to SAVEPOINT before product 2
create a SAVEPOINT before product 3 
insert product 3 
Update Stock for Product 3 
Receive Payment
commit Transaction
confirm results
End
## Pseudocode
BEGIN TRANSACTION
    SET TRANSACTION ISOLATION LEVEL SERIALIZABLE
    
    SELECT DATABASE classicmodels
    
    START TRANSACTION
    
  
    latest_order_number = MAX(orderNumber) FROM orders
    new_order_number = latest_order_number + 1
    INSERT INTO orders (orderNumber, orderDate, requiredDate, shippedDate, status, customerNumber)
    VALUES (new_order_number, CURRENT_DATE, DATE_ADD(CURRENT_DATE, INTERVAL 3 DAY), DATE_ADD(CURRENT_DATE, INTERVAL 2 DAY), 'In Process', 145)
## Support for the Sales Departments' Report
