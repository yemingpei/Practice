### LeetCode-38-Count-and-Say

> 题目链接

[LeetCode-38-Count-and-Say](https://leetcode.com/problems/count-and-say/)

> 思路

根据前一个值来推导想要的string

> 代码

```java
class Solution {
    public String countAndSay(int n) {
        String say = "1";
        for(int i = 1; i < n; i++)
            say = countAndSay(say);
        return say;
    }
    
    private String countAndSay(String s) {
        StringBuilder sb = new StringBuilder();
        int count = 1;
        char say = s.charAt(0);
        for(int i = 1; i < s.length(); i++) {
            if(say == s.charAt(i))
                count ++;
            else {
                sb.append(count);
                sb.append(say);
                count = 1;
                say = s.charAt(i);
            }
        }
        sb.append(count);
        sb.append(say);
        return sb.toString();
    }
}
```

> 复杂度分析

暴力推导法，时间复杂度O(n * m)

额外string变量保存值，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Count and Say.

Memory Usage: 36.9 MB, less than 68.35% of Java online submissions for Count and Say.
