### LeetCode-632-smallest-range-covering-elements-from-k-lists

> 题目链接

[LeetCode-632-smallest-range-covering-elements-from-k-lists](https://leetcode-cn.com/problems/smallest-range-covering-elements-from-k-lists/)

> 思路

利用排序，然后滑动窗口来确认目标值

> 代码

```java
class Solution {
    public int[] smallestRange(List<List<Integer>> nums) {
        int n = 0, k = nums.size();
        for(List<Integer> list : nums){
            n += list.size();
        }
        int[][] arr = new int[n][2];
        int idx = 0;
        for(int i = 0; i < k; i++){
            for(int num : nums.get(i)){
                arr[idx][0] = num;
                arr[idx][1] = i; 
                idx++;
            }
        }
        Arrays.sort(arr, (a, b) -> a[0] - b[0]);
        int[] ans = new int[]{0, Integer.MAX_VALUE};
        int[] cache = new int[k];
        int count = 0;
        int l = 0, r = 0;
        while(r < n){
            if(cache[arr[r][1]] == 0){
                count++;
            }
            cache[arr[r][1]]++;
            if(count == k){
                while(cache[arr[l][1]] > 1){
                    cache[arr[l][1]]--;
                    l++;
                }
                if((ans[1] - ans[0]) > (arr[r][0] - arr[l][0])){
                    ans[1] = arr[r][0];
                    ans[0] = arr[l][0];
                }
            }
            r++;
        }
        return ans;
    }
}
```

> 复杂度分析

遍历全部数据，时间复杂度O(nk)

额外使用数组，空间复杂度O(n)

> 总结

执行用时：19 ms, 在所有 Java 提交中击败了99.26%的用户

内存消耗：44.6 MB, 在所有 Java 提交中击败了49.64%的用户
