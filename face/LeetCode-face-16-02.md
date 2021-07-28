### LeetCode-face-16-02

> 题目链接

[LeetCode-face-16-02](https://leetcode-cn.com/problems/words-frequency-lcci/)

> 思路

用map保存字符串出现的次数

> 代码

```java
class WordsFrequency {
    private Map<String, Integer> map = new HashMap<>();
    public WordsFrequency(String[] book) {
        for(String text : book){
            map.put(text, map.getOrDefault(text, 0) + 1);
        }
    }
    
    public int get(String word) {
        return map.getOrDefault(word, 0);
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用map保存数据，空间复杂度O(n)

> 总结

执行用时：140 ms, 在所有 Java 提交中击败了94.02%的用户

内存消耗：87.7 MB, 在所有 Java 提交中击败了39.31%的用户
