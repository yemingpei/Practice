### LeetCode-373-Find-K-Pairs-with-Smallest-Sums

> 题目链接

[LeetCode-373-Find-K-Pairs-with-Smallest-Sums](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/)

> 思路

先第一排进队列，然后最小的出队列，添加最小的，下一个数字组合

> 代码

```java
class Solution {
    public List<List<Integer>> kSmallestPairs(int[] nums1, int[] nums2, int k) {
        List<List<Integer>> res = new ArrayList<>();
        if(nums1.length == 0 || nums2.length == 0 || k == 0) return res;
        int m = nums1.length;
        int n = nums2.length;
        Queue<Tuple> pq = new PriorityQueue<>();
        for(int j = 0; j < n; j++) {
            pq.offer(new Tuple(0, j,nums1[0] +nums2[j]));
        }
        for(int i = 0; i < k && !pq.isEmpty(); i++) {
            List<Integer> pair = new ArrayList<>();
            Tuple num = pq.poll();
            pair.add(nums1[num.nums1]);
            pair.add(nums2[num.nums2]);
            res.add(pair);
            if(num.nums1 < m -1) pq.offer(new Tuple(num.nums1 +1, num.nums2, nums1[num.nums1+1]+ nums2[num.nums2]));
        }
        return res;
    }
    private static class Tuple implements Comparable<Tuple> {
        int nums1;
        int nums2;
        int sum;
        
        Tuple(int nums1, int nums2, int sum) {
            this.nums1 = nums1;
            this.nums2 = nums2;
            this.sum = sum;
        }
        
        @Override
        public int compareTo(Tuple that) {
            return this.sum - that.sum;

        }
    }
}
```

> 复杂度分析

队列排序，其他操作时间复杂度O(nlogn)

额外使用队列来辅助，空间复杂度O(n)

> 总结

Runtime: 2 ms, faster than 100.00% of Java online submissions for Find K Pairs with Smallest Sums.

Memory Usage: 39.7 MB, less than 76.78% of Java online submissions for Find K Pairs with Smallest Sums.
