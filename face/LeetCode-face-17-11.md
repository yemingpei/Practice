### LeetCode-face-17-11

> 题目链接

[LeetCode-face-17-11](https://leetcode-cn.com/problems/find-closest-lcci/)

> 思路

滑动窗口，不断从左往右滑动来给你个单词的指标，然后计算两点的距离，记录最小值

> 代码

```java
class Solution {
    public int findClosest(String[] words, String word1, String word2) {
        int index1 = -1, index2 = -1, minLen = Integer.MAX_VALUE;
        for(int i = 0; i < words.length; i++){
            if(words[i].equals(word1)){
                index1 = i;
                if(index2 != -1){
                    minLen = Math.min(minLen, index1 - index2);
                }
            } else if(words[i].equals(word2)){
                index2 = i;
                if(index1 != -1){
                    minLen = Math.min(minLen, index2 - index1);
                }
            }
        }
        return minLen;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

使用左右指针，记录位置，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：43.6 MB, 在所有 Java 提交中击败了95.62%的用户
