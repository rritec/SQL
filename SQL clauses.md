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

  ``` SQL
 select DEPTNO , sum(sal)  Total_sal 
from EMP
group by deptno 
having sum(SAL) > 10000
```

   
![image](https://user-images.githubusercontent.com/96119184/178311407-ac09fed7-5b75-41d7-a80d-d7a3b3b13009.png)


3. Get department number wise salarys with more than 10000 salary expenditure sorting department number from small to big.


``` SQL
select DEPTNO , sum(sal)  Total_sal 
from EMP
group by deptno 
having sum(SAL) > 10000
order by DEPTNO ASC
```
![image](https://user-images.githubusercontent.com/96119184/178312555-98551330-c09b-4cc0-8ade-bd7caa599b18.png)

4. Get department name wise total salarys.

``` SQL
 Select DNAME,sum(sal) Total_sal
 from emp,dept
 where emp.deptno=dept.deptno
 group by DNAME
```

 

![image](https://user-images.githubusercontent.com/96119184/178414291-0be452de-47f7-413b-81d7-5b1f786cd2d0.png)

   
5.  Get department name wise salarys with more than 10000 salary expenditure.

``` SQL
Select DNAME,sum(sal) Total_sal
from emp,dept
where emp.deptno=dept.deptno
group by DNAME
Having sum(SAL) > 10000
```

![image](https://user-images.githubusercontent.com/96119184/178414763-4d4024b7-1a2d-49f7-b07a-f4400adc779d.png)


6.  Get department number wise salarys with more than 10000 salary expenditure sorting department number from small to big.
```SQL
Select DNAME,sum(sal) Total_sal
from emp,dept
where emp.deptno=dept.deptno
group by DNAME
Having sum(SAL) > 10000
order by dname asc
```

![image](https://user-images.githubusercontent.com/96119184/178415075-7629cf0e-8e79-4da2-a858-85083c98d6b2.png)


7. Get All Department Names and count of employees in each department.

``` SQL
Select DNAME, count(ENAME) count_of_employess
from emp,dept
where emp.deptno=dept.deptno
group by DNAME
```

![image](https://user-images.githubusercontent.com/96119184/178429103-ebd52c17-13e0-4711-951c-55ef04cefe4e.png)


9. Get top salary employee entire information.


``` SQL
SELECT *
FROM emp
WHERE sal = (SELECT MAX(sal)
                FROM emp)
```

![image](https://user-images.githubusercontent.com/96119184/178471472-b6242384-4963-4538-83a0-3a96db8635cf.png)


10. Get top 2nd salary employee entire information.

``` SQL
select * from (SELECT e.*,
   DENSE_RANK() OVER (ORDER BY sal Desc) AS Rnk
FROM emp as e) as sub_query
where rnk=2
```


![image](https://user-images.githubusercontent.com/96119184/178485441-ed63a9b4-6a1e-4bf4-982d-607fd4b07b81.png)

11. Get bottom salary employee entire information.
``` SQL
SELECT *
FROM emp
WHERE sal = (SELECT Min(sal)
                FROM emp)
```

![image](https://user-images.githubusercontent.com/96119184/178472104-02384a6f-9324-43c3-b0c8-d8032216411f.png)



12. Get bottom 2nd salary employee entire information.

``` SQL
select * from (SELECT e.*,
   DENSE_RANK() OVER (ORDER BY sal asc) AS Rnk
FROM emp as e) as sub_query
where rnk=2
```

![image](https://user-images.githubusercontent.com/96119184/178486037-0450f9a1-bf15-46fc-87c7-b88235b5a28d.png)

13. How to delete duplicate records from the table?
14. How to convert Date datatype to Char datatype?

``` SQL
select HIREDATE, cast( HIREDATE as char(11)) as 'Convertedhiredate' from EMP
```
![image](https://user-images.githubusercontent.com/96119184/181229731-2d655d65-7208-49ec-beb0-6b3324dcc3dd.png)



15. How to convert Char datatype to date?
16. How to convert Int datatype float?
17. What is the difference between Union and Union all?
18. Get deptatment wise totalsal, for all departments.
19. How to write query with sql result from one table to anpther table?

```SQL
SELECT HIREDATE, cast( HIREDATE as char(11)) as 'Convertedhiredate' INTO [dbo].[test123] FROM [dbo].[EMP];
``



