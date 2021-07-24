### LeetCode-face-10-03

> 题目链接

[LeetCode-face-10-03](https://leetcode-cn.com/problems/search-rotate-array-lcci/)

> 思路

二分搜索，用二分决定是在左半部还是右半部

> 代码

```java
class Solution {
    public int search(int[] arr, int target) {
        int l = 0, r = 0, mid = 0, n = arr.length;
        while(n > 1 && arr[n - 1] == arr[0]){
            n--;
        }
        r = n - 1;
        while(l < r){
            mid = (l + r) >> 1;
            if(arr[mid] <= arr[r]){
                r = mid;
            }else{
                l = mid + 1;
            }
        }
        r = l + n - 1;
        if(arr[l] > target){
            return -1;
        }
        while(r > l){
            mid = (l + r) >> 1;
            if(arr[mid % n] >= target){
                r = mid;
            }else{
                l = mid + 1;
            }
        }
        return arr[l % n] == target ? l % n : -1;
    }
}
```

> 复杂度分析

二分搜索，时间复杂度O(logn) 

额外使用int辅助，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：39.6 MB, 在所有 Java 提交中击败了5.48%的用户
