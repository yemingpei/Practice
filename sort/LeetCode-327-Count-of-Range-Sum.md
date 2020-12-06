### LeetCode-327-Count-of-Range-Sum

> 题目链接

[LeetCode-327-Count-of-Range-Sum](https://leetcode.com/problems/count-of-range-sum/)

> 思路

通过i，j两个数据的差值是否在区间（low，hight），归并排序，计算出相应的个数

> 代码

```java
class Solution {
    public int countRangeSum(int[] nums, int lower, int upper) {
        long sum[] = new long[nums.length+1];
        long temp[] = new long[nums.length+1];
        sum[0]=0;
        for(int i=1;i<=nums.length;i++){
            sum[i]=nums[i-1]+sum[i-1];
        }
        return mergeSort(sum,temp,lower,upper,0,sum.length-1);
    }
    int mergeSort(long[] sum, long[] temp, int lower,int upper,int low,int high){
        if(low>=high) return 0;
        int cnt=0;
        int mid=low+(high-low)/2;
        cnt+=mergeSort(sum,temp,lower,upper,low,mid);
        cnt+=mergeSort(sum,temp,lower,upper,mid+1,high);
        cnt+=merge(sum,temp,lower,upper,low,mid,high);
        return cnt;
    }
    int merge(long[] sum, long temp[], int lower, int upper, int start,int mid, int end){
        int cnt=0;
        int low=mid+1,high=mid+1,idx=start,right=mid+1;
        for(int left = start;left<=mid;left++){
            while(low<=end && sum[low]-sum[left]<lower)
                low++;
            while(high<=end && sum[high]-sum[left]<=upper)
                high++;
            while(right<=end && sum[right]<sum[left])
                temp[idx++]=sum[right++];
            cnt += high-low;
            temp[idx++]=sum[left];
        }
        while(right<=end)
            temp[idx++]=sum[right++];
        
        for(int i=start;i<=end;i++)
            sum[i]=temp[i];
        return cnt;
    }
}
```

> 复杂度分析

归并排序，时间复杂度O(nlgn)

两个辅助数组，空间复杂度O(n)

> 总结

Runtime: 5 ms, faster than 100.00% of Java online submissions for Count of Range Sum.

Memory Usage: 40.3 MB, less than 12.68% of Java online submissions for Count of Range Sum.
