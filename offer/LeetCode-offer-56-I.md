### LeetCode-offer-56-I

> 题目链接

[LeetCode-offer-56-I](https://leetcode-cn.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof/)

> 思路

异或运算，相同的数字会消掉，然后获取两个数的异或的值，获取最右边的1，来作分组，在遍历一次

> 代码

```java
class Solution {
    public int[] singleNumbers(int[] nums) {
        int temp = 0;
        for(int i: nums)
            temp ^= i;
        int flag = temp & (-temp);
        int res = 0;
        for(int i: nums){
            if((i  & flag) == 0)
                res ^= i;
        }
        return new int[]{res, temp^res};
    }
}
```

> 复杂度分析

遍历两遍数组，时间复杂度O(n)

额外使用两个常量来记录，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：40.1 MB, 在所有 Java 提交中击败了61.68%的用户
