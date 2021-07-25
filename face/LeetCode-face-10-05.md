### LeetCode-face-10-05

> 题目链接

[LeetCode-face-10-05](https://leetcode-cn.com/problems/sparse-array-search-lcci/)

> 思路

经典的二分搜索，注意中间如果是空字符串的时候就偏移到非空的位置，再进行比较

> 代码

```java
class Solution {
    public int findString(String[] words, String s) {
        int l = 0, r = words.length-1;
        while(r >= l){
            int mid = (l + r) >> 1;
            while(mid > l &&  words[mid].equals("")) mid--;
            if(s.compareTo(words[mid]) == 0) return mid;
            if(s.compareTo(words[mid]) < 0) r = mid - 1;
            else l = mid + 1;
        }
        return -1;
    }
}
```

> 复杂度分析

二分搜索，时间复杂度O(logn) 

额外使用int辅助，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38 MB, 在所有 Java 提交中击败了91.87%的用户
