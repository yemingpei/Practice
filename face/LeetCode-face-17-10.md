### LeetCode-face-17-10

> 题目链接

[LeetCode-face-17-10](https://leetcode-cn.com/problems/find-majority-element-lcci/)

> 思路

摩尔投票法，选出超过一半的数字，然后再遍历，验证是否存在该数

> 代码

```java
class Solution {
    public int majorityElement(int[] nums) {
        if(nums.length == 0) return -1;
        int result = nums[0];
        int count = 1;
        for(int i = 1; i < nums.length; i++){
            if(nums[i] == result) count++;
            else count--;
            if(count < 0){
                count = 1;
                result = nums[i];
            }
        }
        count = 0;
        for(int i = 0; i < nums.length; i++){
            if(nums[i] == result) count++;
        }
        return count > nums.length / 2 ? result : -1;
    }
}
```

> 复杂度分析

遍历两次数组，时间复杂度O(n)

额外使用int值辅助，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：44.1 MB, 在所有 Java 提交中击败了48.23%的用户
