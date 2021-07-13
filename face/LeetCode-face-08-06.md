### LeetCode-face-08-06

> 题目链接

[LeetCode-face-08-06](https://leetcode-cn.com/problems/hanota-lcci/)

> 思路

著名的叠罗汉问题，把n - 1移动到中间，把最后一块移动到目标盘子，再把这n - 1块移动过去

> 代码

```java
class Solution {
    
    public void hanota(List<Integer> A, List<Integer> B, List<Integer> C) {
        move(A.size(), A, C, B);
    }

    public void move(int n, List<Integer> origin, List<Integer> target, List<Integer> buff){
        if(n <= 0) return;
        move(n - 1, origin, buff, target);
        target.add(origin.remove(origin.size() - 1));
        move(n - 1, buff, target, origin);
    }

}
```

> 复杂度分析

移动的次数为时间复杂度，时间复杂度O(2^n - 1) 

函数栈的深度为n，空间复杂度O(n)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了77.72%的用户

内存消耗：36 MB, 在所有 Java 提交中击败了94.53%的用户
