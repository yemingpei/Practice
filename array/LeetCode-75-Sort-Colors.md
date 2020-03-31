### LeetCode-75-Sort-Colors

> 题目链接

[LeetCode-75-Sort-Colors](https://leetcode.com/problems/sort-colors/)

> 思路

左右边界指针和中间移动指针，寻找到0，则和前面的交换，寻找到2就和后面的交换

> 代码

```java
class Solution {
    public void sortColors(int[] nums) {
        if(nums.length<2) return;
        int red = 0;
        int blue = nums.length - 1;
        int start = 0;
        while (start <= blue) {
          if (nums[start] == 1)
            start++;
          else if (nums[start] == 0) {
            nums[start++] = nums[red];
            nums[red++] = 0;
          } else {
            nums[start] = nums[blue];
            nums[blue--] = 2;
          }
        }
	}

}
```

> 复杂度分析

遍历了一轮数组，时间复杂度O(n)
额外使用三个int类型记录位置，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Sort Colors.
Memory Usage: 38.3 MB, less than 5.51% of Java online submissions for Sort Colors.
