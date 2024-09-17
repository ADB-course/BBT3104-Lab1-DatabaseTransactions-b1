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
test
## Support for the Sales Departments' Report
