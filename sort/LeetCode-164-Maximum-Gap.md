### LeetCode-164-Maximum-Gap

> 题目链接

[LeetCode-164-Maximum-Gap](https://leetcode.com/problems/maximum-gap/)

> 思路

按照最大值和最小值的差来分桶，记录每个桶内的最大和最小,然后依次比较，找出相邻差值

> 代码

```java
class Solution {
    public int maximumGap(int[] nums) {
        int n=nums.length,max=0,min=Integer.MAX_VALUE;
        if(n<2)return 0;
        for(int num:nums){
            max=Math.max(max,num);
            min=Math.min(min,num);
        }
        if(min==max)return 0;
        int bs=Math.max(1,(max-min)/(n-1)),bn=(max-min)/bs+1;
        int bucket[][]=new int[bn][2];                            
        for(int i=0;i<bn;i++){
            bucket[i][0]=Integer.MAX_VALUE;
            bucket[i][1]=-1;
        }
        for(int num:nums){
            int p=(num-min)/bs;                                  
            bucket[p][0]=Math.min(bucket[p][0],num);
            bucket[p][1]=Math.max(bucket[p][1],num);
        }
        int res=0;
        int now=0;
        while(bucket[now][0]==Integer.MAX_VALUE&&bucket[now][1]==-1)now++;
        int left=bucket[now][1],right=0;
        now++;                                                   
        while(now<bn){
            if(bucket[now][0]==Integer.MAX_VALUE&&bucket[now][1]==-1){now++;}
            else{
                right=bucket[now][0];
                res=Math.max(res,right-left);
                left=bucket[now][1];
                now++;
            }
        }
        return res;
    }
}
```

> 复杂度分析

桶排序，时间复杂度O(n + m)

额外使用数组来记录桶，空间复杂度O(n)

> 总结

Runtime: 2 ms, faster than 97.07% of Java online submissions for Maximum Gap.

Memory Usage: 39.4 MB, less than 97.07% of Java online submissions for Maximum Gap.
