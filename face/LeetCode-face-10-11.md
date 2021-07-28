### LeetCode-face-10-11

> 题目链接

[LeetCode-face-10-11](https://leetcode-cn.com/problems/peaks-and-valleys-lcci/)

> 思路

通过判断前后位置的大小关系，调整两者的位置，达到峰和谷交错的效果

> 代码

```java
class Solution {
    public void wiggleSort(int[] nums) {
        for(int i = 1; i < nums.length; i++){
            if(((i & 1) == 0 && nums[i] < nums[i-1])||((i & 1) == 1 && nums[i] > nums[i-1])){
                int temp = nums[i];
                nums[i] = nums[i-1];
                nums[i-1] = temp;
            }
        }
    }
}
```

> 复杂度分析

遍历了一次数组，时间复杂度O(n)

无额外使用空间，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.9 MB, 在所有 Java 提交中击败了97.30%的用户
