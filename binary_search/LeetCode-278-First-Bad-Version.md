### LeetCode-278-First-Bad-Version

> 题目链接

[LeetCode-278-First-Bad-Version](https://leetcode.com/problems/first-bad-version/)

> 思路

利用中间值的特点，不断检查版本号，寻找最左边的true

> 代码

```java
public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int left = 1;
        int right = n;
        while(right > left){
            int mid = left + (right - left) / 2;
            if(isBadVersion(mid)) right = mid;
            else left = mid + 1;
        }
        return left;
    }
}
```

> 复杂度分析

不断利用中点缩小检查版本的范围，时间复杂度O(lgn)

额外使用了low,high,mid三个int值，空间复杂度O(1)

> 总结

Runtime: 12 ms, faster than 98.04% of Java online submissions for First Bad Version.

Memory Usage: 36 MB, less than 28.88% of Java online submissions for First Bad Version.
