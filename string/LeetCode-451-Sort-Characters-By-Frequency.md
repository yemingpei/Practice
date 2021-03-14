### LeetCode-451-Sort-Characters-By-Frequency

> 题目链接

[LeetCode-451-Sort-Characters-By-Frequency](https://leetcode.com/problems/sort-characters-by-frequency/)

> 思路

先统计字符的个数，然后找到数量最大的，开始拼装

> 代码

```java
class Solution {
    public String frequencySort(String s) {
        if(s == null || s.isEmpty()) return s;
        int n = s.length();
        int freq[] = new int[128];
        for(char c : s.toCharArray()){
            freq[(int)c]++;
        }
        char result[] = new char[n];
        int x = 0;
        int max;
        int index;
        while(x < n){
            max = 0;
            index = -1;
            for(int i = 0; i < freq.length; i++){
                if(max < freq[i]){
                    max = freq[i];
                    index = i;
                }
            }
            if(max == 0) return new String(result);
            int frequency = max;
            while(frequency-- > 0){
                result[x++] = (char)(index);
            }
            freq[index] = 0;
        }
        return new String(result); 
    }
}
```

> 复杂度分析

两遍数组，每次比较128个数组里面最大的，时间复杂度O(n)

额外使用数组变量，空间复杂度O(n)

> 总结

Runtime: 2 ms, faster than 100.00% of Java online submissions for Sort Characters By Frequency.

Memory Usage: 39.4 MB, less than 94.05% of Java online submissions for Sort Characters By Frequency.
