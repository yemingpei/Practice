### LeetCode-525-contiguous-array

> 题目链接

[LeetCode-525-contiguous-array](https://leetcode-cn.com/problems/contiguous-array/)

> 思路

前缀和，利用两数相减，获取最长的子数组，0为-1，1为1寻找和为0的最长子数组

> 代码

```java
class Solution {
    public int findMaxLength(int[] nums) {
        int max = 0;
        int sum = 0;
        Map<Integer, Integer> map = new HashMap<>();
        for(int i = 0; i < nums.length; i++){
            if(nums[i] == 0) sum--;
            else sum++;
            if(sum == 0) max = i + 1;
            else{
                int number = map.getOrDefault(sum, -1);
                if(number == -1) map.put(sum, i);
                else max = Math.max(max, i - number);
            }
        }
        return max;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用map，空间复杂度O(n)

> 总结

执行用时：18 ms, 在所有 Java 提交中击败了92.69%的用户

内存消耗：47.5 MB, 在所有 Java 提交中击败了93.13%的用户
