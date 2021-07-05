### LeetCode-face-05-03

> 题目链接

[LeetCode-face-05-03](https://leetcode-cn.com/problems/reverse-bits-lcci/)

> 思路

两个计数器，一个计算连续的1，一个计算拼接的值，重置的时候，前一个是后一个的起点

> 代码

```java
class Solution {
    public int reverseBits(int num) {
        int sum = 0;
        int max = 0;
        int pre = 0;
        for(int i = 0; i < 32; i++){
            if((num & 1) == 1){
                sum++;
                pre++;
            }else{
                sum = pre + 1;
                pre = 0;
            }
            max = Math.max(max, sum);
            num >>= 1;
        }
        return max;
    }
}
```

> 复杂度分析

计算了32次，时间复杂度O(1) 

额外使用int常量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.3 MB, 在所有 Java 提交中击败了28.62%的用户
