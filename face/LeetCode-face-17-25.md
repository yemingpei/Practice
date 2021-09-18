### LeetCode-face-17-25

> 题目链接

[LeetCode-face-17-25](https://leetcode-cn.com/problems/word-rectangle-lcci/)

> 思路

先构建字典树,然后利用回溯不断深度搜索寻找结果，然后剪枝，节省时间

> 代码

```java
class Solution {
    class Node{
        char c;
        boolean end;
        Node[] son = new Node[26];
        Node(char c){this.c = c;}
    }
    Node root = new Node('0');
    void add(String word){
        Node p = root;
        for(char c : word.toCharArray()){
            int u = c - 'a';
            if(p.son[u] == null) p.son[u] = new Node(c);
            p = p.son[u];
        }
        p.end = true;
    } 
    List<String> ans; 
    int maxArea = 0;
    public String[] maxRectangle(String[] words) {
        Map<Integer, Set<String>> map = new TreeMap<>();
        for(String word : words){
            add(word);
            int len = word.length();
            Set<String> set = map.get(len);
            if(set == null) map.put(len, set = new HashSet());
            set.add(word);
        }
        for(Map.Entry<Integer, Set<String>> entry : map.entrySet()){
            int len = entry.getKey();
            Node nodes[] = new Node[len];
            Arrays.fill(nodes, root);
            dfs(entry.getValue(), new ArrayList<>(), nodes);
        }
        return ans.toArray(new String[0]);
    }

    void dfs(Set<String> set, List<String> list, Node[] nodes){
        int len = nodes.length;
        if(len * len <= maxArea || list.size() == len)return;
        Node next[] = new Node[len];
        search:
        for(String word : set){
            boolean valid = true;
            for(int i = 0; i < len; i++){
                char c = word.charAt(i);
                int j = c - 'a';
                if(nodes[i].son[j] == null) continue search;
                valid &= nodes[i].son[j].end; 
                next[i] = nodes[i].son[j];
            }
            list.add(word);
            if(valid && maxArea < len * list.size()){
                maxArea = len * list.size();
                ans = new ArrayList(list);
            }
            dfs(set, list, next);
            list.remove(list.size() - 1);
        }
    }
}
```

> 复杂度分析

需要回溯遍历，时间复杂度O(n ^ 2*logn)

额外使用map辅助，空间复杂度O(n)

> 总结

执行用时：52 ms, 在所有 Java 提交中击败了94.21%的用户

内存消耗：49 MB, 在所有 Java 提交中击败了49.59%的用户
