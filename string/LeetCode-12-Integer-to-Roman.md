### LeetCode-12-Integer-to-Roman

> 题目链接

[LeetCode-12-Integer-to-Roman](https://leetcode.com/problems/integer-to-roman/)

> 思路

构建十进制和罗马数字的对应关系，然后一一匹配

> 代码

```java
class Solution {
    public String intToRoman(int num) {
        int[] values = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};    
        String[] symbols = {"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};
        StringBuilder sb = new StringBuilder();
        for(int i = 0; i < values.length  ;i++){
            while(values[i] <= num){
                num-=values[i];
                sb.append(symbols[i]);
            }
        }
        return sb.toString();
    }
}
```

> 复杂度分析

数字不超过3999，使用循环迭代，时间复杂度O(1)

额外使用两个长度是13的数组，空间复杂度O(1)

> 总结

Runtime: 4 ms, faster than 91.05% of Java online submissions for Integer to Roman.

Memory Usage: 39.2 MB, less than 68.70% of Java online submissions for Integer to Roman.
