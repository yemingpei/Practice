### LeetCode-face-16-15

> 题目链接

[LeetCode-face-16-15](https://leetcode-cn.com/problems/master-mind-lcci/)

> 思路

先比较是否相等，否则就计数，猜中为字符相等的数量，伪猜中就是相同字符的较少次数之和

> 代码

```java
class Solution {
    public int[] masterMind(String solution, String guess) {
        int[] number1 = new int[128];
        int[] number2 = new int[128];
        int count = 0;
        for(int i = 0; i < solution.length(); i++){
            char word = solution.charAt(i);
            char key = guess.charAt(i);
            if(word == key) count++;
            else{
                number1[word]++;
                number2[key]++;
            }
        }
        return new int[]{count, Math.min(number1['R'], number2['R']) + Math.min(number1['Y'], number2['Y']) + Math.min(number1['G'], number2['G']) + Math.min(number1['B'], number2['B'])};
    }
}
```

> 复杂度分析

遍历字符串，时间复杂度O(n)

额外使用固定长度的int数组，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36.5 MB, 在所有 Java 提交中击败了23.05%的用户
