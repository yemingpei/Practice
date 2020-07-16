### LeetCode-71-Simplify-Path

> 题目链接

[LeetCode-71-Simplify-Path](https://leetcode.com/problems/simplify-path/)

> 思路

遍历字符串进行简化，处理.和 ..和/相，以及组合产生的字串

> 代码

```java
class Solution {
    public String simplifyPath(String path) {
        StringBuilder sb=new StringBuilder();
        int idx=path.length()-1;
        int skip=0;
        while (idx>=0){
            char ch=path.charAt(idx);
            if (ch=='.') {
                if (path.charAt(idx-1)=='.'){
                    if (idx>2 && path.charAt(idx-2)=='.') {
                        while(path.charAt(idx)=='.'){
                            sb.append('.');
                            idx--;
                        }
                    } else{
                        skip++;
                        idx-=2;
                    }
                } else {
                    idx--;
                }
            } else if(ch=='/') {
               if (sb.length()>0 && sb.charAt(sb.length()-1)!='/') sb.append('/');
               idx--;
            } else {
                if (skip>0) {
                    skip--;
                    idx--;
                    while(path.charAt(idx)!='/') idx--;
                } else {
                    while(path.charAt(idx)!='/') sb.append(path.charAt(idx--));
                }
            }             
        }
        if (sb.length()==0) sb.append('/');
        return sb.reverse().toString();
    }
}
```

> 复杂度分析

遍历字符串推算，时间复杂度O(n)

额外使用int辅助，空间复杂度O(1)

> 总结

Runtime: 3 ms, faster than 96.09% of Java online submissions for Simplify Path.

Memory Usage: 40.1 MB, less than 24.67% of Java online submissions for Simplify Path.
