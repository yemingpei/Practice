### LeetCode-face-16-16

> 题目链接

[LeetCode-face-16-16](https://leetcode-cn.com/problems/sub-sort-lcci/)

> 思路

先寻找不是递增的值，作为右边界，并记录最小值，然后再遍历，确认最小值插入的位置

> 代码

```java
class Solution {
    public int[] subSort(int[] array) {
        int[] result = new int[]{ -1, -1};
        if(array.length == 0) return result;
        int max = array[0];
        int flag = Integer.MAX_VALUE;
        for(int i = 1; i < array.length; i++){
            if(max > array[i]){
                result[1] = i;
                flag = Math.min(flag, array[i]);
            }else{
                max = array[i];
            }
        }
        if(result[1] != -1){
            for(int i = 0; i < array.length; i++){
                if(flag < array[i]){
                    result[0] = i;
                    break;
                }
            }
        }
        return result;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用常量的int值，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了84.38%的用户

内存消耗：61.9 MB, 在所有 Java 提交中击败了67.48%的用户
