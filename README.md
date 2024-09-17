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
     SAVEPOINT before_product_1
      INSERT INTO orderdetails (orderNumber, productCode, quantityOrdered, priceEach, orderLineNumber)
    VALUES (new_order_number, 'S18_1749', 2724, 136, 1)
     quantity_in_stock = SELECT quantityInStock FROM products WHERE productCode = 'S18_1749'
    UPDATE products SET quantityInStock = quantity_in_stock - 2724 WHERE productCode = 'S18_1749'
     SAVEPOINT before_product_2
     INSERT INTO orderdetails (orderNumber, productCode, quantityOrdered, priceEach, orderLineNumber)
    VALUES (new_order_number, 'S18_2248', 540, 55.09, 2)
    quantity_in_stock = SELECT quantityInStock FROM products WHERE productCode = 'S18_2248'
    UPDATE products SET quantityInStock = quantity_in_stock - 540 WHERE productCode = 'S18_2248'
    ROLLBACK TO SAVEPOINT before_product_2
    SAVEPOINT before_product_3
    INSERT INTO orderdetails (orderNumber, productCode, quantityOrdered, priceEach, orderLineNumber)
    VALUES (new_order_number, 'S12_1099', 68, 95.34, 3)
    quantity_in_stock = SELECT quantityInStock FROM products WHERE productCode = 'S12_1099'
    UPDATE products SET quantityInStock = quantity_in_stock - 68 WHERE productCode = 'S12_1099'
     INSERT INTO payments (customerNumber, checkNumber, paymentDate, amount)
    VALUES (145, 'JM555210', CURRENT_DATE, 300000)
## Support for the Sales Departments' Report
