### LeetCode-228-Summary-Ranges

> 题目链接

[LeetCode-228-Summary-Ranges](https://leetcode.com/problems/summary-ranges/)

> 思路

保存前一个起始数值，如果差不是1，则需要拼接，注意数组遍历完毕，最后也需要拼接一次

> 代码

```java
class Solution {
    public List<String> summaryRanges(int[] nums) {
        List<String> result = new ArrayList<>();
        if(nums.length > 0){
            int start = nums[0];
            StringBuilder sb = new StringBuilder(String.valueOf(start));
            for(int i = 1; i < nums.length; i++){
                int j = i - 1;
                if(nums[i] - nums[j] == 1) continue;
                if(start != nums[j]) {
                    sb.append("->");
                    sb.append(nums[j]);
                }
                result.add(sb.toString());
                start = nums[i];
                sb = new StringBuilder(String.valueOf(start));
            }
            if(start != nums[nums.length - 1]) {
                sb.append("->");
                sb.append(nums[nums.length - 1]);
            }
            result.add(sb.toString());
        }
        return result;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

需要常量int来记录起始位置，StringBuilder来拼接字串，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Summary Ranges.

Memory Usage: 37.1 MB, less than 13.90% of Java online submissions for Summary Ranges.
