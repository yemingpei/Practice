### LeetCode-face-17-17

> 题目链接

[LeetCode-face-17-17](https://leetcode-cn.com/problems/multi-search-lcci/)

> 思路

需要寻找没个子串在长串的位置，然后再组装成数组

> 代码

```java
class Solution {
    public int[][] multiSearch(String big, String[] smalls) {
        List<List<Integer>> list = new ArrayList<List<Integer>>();
        for(int i = 0; i < smalls.length; i++){
            if(smalls[i].isEmpty()) continue;
            List<Integer> childList = new ArrayList<Integer>();
            for(int j = 0, k = 0; j < big.length(); j = k + 1){
                k = big.indexOf(smalls[i],j);
                if(k != -1) childList.add(k);
                else break;
            }
            list.add(childList);
        }
        int[][] ret = new int[list.size()][];
        for(int i = 0; i < list.size(); i++){
            List<Integer> childList = list.get(i);
            ret[i] = new int[childList.size()];
            for(int j = 0, n = childList.size(); j < n; j++) ret[i][j] = childList.get(j);
        }
        return list.isEmpty() ? new int[1][0] : ret;
    }
}
```

> 复杂度分析

遍历数组子串里面匹配字符，时间复杂度O(nm)

额外二维list，空间复杂度O(nm)

> 总结

执行用时：179 ms, 在所有 Java 提交中击败了51.78%的用户

内存消耗：57.1 MB, 在所有 Java 提交中击败了52.43%的用户
