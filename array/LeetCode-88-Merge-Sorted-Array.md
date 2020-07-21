### LeetCode-88-Merge-Sorted-Array

> 题目链接

[LeetCode-88-Merge-Sorted-Array](https://leetcode.com/problems/merge-sorted-array/)

> 思路

因为要填满数组1，倒序从尾部开始填，寻找数组1和数组2的最大的值，填在尾部，然后右边界减1

> 代码

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int position1 = m - 1;
        int position2 = n - 1;
        for(int i = nums1.length - 1; i >= 0; i--){
            if(position1 >= 0 && position2 >= 0){
                if(nums1[position1] >= nums2[position2]){
                    nums1[i] = nums1[position1];
                    position1--;
                }else{
                    nums1[i] = nums2[position2];
                    position2--;
                }
            }else if(position1 >= 0){
                nums1[i] = nums1[position1];
                position1--;
            }else{
                nums1[i] = nums2[position2];
                position2--;
            }
        }
    }
}
```

> 复杂度分析

遍历一遍数组1和数组2，长度之和为数组1的长度，O(n)

无额外使用空间保存，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Merge Sorted Array.

Memory Usage: 39.3 MB, less than 82.53% of Java online submissions for Merge Sorted Array.
