### LeetCode-454-4sum-ii

> 题目链接

[LeetCode-454-4sum-ii](https://leetcode-cn.com/problems/4sum-ii/)

> 思路

四元组，必定每个数组都要出一个数字，所以，先分别统计A和B的两两之和，然后再统计C和D的，就转换成两数之和的题目了

> 代码

```java
class Solution {
    public int fourSumCount(int[] A, int[] B, int[] C, int[] D) {
        Map<Integer, Integer> countAB = new HashMap<Integer, Integer>();
        for (int u : A) {
            for (int v : B) {
                countAB.put(u + v, countAB.getOrDefault(u + v, 0) + 1);
            }
        }
        int ans = 0;
        for (int u : C) {
            for (int v : D) {
                if (countAB.containsKey(-u - v)) {
                    ans += countAB.get(-u - v);
                }
            }
        }
        return ans;
    }
}
```

> 复杂度分析

双重for循环，时间复杂度O(n ^ 2)

额外使用map辅助，空间复杂度O(n ^ 2)

> 总结

执行用时：124 ms, 在所有 Java 提交中击败了77.73%的用户

内存消耗：38.2 MB, 在所有 Java 提交中击败了96.04%的用户
