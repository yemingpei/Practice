### LeetCode-485-max-consecutive-ones

> 题目链接

[LeetCode-485-max-consecutive-ones](https://leetcode-cn.com/problems/max-consecutive-ones/)

> 思路

统计连续的1，不为1的时候更新一下count的大小

> 代码

```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int count = 0;
        int start = 0;
        for(int i : nums){
            if(i == 1){
                start++;
            }else{
                count = Math.max(count, start);
                start = 0;
            }
        }
        count = Math.max(count, start);
        return count;
    }
}
```

> 复杂度分析

遍历一遍数组，时间复杂度O(n)

额外使用int变量，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：39.8 MB, 在所有 Java 提交中击败了41.14%的用户
