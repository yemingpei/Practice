### LeetCode-offer-39

> 题目链接

[LeetCode-offer-39](https://leetcode-cn.com/problems/shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof/)

> 思路

利用数字超过半数，抵消的原则，最后剩下的必然是最多的数

> 代码

```java
class Solution {
    public int majorityElement(int[] nums) {
        int result = nums[0];
        int count = 1;
        for(int i = 1; i < nums.length; i++){
            if(result == nums[i]) count++;
            else if(count == 0){
                result = nums[i];
                count = 1;
            }else{
                count--;
            }
        }
        return result;
    }
}
```

> 复杂度分析

遍历一遍数组，时间复杂度O(n)

额外使用两个int值来保存，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了99.97%的用户

内存消耗：41.9 MB, 在所有 Java 提交中击败了37.57%的用户
