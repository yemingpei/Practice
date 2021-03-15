### LeetCode-offer-03

> 题目链接

[LeetCode-offer-03](https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/)

> 思路

交换数字，把对应的数字切换到对应的position的位置，如果相同，则提前结束

> 代码

```java
class Solution {
    public int findRepeatNumber(int[] nums) {
        int len = nums.length;
        int temp;
        for (int i = 0; i < len ; i++) {
            while (nums[i] != i) {
                if (nums[i] == nums[nums[i]]) {
                    return nums[i];
                }
                temp = nums[i];
                nums[i] = nums[nums[i]];
                nums[temp] = temp;
            }
        }
        return -1;
    }
}
```

> 复杂度分析

遍历数组交换位置，时间复杂度O(n)

无额外使用变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：45.8 MB, 在所有 Java 提交中击败了95.95%的用户
