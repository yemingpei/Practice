### LeetCode-182-Duplicate-Emails

> 题目链接

[LeetCode-182-Duplicate-Emails](https://leetcode.com/problems/duplicate-emails/)

> 思路

SQL如下

> 代码

```java
SELECT Email from Person
GROUP BY Email 
HAVING Count(*) > 1
```

> 总结

Runtime: 337 ms, faster than 86.95% of MySQL online submissions for Duplicate Emails.

Memory Usage: 0B, less than 100.00% of MySQL online submissions for Duplicate Emails.
