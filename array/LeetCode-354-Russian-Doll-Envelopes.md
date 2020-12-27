### LeetCode-354-Russian-Doll-Envelopes

> 题目链接

[LeetCode-354-Russian-Doll-Envelopes](https://leetcode.com/problems/russian-doll-envelopes/)

> 思路

按照第一位小到大，次位，大到小，然后就是寻找最长子序列的问题

> 代码

```java
class Solution {
    public int maxEnvelopes(int[][] envelopes) {
        if(envelopes == null || envelopes.length == 0){
            return 0;
        }
        Arrays.sort(envelopes, new Comparator<int[]>(){
            public int compare(int[] arr1, int[] arr2){
                if(arr1[0] == arr2[0]){
                    return arr2[1] - arr1[1];
                }else{
                    return arr1[0] - arr2[0];
                }
            }
        });
        int[] dp = new int[envelopes.length];
        int len = 0;
        for(int[] num: envelopes){
            int i = Arrays.binarySearch(dp, 0, len,num[1]);
            if(i < 0){
                i = -(i + 1);
            }
            dp[i] = num[1];
            if(i == len)
                len++;
        }
        return len;
    }
}
```

> 复杂度分析

排序再寻找递增子序列，时间复杂度O(nlogn)

需要int数组来保存递增子序列的值，空间复杂度O(n)

> 总结

Runtime: 8 ms, faster than 98.03% of Java online submissions for Russian Doll Envelopes.

Memory Usage: 40.3 MB, less than 31.47% of Java online submissions for Russian Doll Envelopes.
