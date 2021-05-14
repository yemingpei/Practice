### LeetCode-offer-57-II

> 题目链接

[LeetCode-offer-57-II](https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/)

> 思路

数组是有序的递增数组，然后通过(left + right) * (right - left + 1) / 2来计算和，如果比target小，则右边界移动，否则，左边界移动

> 代码

```java
class Solution {
    public int[][] findContinuousSequence(int target) {
        int left = 1;
        int right = 2;
        List<int[]> result = new ArrayList<>();
        while(right > left){
            int sum = (left + right) * (right - left + 1) / 2;
            if(sum == target){
                int[] number = new int[right - left + 1];
                int count = 0;
                for(int i = left;i <= right; i++) number[count++] = i;
                result.add(number);
                left++;
            }else if(sum < target) right++;
            else left++;
        }
        return result.toArray(new int[result.size()][]);
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用两个int边界值标记窗口，空间复杂度O(1)

> 总结

执行用时：4 ms, 在所有 Java 提交中击败了55.63%的用户

内存消耗：36.3 MB, 在所有 Java 提交中击败了95.34%的用户
