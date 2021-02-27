### LeetCode-433-Minimum-Genetic-Mutation

> 题目链接

[LeetCode-433-Minimum-Genetic-Mutation](https://leetcode.com/problems/minimum-genetic-mutation/)

> 思路

通过起点去搜寻变化的点，广度索搜

> 代码

```java
class Solution {
    public int minMutation(String start, String end, String[] bank) {
        HashSet<String> set = new HashSet<>(Arrays.asList(bank));
        if (!set.contains(end)) {
            return -1;
        }
        char[] four = {'A', 'C', 'G', 'T'};
        Queue<String> queue = new LinkedList<>();
        queue.offer(start);
        set.remove(start);
        int step = 0;
        while (queue.size() > 0) {
            step++;
            for (int count = queue.size(); count > 0; --count) {
                char[] temStringChars = queue.poll().toCharArray();
                for (int i = 0, len = temStringChars.length; i < len; ++i) {
                    char oldChar = temStringChars[i];
                    for (int j = 0; j < 4; ++j) {
                        temStringChars[i] = four[j];
                        String newGenetic = new String(temStringChars);
                        if (end.equals(newGenetic)) {
                            return step;
                        } else if (set.contains(newGenetic)) {
                            set.remove(newGenetic);
                            queue.offer(newGenetic);
                        }
                    }
                    temStringChars[i] = oldChar;
                }
            }
        }
        return -1;
    }
}
```

> 复杂度分析

检测bank中的元素，时间复杂度O(n)

额外使用set来保存数据，空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Minimum Genetic Mutation.

Memory Usage: 39.1 MB, less than 5.67% of Java online submissions for Minimum Genetic Mutation.
