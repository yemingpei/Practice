### LeetCode-181-Employees-Earning-More-Than-Their-Managers

> 题目链接

[LeetCode-181-Employees-Earning-More-Than-Their-Managers](https://leetcode.com/problems/employees-earning-more-than-their-managers/)

> 思路

SQL如下

> 代码

```java
SELECT
     a.NAME AS Employee
FROM Employee AS a JOIN Employee AS b
     ON a.ManagerId = b.Id
     AND a.Salary > b.Salary
```

> 总结

Runtime: 300 ms, faster than 81.28% of MySQL online submissions for Employees Earning More Than Their Managers.

Memory Usage: 0B, less than 100.00% of MySQL online submissions for Employees Earning More Than Their Managers.
