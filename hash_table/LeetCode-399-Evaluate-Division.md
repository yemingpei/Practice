### LeetCode-399-Evaluate-Division

> 题目链接

[LeetCode-399-Evaluate-Division](https://leetcode.com/problems/evaluate-division/)

> 思路

给定图中的一些点（变量），以及某些边的权值（两个变量的比值），试对任意两点（两个变量）求出其路径长（两个变量的比值）

> 代码

```java
class Solution {
    public double[] calcEquation(List<List<String>> equations, double[] values, List<List<String>> queries) {
        Map<String, Map<String, Double>> graph = new HashMap();
        
        for (int i = 0; i < equations.size(); i++) {
            String first = equations.get(i).get(0);
            String second = equations.get(i).get(1);
            
            if (!graph.containsKey(first)) graph.put(first, new HashMap<String, Double>());
            if (!graph.containsKey(second)) graph.put(second, new HashMap<String, Double>());
            
            graph.get(first).put(second, values[i]);
            graph.get(second).put(first, 1.0/values[i]);
        }
        
        double[] ans = new double[queries.size()];
        for (int i = 0; i < queries.size(); i++) {
            String first = queries.get(i).get(0);
            String second = queries.get(i).get(1);
            
            ans[i] = dfs(first, second, graph, new HashSet<String>());            
        }
        
        return ans;
    }
    
    public double dfs(String current, String target, Map<String, Map<String, Double>> graph, Set<String> visited) {
        
        if (!graph.containsKey(current) || !graph.containsKey(target))
            return -1.0;
        
        if (graph.get(current).containsKey(target))
            return graph.get(current).get(target);
        
        visited.add(current);
        for (String nei: graph.get(current).keySet()) {
            if (!visited.contains(nei)) {
                double tmp = dfs(nei, target, graph, visited);
                if (tmp != -1.0)
                    return graph.get(current).get(nei) * tmp;
            }
        }
        
        return -1.0;
    }
}
```

> 复杂度分析

时间复杂度O(ML+Q⋅(L+M))，其中 MM 为边的数量，QQ 为询问的数量，LL 为字符串的平均长度。

无额外使用变量，空间复杂度O(NL+M)，其中 NN 为点的数量，MM 为边的数量，LL 为字符串的平均长度。

> 总结

Runtime: 1 ms, faster than 88.82% of Java online submissions for Evaluate Division.

Memory Usage: 39.2 MB, less than 14.01% of Java online submissions for Evaluate Division.
