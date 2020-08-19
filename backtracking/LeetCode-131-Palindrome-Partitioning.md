### LeetCode-131-Palindrome-Partitioning

> 题目链接

[LeetCode-131-Palindrome-Partitioning](https://leetcode.com/problems/palindrome-partitioning/)

> 思路

回溯法，先记录字串回文的情况，避免重复的判断，回文成立才添加。

> 代码

```java
class Solution {
    public List<List<String>> partition(String s) {
        List<List<String>> res = new ArrayList<>();
        if(s.length() == 0)
            return res;
        List<String> list = new ArrayList<>();
        boolean[][] pals = new boolean[s.length()][s.length()];
        for(int i = 0; i < s.length(); i++){
            pals[i][i] = true;
            for(int j = i + 1; j < s.length(); j++){
                pals[i][j] = isPal(i, j, s);
            }
        }
        helper(s, 0, res, list, pals);
        return res;
    }
    public void helper(String s , int start, List<List<String>> res, List<String> list, boolean[][] pals){
        if(start == s.length()){
            res.add(new ArrayList<>(list));
            return;
        }
        for(int i = start; i<s.length(); i++){
            if(pals[start][i]){
                String temp = s.substring(start, i+1);
                list.add(temp);
                helper(s, i+1, res,list, pals);
                list.remove(list.size() - 1);
            }
        }
    }
    public boolean isPal(int lo , int hi, String s){
        while(lo < hi){
            if(s.charAt(lo) != s.charAt(hi))
                return false;
            lo++;
            hi--;
        }
        return true;
    }
}
```

> 复杂度分析

最坏情况，没有重复的数字，每个数只有选和不选两种情况，形成组合，时间复杂度O(2 ^ n)

额外使用有二维数组保存对应字串是否为回文字串，空间复杂度O(n ^ 2)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Palindrome Partitioning.

Memory Usage: 40.4 MB, less than 70.79% of Java online submissions for Palindrome Partitioning.
