### LeetCode-119-Pascal's-Triangle-II

> 题目链接

[LeetCode-119-Pascal's-Triangle-II](https://leetcode.com/problems/pascals-triangle-ii/)

> 思路

杨辉三角公式c（n,m）= (n-1)! / (m-1)!(n-m)!;也可以直接由上一行推算出来，用公式法要解决大数溢出的问题（int保存不了）

> 代码

```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> result = new ArrayList<>();
        for(int i =0;i<=rowIndex;i++){
           result.add(1);
           for(int j=i-1;j>=1;j--)
               result.set(j, result.get(j) + result.get(j-1));
        }
        return result;
    }
}
```

> 复杂度分析

遍历杨辉三角(n + 1) * n / 2个数字，时间复杂度O(n ^ 2)

需要list保存结果，空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Pascal's Triangle II.

Memory Usage: 37.4 MB, less than 8.90% of Java online submissions for Pascal's Triangle II.
