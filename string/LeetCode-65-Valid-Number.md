### LeetCode-65-Valid-Number

> 题目链接

[LeetCode-65-Valid-Number](https://leetcode.com/problems/valid-number/)

> 思路

需要处理‘e’，‘+’，‘-’，‘.’和数字，这几类字符，符号可以同时多个出现，如加减，加减要在数字之前，点只能有一个，而且必须在数字之后，e在数字之后

> 代码

```java
class Solution {
    public boolean isNumber(String s) {
        s = s.trim();
        boolean pointSeen = false;
        boolean eSeen = false;
        boolean numberSeen = false;
        boolean numberAfterE = false;
        for(int i=0; i<s.length(); i++) {
            if('0' <= s.charAt(i) && s.charAt(i) <= '9') {
                numberSeen = true;
                numberAfterE = true;
            } else if(s.charAt(i) == '.') { 
                if(eSeen || pointSeen) {
                    return false;
                }
                pointSeen = true;
            } else if(s.charAt(i) == 'e') { 
                if(eSeen || !numberSeen) {
                    return false;
                }
                numberAfterE = false;
                eSeen = true;
            } else if(s.charAt(i) == '-' || s.charAt(i) == '+') {
                if(i != 0 && s.charAt(i-1) != 'e') {
                    return false;
                }
            } else {
                return false;
            }
        }
    
        return numberSeen && numberAfterE;
    }
}
```

> 复杂度分析

遍历了一遍字符串，时间复杂度O(n)

额外使用4个boolean值来辅助，空间复杂度O(1)

> 总结

Runtime: 2 ms, faster than 89.12% of Java online submissions for Valid Number.

Memory Usage: 40.5 MB, less than 20.11% of Java online submissions for Valid Number.
