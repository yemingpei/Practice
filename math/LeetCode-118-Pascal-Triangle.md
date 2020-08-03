### LeetCode-118-Pascal's-Triangle

> 题目链接

[LeetCode-118-Pascal's-Triangle](https://leetcode.com/problems/pascals-triangle/)

> 思路

杨辉三角公式c（n,m）= (n-1)! / (m-1)!(n-m)!;也可以直接由上一行推算出来

> 代码

```java
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> result = new ArrayList<>();
        if(numRows == 0) return result;
        List<Integer> row = new ArrayList<>();
        row.add(1);
        result.add(row);
        for(int i = 1; i < numRows; i++){
            List<Integer> list = new ArrayList<>();
            list.add(1);
            int count = i - 1;
            for(int j = 0; j < count; j++){
                list.add(result.get(i - 1).get(j) + result.get(i - 1).get(j + 1));
            }
            list.add(1);
            result.add(list);
        }
        return result;
    }
}
```

> 复杂度分析

需要遍历两重，时间复杂度O(n ^ 2)

需要二维数组来保存结果，空间复杂度O(n ^ 2)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Pascal's Triangle.

Memory Usage: 37.3 MB, less than 14.11% of Java online submissions for Pascal's Triangle.
