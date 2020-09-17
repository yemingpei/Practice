### LeetCode-177-Nth-Highest-Salary

> 题目链接

[LeetCode-177-Nth-Highest-Salary](https://leetcode.com/problems/nth-highest-salary/)

> 思路

SQL如下

> 代码

```java
CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN
    DECLARE M INT;
    SET M = N-1;
    RETURN(
        SELECT DISTINCT Salary FROM Employee ORDER BY Salary DESC LIMIT 1 OFFSET M
    );
END
```

> 总结

Runtime: 298 ms, faster than 98.74% of MySQL online submissions for Nth Highest Salary.

Memory Usage: 0B, less than 100.00% of MySQL online submissions for Nth Highest Salary.
