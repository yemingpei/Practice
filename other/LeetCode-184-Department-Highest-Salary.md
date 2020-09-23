### LeetCode-184-Department-Highest-Salary

> 题目链接

[LeetCode-184-Department-Highest-Salary](https://leetcode.com/problems/department-highest-salary/)

> 思路

SQL如下

> 代码

```java
select dept.Name as Department, emp.Name as Employee, emp.Salary
from Employee as emp, Department as dept
where emp.DepartmentId = dept.Id
and (dept.Id, emp.Salary) in (
        select DepartmentId, max(Salary)
        from Employee 
        group by DepartmentId
);
```

> 总结

Runtime: 584 ms, faster than 88.68% of MySQL online submissions for Department Highest Salary.

Memory Usage: 0B, less than 100.00% of MySQL online submissions for Department Highest Salary.
