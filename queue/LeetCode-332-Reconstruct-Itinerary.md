### LeetCode-332-Reconstruct-Itinerary

> 题目链接

[LeetCode-332-Reconstruct-Itinerary](https://leetcode.com/problems/reconstruct-itinerary/)

> 思路

从起点出发，进行深度优先搜索，需要标志这个路径，没有可移动的路径，则将所在节点加入到栈中，并返回

> 代码

```java
class Solution {
    Map<String, PriorityQueue<String>> it = new HashMap<>();
    LinkedList<String> result = new LinkedList<>();
    public List<String> findItinerary(List<List<String>> tickets) {        
        for(int i=0; i<tickets.size(); i++){
            List<String> ticket = tickets.get(i);
            if(!it.containsKey(ticket.get(0))){
                PriorityQueue<String> pq = new PriorityQueue<>();
                pq.offer(ticket.get(1));
                it.put(ticket.get(0),pq);
            } else{
                PriorityQueue<String> pq = it.get(ticket.get(0));
                pq.offer(ticket.get(1));         
            }
        }
        dfs("JFK");
        return result;   
    }
    
   public void dfs(String s){
        PriorityQueue<String> dest = it.get(s);
        while(dest != null && !dest.isEmpty()){
           String d = dest.poll();            
           dfs(d);
        }   
        result.addFirst(s);
    }
}
```

> 复杂度分析

深度搜索，需要不断锁定和解锁原信息，均摊时间复杂度O(nlogn)

额外使用一个队列辅助，空间复杂度O(n)

> 总结

Runtime: 5 ms, faster than 75.25% of Java online submissions for Reconstruct Itinerary.

Memory Usage: 46.7 MB, less than 5.48% of Java online submissions for Reconstruct Itinerary.
