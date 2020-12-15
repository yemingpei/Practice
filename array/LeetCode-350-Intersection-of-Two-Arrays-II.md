### LeetCode-350-Intersection-of-Two-Arrays-II

> 题目链接

[LeetCode-350-Intersection-of-Two-Arrays-II](https://leetcode.com/problems/intersection-of-two-arrays-ii/)

> 思路

先记录最短的数组的数据分布情况，然后再遍历长的数组，筛选出相同的元素

> 代码

```java
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        int length1 = nums1.length;
        int length2 = nums2.length;
        Map<Integer, Integer> map = new HashMap<>();
        if(length1 > length2)  return makeMap(map, nums2, nums1);
        else return makeMap(map, nums1, nums2);
    }
    public int[] makeMap(Map<Integer, Integer> map, int[] nums, int[] target){
        int[] result = new int[nums.length];
        int n = 0;
        for(int i: nums){
            map.put(i, map.getOrDefault(i, 0) + 1);
        }
        for(int j: target){
            if(map.containsKey(j) && map.get(j) > 0 && n < nums.length){
                map.put(j, map.get(j) - 1);
                result[n++] = j;
            }
        }
        return Arrays.copyOfRange(result, 0, n);
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n + m)

需要map来记录最短数组的次数，int来保存结果数据，空间复杂度O(n)

> 总结

Runtime: 2 ms, faster than 94.39% of Java online submissions for Intersection of Two Arrays II.

Memory Usage: 39.5 MB, less than 23.57% of Java online submissions for Intersection of Two Arrays II.
