### LeetCode-551-student-attendance-record-i

> 题目链接

[LeetCode-551-student-attendance-record-i](https://leetcode-cn.com/problems/student-attendance-record-i/)

> 思路

计数法，不连续则重置

> 代码

```java
class Solution {
    public boolean checkRecord(String s) {
        int countA= 0;
        int countL= 0;
        char[] text = s.toCharArray();
        for(char c: text){
            if(c == 'A'){
                countL = 0;
                countA++;
            }
            else if(c == 'L') countL++;
            else countL = 0;
            if(countA > 1 || countL > 2) return false;
        }
        return true;
    }
}
```

> 复杂度分析

遍历字符串，时间复杂度O(n)

额外使用int计数，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36.6 MB, 在所有 Java 提交中击败了30.76%的用户
