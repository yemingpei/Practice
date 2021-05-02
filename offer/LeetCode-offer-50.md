### LeetCode-offer-50

> 题目链接

[LeetCode-offer-50](https://leetcode-cn.com/problems/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/)

> 思路

全部小写，从第一个和最后一个的位置对比，如果相同，则只有一个

> 代码

```java
class Solution {
    public char firstUniqChar(String s) {
        int target = s.length();
        for (int i ='a';i <= 'z'; i++){
            int index = s.indexOf(i);
            if(index != -1 && index == s.lastIndexOf(i) && index < target){
                target = index;
            }
        }
        if(target == s.length()) return ' ';
        return s.charAt(target);
    }
}
```

> 复杂度分析

寻找第一个和最后一个同一个字符，时间复杂度O(n)

额外使用index来记录，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.8 MB, 在所有 Java 提交中击败了59.79%的用户
