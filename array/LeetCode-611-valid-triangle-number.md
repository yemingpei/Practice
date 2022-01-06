### LeetCode-611-valid-triangle-number

> 题目链接

[LeetCode-611-valid-triangle-number](https://leetcode-cn.com/problems/valid-triangle-number/)

> 思路

先排序，然后利用二分查找第三个值，用map来记录寻找过的位置

> 代码

```java
class Solution {
    public int triangleNumber(int[] nums) {
        int[] map = new int[2001];
        Arrays.sort(nums);
        int result = 0;
        for(int low = 0; low < nums.length; low++)
            for(int mid = low + 1; mid < nums.length; mid++){
                int num = nums[low] + nums[mid];
                int position = map[num] != 0 ? map[num] : findPosition(num, nums);
                map[num] = position;
                result += Math.max(0, position - mid);
            }
        return result;
    }
    public int findPosition(int target, int[] nums){
        int left = 0;
        int right = nums.length - 1;
        while(left < right){
            int mid = (right + left) / 2 + 1;
            if(nums[mid] >= target) right = mid - 1;
            else left = mid;
        }
        return left;
    }
}
```

> 复杂度分析

利用排序和二分查找和记忆法，时间复杂度O(n ^ 2 logn)

额外使用固定长度的数组，空间复杂度O(1)

> 总结

执行用时：27 ms, 在所有 Java 提交中击败了99.22%的用户

内存消耗：38.6 MB, 在所有 Java 提交中击败了5.43%的用户
