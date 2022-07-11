SELECT column1, column2   
FROM table_name  
WHERE conditions   
GROUP BY column1, column2   
HAVING conditions  
ORDER BY column1, column2;

1. Get department number wise total salarys.

  ``` SQL 
  select DEPTNO , sum(sal) Total_sal 
from EMP
group by deptno
```
![image](https://user-images.githubusercontent.com/96119184/178267717-8056e3eb-ca27-48bf-bdcd-f18c6d2d1623.png)


2. Get department number wise salarys with more than 10000 salary expenditure.
3. Get department number wise salarys with more than 10000 salary expenditure sorting department number fro small to big.
