### LeetCode-66-Plus-One

> 题目链接

[LeetCode-66-Plus-One](https://leetcode.com/problems/plus-one/)

> 思路

从右往左遍历，确定是否需要进位，不需要提前跳出

> 代码

```java
class Solution {
    public int[] plusOne(int[] digits) {
        for(int i = digits.length - 1; i >= 0; i--){
            if(digits[i] < 9){
                digits[i] = digits[i] + 1;
                break;
            }else{
                digits[i] = 0;
            }
        }
        if(digits[0] == 0){
            int[] result = new int[digits.length + 1];
            result[0] = 1;
            for(int j = 0; j < digits.length; j++){
                result[j + 1] = digits[j];
            }
            return result;
        }
        return digits;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

存在最高位数进1，需要额外的数组空间，空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Plus One.

Memory Usage: 39.1 MB, less than 16.34% of Java online submissions for Plus One.
