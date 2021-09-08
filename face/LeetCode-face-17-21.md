### LeetCode-face-17-21

> 题目链接

[LeetCode-face-17-21](https://leetcode-cn.com/problems/volume-of-histogram-lcci/)

> 思路

左右挡板，利用短板效应，不断移动边界。

> 代码

```java
class Solution {
    public int trap(int[] height) {
        if(height.length == 0) return 0;
        int count = 0;
        int left = 0;
        int right = height.length - 1;
        int minLeft = height[left];
        int minRight = height[right];
        while(left < right){
            if(minLeft < minRight){
                left++;
                if(height[left] < minLeft) count += minLeft - height[left];
                else minLeft = height[left];
            }else{
                right--;
                if(height[right] < minRight) count += minRight - height[right];
                else minRight = height[right];
            }
        }
        return count;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用int变量辅助，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了97.08%的用户

内存消耗：37.8 MB, 在所有 Java 提交中击败了89.82%的用户
