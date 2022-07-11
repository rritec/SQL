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


2. Get department number wise salarys with more than 1000 salary expenditure.

    ``` SQL
 select DEPTNO , sum(sal) Total_sal 
from EMP 
where SAL > 1000
group by deptno
```
![image](https://user-images.githubusercontent.com/96119184/178273018-7a6d94e9-11d9-46ca-8aa3-23de40d0bde6.png)

3. Get department number wise salarys with more than 10000 salary expenditure sorting department number fro small to big.
