### LeetCode-176-Second-Highest-Salary

> 题目链接

[LeetCode-176-Second-Highest-Salary](https://leetcode.com/problems/second-highest-salary/)

> 思路

SQL如下

> 代码

```java
SELECT (SELECT DISTINCT
            Salary
        FROM
            Employee
        ORDER BY Salary DESC
        LIMIT 1 OFFSET 1) AS SecondHighestSalary
```

> 总结

Runtime: 207 ms, faster than 80.22% of MySQL online submissions for Second Highest Salary.

Memory Usage: 0B, less than 100.00% of MySQL online submissions for Second Highest Salary.
