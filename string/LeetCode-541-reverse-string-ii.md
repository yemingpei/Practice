### LeetCode-541-reverse-string-ii

> 题目链接

[LeetCode-541-reverse-string-ii](https://leetcode-cn.com/problems/reverse-string-ii/)

> 思路

遍历数组，然后交换指定范围的字符串

> 代码

```java
class Solution {
    public String reverseStr(String s, int k) {
        char[] result = s.toCharArray();
        int size = result.length - 1;
        for(int i = 0; i < result.length; i += k * 2){
            swapArray(i, Math.min(i + k - 1, size), result);
        }
        return new String(result);
    }
    public void swapArray(int start, int end, char[] array){
        while(end > start){
            char c = array[start];
            array[start] = array[end];
            array[end] = c;
            start++;
            end--;
        }
    }
}
```

> 复杂度分析

遍历两次数组，时间复杂度O(n)

额外使用char数组，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.4 MB, 在所有 Java 提交中击败了64.74%的用户
