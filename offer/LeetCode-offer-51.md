### LeetCode-offer-51

> 题目链接

[LeetCode-offer-51](https://leetcode-cn.com/problems/shu-zu-zhong-de-ni-xu-dui-lcof/)

> 思路

通过归并排序，如果后半部分的数组先被选中，则表示前半部分的数组剩余个数就是逆序对的个数

> 代码

```java
class Solution {
    int count = 0;
    public int reversePairs(int[] nums) {
        int[] mergeList = new int[nums.length];
        int len = 1;
        while(len <= nums.length){
            mergePass(nums, mergeList, len);
            len <<= 1;
            if(len <= nums.length){
                mergePass(mergeList, nums, len);
                len <<= 1;
            }
        }
        return count;
    }

    private void mergePass(int[] initList, int[] mergeList, int len){
        int i = 0;
        while(i + 2*len - 1 <= initList.length - 1){
            merge(initList, mergeList, i, i + len - 1, i + 2*len - 1);
            i += 2*len;
        }
        if(i + len <= initList.length - 1){
            merge(initList, mergeList, i, i + len - 1, initList.length - 1);
        }else{
            for(int j = i; j < initList.length; j++){
                mergeList[j] = initList[j];
            }
        }
    }

    private void merge(int[] initList, int[] mergeList, int llow, int mid, int rhigh){
        int rlow = mid + 1;
        int mlow = llow;

        while(llow <= mid && rlow <= rhigh){
            if(initList[llow] <= initList[rlow]){
                mergeList[mlow] = initList[llow];
                llow++;
                mlow++;
            }else{
                count += mid - llow + 1;
                mergeList[mlow] = initList[rlow];
                rlow++;
                mlow++;
            }
        }

        while(llow <= mid){
            mergeList[mlow] = initList[llow];
            llow++;
            mlow++;
        }

        while(rlow <= rhigh){
            mergeList[mlow] = initList[rlow];
            rlow++;
            mlow++;
        }
    }
}
```

> 复杂度分析

归并排序，时间复杂度O(nlogn)

额外使用数组来辅助，空间复杂度O(n)

> 总结

执行用时：26 ms, 在所有 Java 提交中击败了99.90%的用户

内存消耗：47.4 MB, 在所有 Java 提交中击败了71.90%的用户
