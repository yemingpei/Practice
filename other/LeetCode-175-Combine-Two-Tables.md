### LeetCode-175-Combine-Two-Tables

> 题目链接

[LeetCode-175-Combine-Two-Tables](https://leetcode.com/problems/combine-two-tables/)

> 思路

SQL如下

> 代码

```java
select P.FirstName,P.Lastname,A.City,A.State from Person P left join Address A on P.PersonId = A.PersonId;
```

> 总结

Runtime: 303 ms, faster than 84.12% of MySQL online submissions for Combine Two Tables.

Memory Usage: 0B, less than 100.00% of MySQL online submissions for Combine Two Tables.
