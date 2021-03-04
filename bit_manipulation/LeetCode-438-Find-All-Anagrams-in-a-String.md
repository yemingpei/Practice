### LeetCode-438-Find-All-Anagrams-in-a-String

> 题目链接

[LeetCode-438-Find-All-Anagrams-in-a-String](https://leetcode.com/problems/find-all-anagrams-in-a-string//)

> 思路

遍历字符串，记录字符串的字母数量，然后滑动窗口，比较头尾的变化，用位运算记录变化，相同为0，不同则变为1

> 代码

```java
class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        List<Integer> output = new ArrayList<>();
        if (p.length() > s.length()) return output;
        int[] alph1 = new int[26];
        int[] alph2 = new int[26];
        for (int i = 0; i < p.length(); i++) {
            alph1[p.charAt(i) - 'a']++;
            alph2[s.charAt(i) - 'a']++;
        }
        int flag = 0;
        for(int i = 0; i < 26; i++){
            if(alph1[i] != alph2[i])
                flag ^= (1 << i);
        }
        if(flag == 0) output.add(0);
        int end = s.length() - p.length() + 1;
        for (int i = 1; i < end; i++) {
            int start = s.charAt(i - 1) - 'a';
            alph2[start]--;
            if(alph1[start] != alph2[start]) flag |= (1 << start);
            else  flag &= (~(1 << start));
            
            int position = s.charAt(i + p.length() - 1) - 'a';
            alph2[position]++;
            if(alph1[position] != alph2[position]) flag |= (1 << position);
            else  flag &= (~(1 << position));
            if(flag == 0) output.add(i);
        }
        return output;
    }
}
```

> 复杂度分析

遍历长的字符串，时间复杂度O(n)

额外使用26长度数组计数，空间复杂度O(1)

> 总结

Runtime: 3 ms, faster than 100.00% of Java online submissions for Find All Anagrams in a String.

Memory Usage: 39.9 MB, less than 70.23% of Java online submissions for Find All Anagrams in a String.
