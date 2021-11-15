### LeetCode-523-continuous-subarray-sum

> 题目链接

[LeetCode-523-continuous-subarray-sum](https://leetcode-cn.com/problems/continuous-subarray-sum/)

> 思路

计算前缀和，然后记录余数和对应的位置，如果余数相同，位置相差超过2，则输出

> 代码

```java
class Solution {
    public boolean checkSubarraySum(int[] nums, int k) {
        int m = nums.length;
        if (m < 2) {
            return false;
        }
        Map<Integer, Integer> map = new HashMap<Integer, Integer>();
        map.put(0, -1);
        int remainder = 0;
        for (int i = 0; i < m; i++) {
            remainder = (remainder + nums[i]) % k;
            if (map.containsKey(remainder)) {
                int prevIndex = map.get(remainder);
                if (i - prevIndex >= 2) {
                    return true;
                }
            } else {
                map.put(remainder, i);
            }
        }
        return false;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用map，空间复杂度O(n)

> 总结

执行用时：15 ms, 在所有 Java 提交中击败了70.64%的用户

内存消耗：54.4 MB, 在所有 Java 提交中击败了53.25%的用户
