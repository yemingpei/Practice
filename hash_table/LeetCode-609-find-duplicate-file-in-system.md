### LeetCode-609-find-duplicate-file-in-system

> 题目链接

[LeetCode-609-find-duplicate-file-in-system](https://leetcode-cn.com/problems/find-duplicate-file-in-system/)

> 思路

用map来记录文件的路径，利用哈希记录相关的路径

> 代码

```java
class Solution {
    public List<List<String>> findDuplicate(String[] paths) {
        HashMap<String, ArrayList<String>> map = new HashMap<>();
        StringBuilder sb = new StringBuilder();
        for (String path : paths) {
            String[] subArr = path.split(" ");
            for (int i = 1; i < subArr.length; ++i) {
                int l = subArr[i].indexOf('(');
                int r = subArr[i].indexOf(')');
                String fileName = subArr[i].substring(0, l);
                String content = subArr[i].substring(l + 1, r);
                ArrayList<String> fullPaths = map.get(content);
                if (fullPaths == null) {
                    fullPaths = new ArrayList<>();
                    map.put(content, fullPaths);
                }
                sb.append(subArr[0]).append('/').append(fileName);
                fullPaths.add(sb.toString());
                sb.setLength(0);
            }
        }
        List<List<String>> ret = new ArrayList<>();
        for (ArrayList<String> fullPaths : map.values()) {
            if (fullPaths.size() >= 2) {
                ret.add(fullPaths);
            }
        }
        return ret;
    }
}
```

> 复杂度分析

遍历字符串数组，分割后的也需要遍历，时间复杂度O(nm)

额外使用map，空间复杂度O(n)

> 总结

执行用时：18 ms, 在所有 Java 提交中击败了94.85%的用户

内存消耗：47.6 MB, 在所有 Java 提交中击败了41.75%的用户
