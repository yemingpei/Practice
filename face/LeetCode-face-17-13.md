### LeetCode-face-17-13

> 题目链接

[LeetCode-face-17-13](https://leetcode-cn.com/problems/re-space-lcci/)

> 思路

字典树加动态规划，动态规划公式：dp[i] = Math.min(dp[i], dp[j - 1])

> 代码

```java
class Solution {
    public int respace(String[] dictionary, String sentence) {
        int n = sentence.length();
        Trie root = new Trie();
        for (String word : dictionary)
            root.insert(word);
        int[] dp = new int[n + 1];
        Arrays.fill(dp, Integer.MAX_VALUE);
        dp[0] = 0;
        for (int i = 1; i <= n; ++i) {
            dp[i] = dp[i - 1] + 1;
            Trie curPos = root;
            for (int j = i; j >= 1; --j) {
                int t = sentence.charAt(j - 1) - 'a';
                if (curPos.next[t] == null) break;
                else if (curPos.next[t].isEnd) dp[i] = Math.min(dp[i], dp[j - 1]);
                if (dp[i] == 0) break;
                curPos = curPos.next[t];
            }
        }
        return dp[n];
    }

    class Trie {
        public Trie[] next;
        public boolean isEnd;

        public Trie() {
            next = new Trie[26];
            isEnd = false;
        }

        public void insert(String s) {
            Trie curPos = this;
            for (int i = s.length() - 1; i >= 0; --i) {
                int t = s.charAt(i) - 'a';
                if (curPos.next[t] == null) curPos.next[t] = new Trie();
                curPos = curPos.next[t];
            }
            curPos.isEnd = true;
        }
    }
}
```

> 复杂度分析

遍历二维数组，时间复杂度O(n ^ 2)

额外使用数组，空间复杂度O(n)

> 总结

执行用时：11 ms, 在所有 Java 提交中击败了95.24%的用户

内存消耗：60.9 MB, 在所有 Java 提交中击败了23.81%的用户
