---
title: Leetcode MySql记录
date: 2020-09-30 21:07:40
tags: 
    - MySql 
    - Leetcode
categories: MySql 

keywords: 
    - MySql 
    - Leetcode
cover: https://s1.ax1x.com/2020/09/30/0KSEqO.jpg
---



### 1.超过经理收入的员工

```mysql
SELECT
    *
FROM
    Employee AS a,	（新颖）
    Employee AS b
WHERE
    a.ManagerId = b.Id
        AND a.Salary > b.Salary
```

### 2.删除重复数据

```mysql
delete a from Person a,Person b where a.Email = b.Email and a.id > b.id	
```

### 3.返回两个日期之间的天数（DATEDIFF）

```mysql
SELECT DATEDIFF('2008-12-30','2008-12-29') AS DiffDate
```

### 4.取第二高的薪水

offset X   是跳过X个数据  limit Y      是选取Y个数据

```mysql
SELECT
    IFNULL(
      (SELECT DISTINCT Salary
       FROM Employee
       ORDER BY Salary DESC
        LIMIT 1 OFFSET 1),
    NULL) AS SecondHighestSalary
```

### 5.实现分数排名

确定一个分数的排名，就是大于此分数的分数去重后的个数

```mysql
select a.Score as Score,
(select count(distinct b.Score) from Scores b where b.Score >= a.Score) as 'Rank'
from Scores a
order by a.Score DESC
```



















