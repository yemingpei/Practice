### LeetCode-offer-40

> 题目链接

[LeetCode-offer-40](https://leetcode-cn.com/problems/zui-xiao-de-kge-shu-lcof/)

> 思路

利用快排找出最小的k个数字,每次对比结束都比较标志位是否是k，然后再处理偏向k的一边

> 代码

```java
class Solution {
    public int[] getLeastNumbers(int[] arr, int k) {
        if(k == 0) return new int[0];      
        selectK(arr, 0, arr.length - 1, k - 1);
        return Arrays.copyOf(arr, k);
    }
      private void selectK(int[] arr, int l, int r, int k){
        int p = partition(arr, l, r);
        if(k == p) return ;
        else if(k < p) selectK(arr, l, p - 1 , k);
        else selectK(arr, p +1, r, k);
    }
    public static int partition(int[] nums, int l, int r){
        int i = l+1,j = r;
        while(i <= j && j > 0){
            if(nums[i] < nums[l]){
                i++;
                continue;
            }
            if(nums[j]>nums[l]){
                j--;
                continue;
            }
            swap(nums,i,j);
            i++;
            j--;
        }
        swap(nums, l, j);
        return j;
    }
    public static void swap(int[] nums, int l, int r){
        int tem = nums[l];
        nums[l] = nums[r];
        nums[r] = tem;
    }
}
```

> 复杂度分析

利用快排，时间复杂度O(nlogn)

无额外使用空间，空间复杂度O(1)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了84.78%的用户

内存消耗：39.6 MB, 在所有 Java 提交中击败了78.65%的用户
