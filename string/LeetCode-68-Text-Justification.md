### LeetCode-68-Text-Justification

> 题目链接

[LeetCode-68-Text-Justification](https://leetcode.com/problems/text-justification/)

> 思路

计算字符串和最大长度的关系，每个字符中间的距离为一个空格，不足以放下下一个单词时，已经加入的字符均分长度，若不能均分，左边要少于右边，最后一行特殊处理。

> 代码

```java
class Solution {
    public List<String> fullJustify(String[] words, int maxWidth) {
        List<String> res = new ArrayList<>();
        if(words==null || words.length==0)
            return res;
        int count = 0;
        int last = 0;
        for(int i=0;i<words.length;i++){
            if(count + words[i].length() + (i-last) > maxWidth){
                int space = 0;     
                int extraSpace = 0;     
                if(i-last-1 >0){
                    space = (maxWidth - count) / (i-last - 1);      
                    extraSpace = (maxWidth - count) % (i-last-1);
                }
 
                StringBuilder stringBuilder = new StringBuilder();
                for(int j=last;j<i;j++){
                    stringBuilder.append(words[j]);
                    if(j < i-1){
                        for(int m=0;m<space;m++){
                            stringBuilder.append(" ");
                        }
                        if(extraSpace >0)
                            stringBuilder.append(" ");
                        extraSpace--;
                    }
                }
                for(int j=stringBuilder.length();j<maxWidth;j++)
                    stringBuilder.append(" ");
 
                res.add(stringBuilder.toString());
                count = 0;
                last = i;
            }
            count += words[i].length();
        }
        StringBuilder str = new StringBuilder();
        for(int i=last;i<words.length;i++){
            str.append(words[i]);
            if(str.length()<maxWidth)
                str.append(" ");
        }
        for(int i=str.length();i<maxWidth;i++)
            str.append(" ");
        res.add(str.toString());
        return res;
    }
}
```

> 复杂度分析

需要遍历数组，时间复杂度O(n)

List来保存结果，空间复杂度O(n * m)

> 总结

Details 
Runtime: 0 ms, faster than 100.00% of Java online submissions for Text Justification.

Memory Usage: 39.1 MB, less than 19.24% of Java online submissions for Text Justification.
