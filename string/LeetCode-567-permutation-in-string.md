### LeetCode-567-permutation-in-string

> 题目链接

[LeetCode-567-permutation-in-string](https://leetcode-cn.com/problems/permutation-in-string/)

> 思路

利用滑动窗口，先记录需要补充的元素，如果元素补充完，宽度正好合适，则返回true

> 代码

```java
class Solution {
    public boolean checkInclusion(String s1, String s2) {
        int n = s1.length(),m = s2.length();
        if(n > m)
            return false;
        int[] cnt = new int[26];
        for (int i = 0; i < n; i++) {
            --cnt[s1.charAt(i) - 'a'];
        }
        int left = 0;
        for(int right = 0; right < m; right++){
            int x = s2.charAt(right) - 'a';
            ++cnt[x];
            while (cnt[x] > 0){
                --cnt[s2.charAt(left) - 'a'];
                ++left;
            }
            if((right - left + 1) == n)
                return true;
        }
        return false;
    }
}
```

> 复杂度分析

遍历两个字符串，时间复杂度O(m + n)

额外使用长度固定的数组，空间复杂度O(1)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了96.52%的用户

内存消耗：38.2 MB, 在所有 Java 提交中击败了86.13%的用户
