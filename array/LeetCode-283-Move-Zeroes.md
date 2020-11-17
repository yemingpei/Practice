### LeetCode-283-Move-Zeroes

> 题目链接

[LeetCode-283-Move-Zeroes](https://leetcode.com/problems/move-zeroes/)

> 思路

记录0的位置，和非0的数进行替换，后面再补0

> 代码

```java
class Solution {
    public void moveZeroes(int[] nums) {
        int zeroPosition = 0;
        for(int i = 0; i < nums.length; i++){
            if(nums[i] != 0){
                if(zeroPosition != i)
                    nums[zeroPosition] = nums[i];
                zeroPosition++;
            }
        }
        for(int i = zeroPosition; i < nums.length; i++){
            nums[i] = 0;
        }
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

需要记录0的位置来置换，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Move Zeroes.

Memory Usage: 39.2 MB, less than 77.53% of Java online submissions for Move Zeroes.
