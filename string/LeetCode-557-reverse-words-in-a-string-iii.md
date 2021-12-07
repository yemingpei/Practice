### LeetCode-557-reverse-words-in-a-string-iii

> 题目链接

[LeetCode-557-reverse-words-in-a-string-iii](https://leetcode-cn.com/problems/reverse-words-in-a-string-iii/)

> 思路

遍历字符串，然后开始逆转单词，遇到空格就交换一次，并重置开始的位置

> 代码

```java
class Solution {
    public String reverseWords(String s) {
        char[] text = s.toCharArray();
        int left = 0;
        for(int i = 0; i < text.length; i++){
            if(text[i] == ' '){
                swap(left, i - 1, text);
                left = text.length;
            }else if(left == text.length){
                left = i;
            }
        }
        swap(left, text.length - 1, text);
        return new String(text);
    }
    public void swap(int left, int right,char[] result){
        while(right > left){
            char c = result[right];
            result[right] = result[left];
            result[left] = c;
            right--;
            left++;
        }
    }
}
```

> 复杂度分析

遍历字符串两次，时间复杂度O(n)

额外使用char数组，空间复杂度O(n)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了95.30%的用户

内存消耗：39 MB, 在所有 Java 提交中击败了59.38%的用户
