### LeetCode-178-Rank-Scores

> 题目链接

[LeetCode-178-Rank-Scores](https://leetcode.com/problems/rank-scores/)

> 思路

SQL如下

> 代码

```java
select Score, dense_rank() over (order by Score desc)  as `Rank`
from Scores;
```

> 总结

Runtime: 281 ms, faster than 81.45% of MySQL online submissions for Rank Scores.

Memory Usage: 0B, less than 100.00% of MySQL online submissions for Rank Scores.
