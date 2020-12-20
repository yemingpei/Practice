### LeetCode-335-Self-Crossing

> 题目链接

[LeetCode-335-Self-Crossing](https://leetcode.com/problems/self-crossing/)

> 思路

不断循环画圈，总结出4条边，5条边会重叠的情况，然后循环画边，取前四条，五条来判断

> 代码

```java
class Solution {
    public boolean isSelfCrossing(int[] x) {
        int l = x.length;
        if(l <= 3) return false;
        for(int i = 3; i < l; i++){
            if(x[i] >= x[i-2] && x[i-1] <= x[i-3]) return true;
            if(i >= 4){
                if(x[i-1] == x[i-3] && x[i] + x[i-4] >= x[i-2]) return true;
            }
            if(i >= 5){
                if(x[i-2] - x[i-4] >= 0 && x[i] >= x[i-2] - x[i-4] && x[i-1] >= x[i-3] - x[i-5] && x[i-1] <= x[i-3]) return true;
            }
        }
        return false;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

无额外使用空间，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Self Crossing.

Memory Usage: 36.3 MB, less than 80.41% of Java online submissions for Self Crossing.
