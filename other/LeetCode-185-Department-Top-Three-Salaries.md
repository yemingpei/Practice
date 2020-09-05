### LeetCode-185-Department-Top-Three-Salaries

> 题目链接

[LeetCode-185-Department-Top-Three-Salaries](https://leetcode.com/problems/department-top-three-salaries/)

> 思路

SQL如下

> 代码

```java
SELECT d.Name AS 'Department', e1.Name AS 'Employee', e1.Salary
FROM Employee e1 JOIN Department d ON e1.DepartmentId = d.Id
WHERE 3 > (SELECT
             COUNT(DISTINCT e2.Salary)
             FROM Employee e2
             WHERE e2.Salary > e1.Salary AND e1.DepartmentId = e2.DepartmentId
       );
```

> 总结

Runtime: 700 ms, faster than 90.79% of MySQL online submissions for Department Top Three Salaries.

Memory Usage: 0B, less than 100.00% of MySQL online submissions for Department Top Three Salaries.
