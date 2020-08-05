### LeetCode-120-Triangle

> 题目链接

[LeetCode-120-Triangle](https://leetcode.com/problems/triangle/)

> 思路

动态规划，从底到上来寻找最少的路径，动态规划公式为result[j] = Math.min(result[j], result[j + 1]) + triangle.get(i).get(j)

> 代码

```java
class Solution {
    public int minimumTotal(List<List<Integer>> triangle) {
        int[] result = new int[triangle.size() + 1];
        for(int i = triangle.size() - 1; i >= 0 ; i--){
            for(int j = 0; j < triangle.get(i).size(); j++){
                result[j] = Math.min(result[j], result[j + 1]) + triangle.get(i).get(j);
            }
        }
        return result[0];
    }
}
```

> 复杂度分析

遍历(n+1) * n / 2 个点，时间复杂度O(n ^ 2)

额外使用数组保存路径的和，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 96.84% of Java online submissions for Triangle.

Memory Usage: 40.8 MB, less than 5.00% of Java online submissions for Triangle.
