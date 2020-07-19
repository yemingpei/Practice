### LeetCode-76-Minimum-Window-Substring

> 题目链接

[LeetCode-76-Minimum-Window-Substring](https://leetcode.com/problems/minimum-window-substring/)

> 思路

先记录目标字串的字母情况，然后start和end形成窗口，不断移动，找目标子串

> 代码

```java
class Solution {
    public String minWindow(String s, String t) {
        if(s==null || t==null) return "";
        int[] map=new int[128];
        for(Character c:t.toCharArray()){
            map[c]++;
        }
        int start = 0, end = 0, minStart = 0, minLen = Integer.MAX_VALUE, counter = t.length();
        char[] arr=s.toCharArray();
        while(end<arr.length){
             if (map[arr[end]] > 0) counter--;
             map[arr[end]]--;
             end++;
             while(counter==0){
                 if((end-start)<minLen){
                     minLen=end-start;
                     minStart=start;
                 }
                 map[arr[start]]++;
                 if(map[arr[start]]>0)counter++;
                 start++;
             }
        }
        return minLen == Integer.MAX_VALUE ? "" : s.substring(minStart, minStart + minLen);
    }
}
```

> 复杂度分析

start和end分别遍历两遍字符串，时间复杂度O(n)

额外使用长度为128的数组辅助，空间复杂度O(1)

> 总结

Runtime: 4 ms, faster than 90.76% of Java online submissions for Minimum Window Substring.

Memory Usage: 41.1 MB, less than 17.64% of Java online submissions for Minimum Window Substring.
