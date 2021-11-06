### LeetCode-514-freedom-trail

> 题目链接

[LeetCode-514-freedom-trail](https://leetcode-cn.com/problems/freedom-trail/)

> 思路

深度遍历，先做好二维的字符记录，便于快速检索，缩短距离

> 代码

```java
class Solution {
    public int findRotateSteps(String ring, String key) {
        int[] lettersNum = new int[26];
        int[][] lettersPos = new int[26][];
        int[] lettersIndex = new int[26];
        int[][] keyStep = new int[ring.length()][key.length()];
        for (int i = 0; i < ring.length(); i++) {
            lettersNum[ring.charAt(i) - 'a']++;
        }
        for (int i = 0; i < ring.length(); i++) {
            int j = ring.charAt(i) - 'a';
            if (null == lettersPos[j]) {
                lettersPos[j] = new int[lettersNum[j]];
            }
            lettersPos[j][lettersIndex[j]] = i;
            lettersIndex[j]++;
        }
        return findMinSteps(keyStep, ring, key, lettersPos, lettersNum, 0, 0);
    }

    public static  int findMinSteps(int[][] keyStep, String ring, String key, int[][] lettersPos, int[] lettersNum, int position, int index) {
        if (index == key.length()) {
            return 0;
        }
        if (keyStep[position][index] > 0) {
            return keyStep[position][index];
        }
        int letter = key.charAt(index) - 'a';
        int steps = Integer.MAX_VALUE;
        for (int j = 0; j < lettersNum[letter]; j++) {
            int dis = (position + ring.length() - lettersPos[letter][j]) % ring.length();
            dis = Math.min(dis, ring.length() - dis);
            int step = dis + findMinSteps(keyStep, ring, key, lettersPos, lettersNum, lettersPos[letter][j], index + 1);
            if (step < steps) {
                steps = step;
            }
        }
        keyStep[position][index] = steps + 1;
        return keyStep[position][index];
    }
}
```

> 复杂度分析

遍历两个字符串的坐标，时间复杂度O(mn)

无额外二维数组，空间复杂度O(n ^ 2)

> 总结

执行用时：4 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：39 MB, 在所有 Java 提交中击败了40.55%的用户
