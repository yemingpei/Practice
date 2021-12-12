### LeetCode-560-subarray-sum-equals-k

> 题目链接

[LeetCode-560-subarray-sum-equals-k](https://leetcode-cn.com/problems/subarray-sum-equals-k/)

> 思路

利用前缀和，用map记录数据，优化时间复杂度

> 代码

```java
class Solution {
    Map<Integer, Integer> map = new HashMap<>();
    public int subarraySum(int[] nums, int k) {
        int count = 0;
        int sum = 0;
        map.put(k, 1);
        for(int i : nums){
            sum += i;
            int number = map.getOrDefault(sum, 0);
            count += number;
            int z = sum + k;
            map.put(z, map.getOrDefault(z, 0) + 1);
        }
        return count;
    }
}
```

> 复杂度分析

利用前缀和，时间复杂度O(n)

额外使用map，空间复杂度O(h)

> 总结

执行用时：23 ms, 在所有 Java 提交中击败了57.77%的用户

内存消耗：41.3 MB, 在所有 Java 提交中击败了35.38%的用户
