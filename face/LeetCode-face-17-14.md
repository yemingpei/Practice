### LeetCode-face-17-14

> 题目链接

[LeetCode-face-17-14](https://leetcode-cn.com/problems/smallest-k-lcci/)

> 思路

部分快排，不需要完全有序，保证前k个事最小的就可以

> 代码

```java
class Solution {
    public int[] smallestK(int[] list, int k){
            if (k >= list.length)
                return list;
            quickSort(list, 0, list.length-1, k);
            int[] ans = new int[k];
            System.arraycopy(list, 0, ans, 0, k);
            return ans;
        }

    private void quickSort(int[] list, int l, int r, int k){
        if (l >= r)
            return;
        int key = list[l];
        int i = l, j = r;
        while (i < j){
            while(i < j && list[j] >= key) --j;
            list[i] = list[j];
            while (i < j && list[i] <= key) ++i;
            list[j] = list[i];
        }
        list[i] = key;
        if(i > k)
            quickSort(list, l, i - 1, k);
        else if(i == k){
            return ;
        }else{
            quickSort(list, i + 1, r, k);
        }
    }
}
```

> 复杂度分析

半区快排，时间复杂度O(n)，最坏时间复杂度,时间复杂度O(n ^ 2)

额外使用不断递归，递归深度，空间复杂度O(logn)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了97.96%的用户

内存消耗：48.2 MB, 在所有 Java 提交中击败了31.67%的用户
