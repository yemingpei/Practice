### LeetCode-385-Mini-Parser

> 题目链接

[LeetCode-385-Mini-Parser](https://leetcode.com/problems/mini-parser/)

> 思路

递归寻找值和被嵌套的值，需要找到尾部的]来截取，继续递归

> 代码

```java
class Solution {
    public NestedInteger deserialize(String s) {
        if(s.charAt(0) != '[') return new NestedInteger(Integer.valueOf(s));
        NestedInteger ni = new NestedInteger();
        int i = 0;
        int open = 0;
        int start = -1;
        while(i < s.length()){
            if(s.charAt(i) == '['){
                if(open++ == 1) start = i;
            }else if(s.charAt(i) == ']'){
                if(--open == 1) ni.add(deserialize(s.substring(start, i + 1)));
            }else if(open == 1 && s.charAt(i) != ','){
                int val = 0;
                boolean neg = false;
                if(s.charAt(i) == '-'){
                    neg = true;
                    i++;
                }
                while(i < s.length() && 
                      s.charAt(i) >= '0' && s.charAt(i) <= '9'){
                    val = val * 10 + (s.charAt(i++) - '0');
                }
                if(neg) val *= -1;
                ni.add(new NestedInteger(val));
                i--;
            }
            i++;
        }
        return ni;
    }
}
```

> 复杂度分析

循环遍历1到n，时间复杂度O(n)

额外使用常量定值，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Mini Parser.

Memory Usage: 39.2 MB, less than 96.82% of Java online submissions for Mini Parser.
