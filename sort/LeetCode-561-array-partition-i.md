### LeetCode-561-array-partition-i

> 题目链接

[LeetCode-561-array-partition-i](https://leetcode-cn.com/problems/array-partition-i/)

> 思路

先排序 ，然后利用贪心算法，取奇数位置的数相加

> 代码

```java
class Solution {
    public int arrayPairSum(int[] nums) {
        Arrays.sort(nums);
        int sum = 0;
        for(int i = 0; i < nums.length; i+=2){
            sum += nums[i];
        }
        return sum;
    }
}
```

> 复杂度分析

利用排序，再遍历，时间复杂度O(nlogn)

额外使用int变量，空间复杂度O(1)

> 总结

执行用时：12 ms, 在所有 Java 提交中击败了98.24%的用户

内存消耗：40.5 MB, 在所有 Java 提交中击败了83.43%的用户
