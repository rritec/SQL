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


10. Get  salary employees entire information.

``` SQL
select * from (SELECT e.*,
   DENSE_RANK() OVER (ORDER BY sal asc) AS DENSE_Rnk
FROM emp as e) as sub_query

```


![image](https://user-images.githubusercontent.com/20516321/193268634-63b65e9d-9cce-4f55-8539-1605eb572b14.png)

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
```SQL
**Use query to create table**

create table test (
Deptno int,
Dname varchar(225),
Loc varchar(225)
);
```
```SQL
**Inserting dupilcate values into table**

Insert into test (Deptno , Dname , Loc) values(10 , 'ACCOUNTING' , 'NEW YORK')
Insert into test (Deptno , Dname , Loc) values(10 , 'ACCOUNTING' , 'NEW YORK')
Insert into test (Deptno , Dname , Loc) values(20 , 'clerk' , 'india')
Insert into test (Deptno , Dname , Loc) values(20 , 'clerk' , 'india')
```
![image](https://user-images.githubusercontent.com/96119184/181483849-7f0d58e6-46d0-482b-b680-a9a7d46f2b91.png)

```SQL
**Use query to remove duplicate rows from table**

 WITH CTE AS
(
SELECT *,ROW_NUMBER() OVER (PARTITION BY DEPTNO , DNAME , LOC ORDER BY DEPTNO , DNAME , LOC) AS RN
FROM test
)
DELETE FROM CTE WHERE RN<>1
```
**After removing duplicate rows from table**

```SQL
Select * from test
```

![image](https://user-images.githubusercontent.com/96119184/181487449-9c8f53f6-fc33-4ce1-b2f1-0265b81ec198.png)


14. How to convert Date datatype to Char datatype?

``` SQL
select HIREDATE, cast( HIREDATE as char(11)) as 'Convertedhiredate' 
from EMP
```
![image](https://user-images.githubusercontent.com/96119184/181229731-2d655d65-7208-49ec-beb0-6b3324dcc3dd.png)



15. How to convert Char datatype to date?

```SQL
SELECT [Convertedhiredate],
      CAST([Convertedhiredate] AS date) as 'Date-CAST'      
FROM [dbo].[test123]
```

![image](https://user-images.githubusercontent.com/96119184/181243046-5c31acd2-a6dd-4b18-a165-79c8f96fa8bb.png)

16. How to convert Int datatype float?

```SQL

Select SAL, CAST(SAL as int) as 'converting int to float'
 from EMP
```

![image](https://user-images.githubusercontent.com/96119184/181489643-62eed295-6c20-4f57-b3ab-93fc2db9a5e8.png)


17. What is the difference between Union and Union all?

```SQL

select * from emp10
union 
select * from emp10
```


![image](https://user-images.githubusercontent.com/96119184/181237409-e69bf636-5962-414b-94cf-1465f5246980.png)


```SQL

select * from emp10
union all
select * from emp10
```

![image](https://user-images.githubusercontent.com/96119184/181237845-ddf55d86-c1c6-40bb-8357-f298e0971be4.png)


18. Get deptatment wise totalsal, for all departments.

```SQL
select 
      deptno,
	  SUM(sal) as Total_salary
	  from EMP
	  Group by DEPTNO
```

![image](https://user-images.githubusercontent.com/96119184/181241083-10221170-ad53-4467-9885-f0afea0b70f0.png)

18. Get deptatment name wise totalsal, for all department names.

```SQL
  Select dname,round(isnull(sum(sal),0),4) as total_sal
from emp Right outer join dept
on emp.deptno=dept.deptno
group by DNAME

```
![image](https://user-images.githubusercontent.com/96119184/181463904-43d8656c-8586-4aaa-b027-64b556b9788e.png)


19. Create table using SQL Query Result?

```SQL
SELECT HIREDATE, cast( HIREDATE as char(11)) as 'Convertedhiredate' INTO [dbo].[test123] FROM [dbo].[EMP];
```
20. Round the number to 2 decimal places?

```SQL
SELECT ROUND(235.415, 2) AS RoundValue;
```

![image](https://user-images.githubusercontent.com/96119184/181465079-bb72e3cd-1cbb-45ff-9897-e02a029565c2.png)










