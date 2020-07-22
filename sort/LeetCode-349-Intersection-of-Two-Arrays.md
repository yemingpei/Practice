### LeetCode-349-Intersection-of-Two-Arrays

> 题目链接

[LeetCode-349-Intersection-of-Two-Arrays](https://leetcode.com/problems/intersection-of-two-arrays/)

> 思路

先记录数组1出现的数字，然后再遍历数组2看是否存在

> 代码

```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        Set<Integer> set = new HashSet<>();
        for(int n:nums1){
            set.add(n);
        }
        int i = 0;
        for(int n:nums2){
            if(set.remove(n))
                nums2[i++] = n;
        }
        return Arrays.copyOfRange(nums2,0,i);
    }
}
```

> 复杂度分析

两个数组都遍历了一次，均摊时间复杂度O(m + n)

额外使用Set集合保存了一个数组的数据,空间复杂度O(n)

> 总结

Runtime: 2 ms, faster than 99.32% of Java online submissions for Intersection of Two Arrays.
Memory Usage: 41.1 MB, less than 6.75% of Java online submissions for Intersection of Two Arrays.
