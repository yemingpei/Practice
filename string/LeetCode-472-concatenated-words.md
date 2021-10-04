### LeetCode-472-concatenated-words

> 题目链接

[LeetCode-472-concatenated-words](https://leetcode-cn.com/problems/concatenated-words/)

> 思路

利用动态规划加哈希记忆

> 代码

```java
class Solution {
    public List<String> findAllConcatenatedWordsInADict(String[] words) {
        if(words.length <= 2)
            return new ArrayList<>();
        Set<String> wordDict = new HashSet<>(Arrays.asList(words));
        List<String> list = new ArrayList<>();
        int len = Integer.MAX_VALUE;
        for(String word : words)
            len = Math.min(len, word.length());
        for(String s : words){
            if(!s.equals("") && wordBreak(s, len, wordDict))
                list.add(s);
        }
        return list;
    }
    public boolean wordBreak(String s, int len, Set<String> wordDict) {
        if(s.length() < 2 * len) return false;
        int n = s.length();
        boolean[] dp = new boolean[n+1];
        dp[0] = true;
        for(int i = 1; i <= n; ++i){
            for(int j = 0; j < i; ++j){
                if(dp[j] && wordDict.contains(s.substring(j, i))){
                    if(j == 0 && i == n) continue;
                    dp[i] = true;
                    break;
                }
            }
        }
        return dp[n];
    }
}
```

> 复杂度分析

二维动态规划，时间复杂度O(n ^ 2)

额外使用boolean数组，空间复杂度O(n)

> 总结

执行用时：1065 ms, 在所有 Java 提交中击败了26.34%的用户

内存消耗：43.2 MB, 在所有 Java 提交中击败了87.81%的用户
