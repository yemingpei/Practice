### LeetCode-face-10-10

> 题目链接

[LeetCode-face-10-10](https://leetcode-cn.com/problems/sorted-matrix-search-lcci/)

> 思路

利用二分搜索，快速找到插入点，插入点就是大于等于该数字的个数，可以复用

> 代码

```java
class StreamRank {

    private List<Integer> list;

    public StreamRank() {
        list = new ArrayList<>();
    }
    
    public void track(int x) {
        list.add(getRankOfNumber(x), x);
    }
    
    public int getRankOfNumber(int x) {
        int left = 0;
        int right = list.size() - 1;
        while(right >= left){
            int mid = (right - left) / 2 + left;
            if(list.get(mid) > x) right = mid - 1;
            else left = mid + 1;
        }
        return left;
    }
}
```

> 复杂度分析

track，时间复杂度O(n)，getRankOfNumber，时间复杂度是O(logn)

额外使用list辅助，空间复杂度O(n)

> 总结

执行用时：4 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：43.9 MB, 在所有 Java 提交中击败了48.34%的用户
