### LeetCode-offer-21

> 题目链接

[LeetCode-offer-21](https://leetcode-cn.com/problems/diao-zheng-shu-zu-shun-xu-shi-qi-shu-wei-yu-ou-shu-qian-mian-lcof/)

> 思路

左边寻找双数，右边寻找单数，然后交换位置

> 代码

```java
class Solution {
    public int[] exchange(int[] nums) {
        int left = 0;
        int right = nums.length - 1;
        while(right > left){
            while(left < right && (nums[left] & 1) == 1){
                left++;
            }
            while(left < right && (nums[right] & 1) == 0){
                right--;
            }
            if(right > left){
                int number = nums[left];
                nums[left] = nums[right];
                nums[right] = number;
                left++;
                right--;
            }
        }
        return nums;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

无额外使用变量，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了98.03%的用户

内存消耗：46.3 MB, 在所有 Java 提交中击败了67.93%的用户
