### LeetCode-face-17-07

> 题目链接

[LeetCode-face-17-07](https://leetcode-cn.com/problems/baby-names-lcci/)

> 思路

并查集，先构建出现的次数的hash表，然后寻找父子关系，合并次数

> 代码

```java
class Solution {
    private final Map<String, Integer> idMap = new HashMap<>();
    private int[] parent;
    private String[] nameMap;
    private int currentId = 1;

    public String[] trulyMostPopular(String[] names, String[] synonyms) {
        int vertexSize = names.length + (synonyms.length << 1);
        parent = new int[vertexSize];
        nameMap = new String[vertexSize];
        for (String name : names) {
            int index = name.indexOf('(');
            String realName = name.substring(0, index);
            int nameId = distributeId(realName);
            int frequency = 0;
            for (index++; name.charAt(index) != ')'; index++) {
                frequency = frequency * 10 + name.charAt(index) - '0';
            }
            parent[nameId] = -frequency;
        }
        for (String synonym : synonyms) {
            int index = synonym.indexOf(',');
            int nameId1 = distributeId(synonym.substring(1, index));
            int nameId2 = distributeId(synonym.substring(index + 1, synonym.length() - 1));
            union(nameId1, nameId2);
        }
        LinkedList<String> result = new LinkedList<>();
        for (int i = 1; i < currentId; i++) {
            if (parent[i] <= 0) {
                StringBuilder builder = new StringBuilder(nameMap[i]);
                result.add(builder.append('(').append(-parent[i]).append(')').toString());
            }
        }
        return result.toArray(new String[0]);
    }

    private int distributeId(String name) {
        Integer nameId = idMap.putIfAbsent(name, currentId);
        if (nameId == null) {
            nameId = currentId++;
        }
        nameMap[nameId] = name;
        return nameId;
    }

    private void union(int vertex1, int vertex2) {
        int root1 = find(vertex1), root2 = find(vertex2);
        if (root1 == root2) {
            return;
        }
        if (nameMap[root1].compareTo(nameMap[root2]) > 0) {
            parent[root2] += parent[root1];
            parent[root1] = root2;
        } else {
            parent[root1] += parent[root2];
            parent[root2] = root1;
        }
    }

    private int find(int vertex) {
        if (parent[vertex] <= 0) {
            return vertex;
        }
        return parent[vertex] = find(parent[vertex]);
    }
}
```

> 复杂度分析

遍历数组构建哈希表，时间复杂度O(n + m)

额外使用hashmap，空间复杂度O(n)

> 总结

执行用时：34 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：47.2 MB, 在所有 Java 提交中击败了29.58%的用户
