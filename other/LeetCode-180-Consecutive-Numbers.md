### LeetCode-180-Consecutive-Numbers

> 题目链接

[LeetCode-180-Consecutive-Numbers](https://leetcode.com/problems/consecutive-numbers/)

> 思路

SQL如下

> 代码

```java
SELECT DISTINCT
    l1.Num ConsecutiveNums
FROM
    Logs l1,
    Logs l2,
    Logs l3
WHERE
    l1.Id = l2.Id - 1
    AND l2.Id = l3.Id - 1
    AND l1.Num = l2.Num
    AND l2.Num = l3.Num
```

> 总结

Runtime: 418 ms, faster than 98.74% of MySQL online submissions for Consecutive Numbers.

Memory Usage: 0B, less than 100.00% of MySQL online submissions for Consecutive Numbers.
