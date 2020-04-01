### LeetCode-670-Maximum-Swap

> 题目链接

[LeetCode-670-Maximum-Swap](https://leetcode.com/problems/maximum-swap/)

> 思路

遍历一遍数组，数值用HashMap保存起来，如果找到target - 对应位置差值的数，则输出位置

> 代码

```java
class Solution {
    public int maximumSwap(int num) {
        if (num < 12) return num;
        char[] numString = Integer.toString(num).toCharArray();
        int flag = -1;
        int start = 0;
        char startNum = numString[0];
        for (int i = 0; i < numString.length - 1; i++) {
          if (numString[i] < numString[i + 1]) {
            flag = i;
            break;
          } else if (numString[i] > numString[i + 1]) {
            start = i + 1;
            startNum = numString[i + 1];
          }
        }
        if (flag == -1) return num;
        int end = numString.length - 1;
        char endNum = numString[end];
        for (int i = end; i > flag; i--) {
          if (numString[i] > endNum) {
            end = i;
            endNum = numString[i];
          }
        }
        if (endNum > numString[0]) {
          numString[end] = numString[0];
          numString[0] = endNum;
        } else {
          numString[end] = startNum;
          numString[start] = endNum;
        }
        return Integer.valueOf(new String(numString));
    }
}
```

> 复杂度分析

for循环遍历了一遍数组，时间复杂度O(n)

额外使用了char[]数组,大小为n，还有额外的几个int变量，空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Maximum Swap.
Memory Usage: 36.5 MB, less than 25.00% of Java online submissions for Maximum Swap.
