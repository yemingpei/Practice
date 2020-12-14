### LeetCode-345-Reverse-Vowels-of-a-String

> 题目链接

[LeetCode-345-Reverse-Vowels-of-a-String](https://leetcode.com/problems/reverse-vowels-of-a-string/)

> 思路

前后指针，分别找出前后位置的元音字母，然后交换位置

> 代码

```java
class Solution {
    public String reverseVowels(String s) {
        int i = 0;
        int j = s.length() - 1;
        char[] charArray = s.toCharArray();
        while(i < j) {
            while(!isVowel(s.charAt(i)) && i < j) {
                i++;
            } 
            while(!isVowel(s.charAt(j)) && i < j) {
                j--;
            }
            if(i < j){
                char temp = charArray[i];
                charArray[i] = charArray[j];
                charArray[j] = temp;
                i++;
                j--;
            }
        } 
        return String.valueOf(charArray);
    }
    
    public boolean isVowel(char c) {
        if(c=='a' || c=='e' || c=='i' || c=='o' || c=='u' || c=='A' || c=='E' || c=='I' || c=='O' || c=='U')
            return true;
        return false;
    }
}
```

> 复杂度分析

遍历整个字符串，时间复杂度O(n)

额外使用数组便于交换字符的位置，空间复杂度O(n)

> 总结

Runtime: 2 ms, faster than 99.44% of Java online submissions for Reverse Vowels of a String.

Memory Usage: 38.9 MB, less than 89.93% of Java online submissions for Reverse Vowels of a String.
