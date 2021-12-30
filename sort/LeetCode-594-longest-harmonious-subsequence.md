### LeetCode-594-longest-harmonious-subsequence

> 题目链接

[LeetCode-594-longest-harmonious-subsequence](https://leetcode-cn.com/problems/longest-harmonious-subsequence/)

> 思路

排序，然后利用滑动窗口寻找最长的区间

> 代码

```java
class Solution {
    public int findLHS(int[] nums) {
        Arrays.sort(nums);
        int begin = 0,res = 0;
        for(int end = 0;end < nums.length;end++){
            while(nums[end] - nums[begin] > 1)
                 begin++;
            if(nums[end] - nums[begin] == 1)
              res = Math.max(res,end - begin + 1);
        }
        return res;
    }
}
```

> 复杂度分析

使用排序，时间复杂度O(nlogn)

额外使用常量的int，空间复杂度O(1)

> 总结

执行用时：13 ms, 在所有 Java 提交中击败了96.34%的用户

内存消耗：39.3 MB, 在所有 Java 提交中击败了49.41%的用户
