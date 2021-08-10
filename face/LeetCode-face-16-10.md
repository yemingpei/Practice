### LeetCode-face-16-10

> 题目链接

[LeetCode-face-16-10](https://leetcode-cn.com/problems/living-people-lcci/)

> 思路

用数组先保存出生点为+1，结束点次结点为-1，然后就寻找最大的和，进行输出

> 代码

```java
class Solution {
    public int maxAliveYear(int[] birth, int[] death) {
        int[] arr = new int[2002];
        for(int i = 0;i < birth.length; i++){
            arr[birth[i]] ++;
            arr[death[i] + 1] --;
        }
        int max = 0, live = 0, index = 0;
        for(int i = 1900;i < arr.length; i++){
            live += arr[i];
            if(live > max){
                max = live;
                index = i;
            }
        }
        return index;
    }
}
```

> 复杂度分析

需要遍历数组，时间复杂度O(n)

额外使用int数组长度固定，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了95.68%的用户

内存消耗：38.9 MB, 在所有 Java 提交中击败了59.48%的用户
