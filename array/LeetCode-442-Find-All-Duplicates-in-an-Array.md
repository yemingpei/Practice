### LeetCode-442-Find-All-Duplicates-in-an-Array

> 题目链接

[LeetCode-442-Find-All-Duplicates-in-an-Array](https://leetcode.com/problems/find-all-duplicates-in-an-array/)

> 思路

利用原数组，若出现过，标记为负数，检测该位置有没有被标记过，来判断是否重复

> 代码

```java
class Solution {
    public List<Integer> findDuplicates(int[] nums) {
        List<Integer> list = new ArrayList<>();
        for(int i = 0; i < nums.length; i++){
            int tmp = nums[i];
            if(tmp < 0) tmp *= -1;
            if(nums[tmp -1 ] < 0){
                list.add(tmp);
            }
            else{
                nums[tmp -1] *= -1;
            }
        }
        return list;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

在原数组上操作，空间复杂度O(1)

> 总结

Runtime: 4 ms, faster than 94.03% of Java online submissions for Find All Duplicates in an Array.

Memory Usage: 48.4 MB, less than 33.17% of Java online submissions for Find All Duplicates in an Array.
