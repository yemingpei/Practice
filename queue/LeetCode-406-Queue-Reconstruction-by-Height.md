### LeetCode-406-Queue-Reconstruction-by-Height

> 题目链接

[LeetCode-406-Queue-Reconstruction-by-Height](https://leetcode.com/problems/queue-reconstruction-by-height/)

> 思路

按照身高升序，排位降序进行排列，然后检索排位，来重新排序，确保前面有多少人更高

> 代码

```java
class Solution {
    public int[][] reconstructQueue(int[][] people) {
        List<int[]> list = new ArrayList<>();
        PriorityQueue<int[]> pq = new PriorityQueue<>(new comp());
        
        for(int[] temp : people){
            pq.add(temp);
        }
        
        while(!pq.isEmpty()){
            int[] temp = pq.poll();
            list.add(temp[1], temp);
        }
        
        return list.toArray(new int[people.length][2]);
    }
    
    class comp implements Comparator<int[]>{
        public int compare(int[] a, int[] b){
            if(a[0]!=b[0])
                return b[0] - a[0];
            else{
                return a[1] - b[1];
            }
        }
    }
}
```

> 复杂度分析

遍历两遍数组，时间复杂度O(n ^ 2)

额外使用优先队列，空间复杂度O(n)。

> 总结

Runtime: 4 ms, faster than 99.84% of Java online submissions for Queue Reconstruction by Height.

Memory Usage: 39.9 MB, less than 73.98% of Java online submissions for Queue Reconstruction by Height.
