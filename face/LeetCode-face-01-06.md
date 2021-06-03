### LeetCode-face-01-06

> 题目链接

[LeetCode-face-01-06](https://leetcode-cn.com/problems/compress-string-lcci/)

> 思路

遍历字符串，记录重复的字符出现的次数，在不相同的时候，做压缩处理

> 代码

```java
class Solution {
    public String compressString(String S) {
        if(S.length() < 3) return S;
        StringBuilder sb = new StringBuilder();
        char[] text = S.toCharArray();
        int position = 0;
        for(int i = 1; i < text.length; i++){
            if(text[i] != text[position]){
                sb.append(text[position]);
                sb.append(i - position);
                position = i;
            }
        }
        sb.append(text[position]);
        sb.append(text.length - position);
        return sb.length() < text.length ? sb.toString() : S;
    }
}
```

> 复杂度分析

遍历字符串，时间复杂度O(n)

额外使用char数组来辅助，空间复杂度O(n)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了98.40%的用户

内存消耗：38.3 MB, 在所有 Java 提交中击败了53.13%的用户
