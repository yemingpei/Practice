### LeetCode-300-Longest-Increasing-Subsequence

> 题目链接

[LeetCode-300-Longest-Increasing-Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)

> 思路

```java
//输入数组为[10,9,2,5,3,7,101,18]，则d数组的变化顺序如下
//position=0,[10]
//position=1,[9]
//position=2,[2]
//position=3,[2,5]
//position=4,[2,3]
//position=5,[2,3,7]
//position=6,[2,3,7,101]
//position=7,[2,3,7,18]
```

辅助数组d保存数列的最小值，是单调递增的，利用二分法寻找第一个大于或者等于nums[i]的值，然后替换，如果nums[i] > d[len]，则直接插入

> 代码

```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        if(nums.length == 0) return 0;
        int len = 0, n = nums.length;
        int[] d = new int[n];
        d[len] = nums[0];
        for (int i = 1; i < n; i++) {
            if (nums[i] > d[len]) {
                d[++len] = nums[i];
            } else {
                d[getInsertPosition(0, len, nums[i], d)] = nums[i];
            }
        }
        return len + 1;
    }
    public int getInsertPosition(int left, int right, int number, int[] d){
        while(right > left){
            int mid = (left + right) >> 1;
            if(d[mid] >= number) right = mid;
            else left = mid + 1; 
        }
        return left;
    }
}
```

> 复杂度分析

遍历数组，然后每个循环内，通过二分法来寻找插入的位置，时间复杂度O(nlgn)

额外使用数组保存构建的最小数列，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 85.44% of Java online submissions for Longest Increasing Subsequence.

Memory Usage: 38.6 MB, less than 15.03% of Java online submissions for Longest Increasing Subsequence.
