### LeetCode-167-Two-Sum-II-Input-array-is-sorted

> 题目链接

[LeetCode-167-Two-Sum-II-Input-array-is-sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

> 思路

前后指针，寻找对应的和，如果numbers[start] + numbers[end] > target，前指针移动，numbers[start] + numbers[end] < target,后指针移动

> 代码

```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int start = 0;
        int end = numbers.length - 1;
        int[] result = new int[2];
        while(end > start){
            if(numbers[start] + numbers[end] == target){
                result[0] = start + 1;
                result[1] = end + 1;
                return result;
            }else if(numbers[start] + numbers[end] > target){
                end--;
            }else{
                start++;
            }
        }
        return result;
    }
}
```

> 复杂度分析

遍历一遍数组，应该为O(n)

无额外使用空间，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Two Sum II - Input array is sorted.

Memory Usage: 39.3 MB, less than 92.66% of Java online submissions for Two Sum II - Input array is sorted.
