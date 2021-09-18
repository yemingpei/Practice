### LeetCode-face-17-26

> 题目链接

[LeetCode-face-17-26](https://leetcode-cn.com/problems/sparse-similarity-lcci/)

> 思路

记录出现过的数字，然后通过组合寻找答案

> 代码

```java
class Solution {
    public List<String> computeSimilarities(int[][] docs) {
        List<String> ans = new ArrayList<>();
        Map<Integer, List<Integer>> map = new HashMap<>();
        int[][] help = new int[docs.length][docs.length];
        for (int i = 0; i < docs.length; i++) {
            for (int j = 0; j < docs[i].length; j++) {
                List<Integer> list = map.get(docs[i][j]);
                if (list == null) {
                    list = new ArrayList<>();
                    map.put(docs[i][j], list);
                } else {
                    for (Integer k : list) {
                        help[i][k]++;
                    }
                }
                list.add(i);
            }

            for (int k = 0; k < docs.length; k++) {
                if (help[i][k] > 0) {
                    ans.add(k + "," + i + ": " + String.format("%.4f", (double) help[i][k] / (docs[i].length + docs[k].length - help[i][k])));
                }
            }
        }
        return ans;
    }
}
```

> 复杂度分析

需要两两比较，比较次数为，时间复杂度O(n ^ 2)

额外使用map辅助，空间复杂度O(n)

> 总结

执行用时：279 ms, 在所有 Java 提交中击败了71.26%的用户

内存消耗：71.6 MB, 在所有 Java 提交中击败了37.93%的用户
