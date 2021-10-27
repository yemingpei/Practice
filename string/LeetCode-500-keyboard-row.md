### LeetCode-500-keyboard-row

> 题目链接

[LeetCode-500-keyboard-row](https://leetcode-cn.com/problems/keyboard-row/)

> 思路

先把字母和组的关系列在数组里面，然后通过不断遍历，是否都属于同一个组，来确定是否是目标字符串

> 代码

```java
class Solution {
    private int[] data = new int[]{2, 3, 3, 2, 1, 2, 2, 2, 1, 2, 2, 2, 3, 3, 1, 1, 1, 1, 2, 1, 1, 3, 1, 3, 1, 3};
    public String[] findWords(String[] words) {
        List<String> list = new ArrayList<>();
        for(String text : words){
            if(checkString(text)) list.add(text);
        }
        String[] result = new String[list.size()];
        list.toArray(result);
        return result;
    }
    public boolean checkString(String text){
        if(text.length() == 0) return true;
        char[] array = text.toCharArray();
        int start = findChar(array[0]);
        for(int i = 1; i < array.length; i++){
            if(start != findChar(array[i])) return false;
        }
        return true;
    }
    public int findChar(char c){
        if(c >= 'a') return data[c - 'a'];
        else return data[c - 'A'];
    }
}
```

> 复杂度分析

遍历字符串数组，时间复杂度O(n)

额外使用list，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36.2 MB, 在所有 Java 提交中击败了86.03%的用户
