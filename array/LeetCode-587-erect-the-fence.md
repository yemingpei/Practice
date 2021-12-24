### LeetCode-587-erect-the-fence

> 题目链接

[LeetCode-587-erect-the-fence](https://leetcode-cn.com/problems/erect-the-fence/)

> 思路

先排序，然后通过范围确定点的关系

> 代码

```java
class Solution {
    public int[][] outerTrees(int[][] trees) {
        if (trees == null || trees.length == 0 || trees[0].length == 0){
            return new int[0][0];
        }
        int n = trees.length;
        int[][] stack = new int[n << 1][];
        int size = 0;
        Arrays.sort(trees, (a, b) -> (a[0] != b[0] ? a[0] - b[0] : a[1] - b[1]));
        for (int i = 0; i < n; i++){
            while (size > 1 && cross(stack[size - 2], stack[size - 1], trees[i]) > 0){
                size--;
            }
            stack[size++] = trees[i];
        }
        for (int i = n - 2; i >= 0; i--){
            while (size > 1 && cross(stack[size - 2], stack[size - 1], trees[i]) > 0){
                size--;
            }
            stack[size++] = trees[i];
        }
        Arrays.sort(stack,0, size,  (a, b) ->(a[0] != b[0] ? a[0] - b[0] : a[1] - b[1]));
        int index = 1;
        for (int i = 1; i < size; i++){
            if (stack[i][0] == stack[i - 1][0] && stack[i][1] == stack[i - 1][1]){
                continue;
            }
            stack[index++] = stack[i];
        }
        return Arrays.copyOf(stack, index);
    }

    public static int cross(int[] a, int[] b, int[] c){
        return (c[0] - a[0]) * (b[1] - a[1]) - (b[0] - a[0]) * (c[1] - a[1]);
    }
}
```

> 复杂度分析

使用了排序，时间复杂度O(nlogn)

额外使用二维数组，空间复杂度O(mn)

> 总结

执行用时：6 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：39.4 MB, 在所有 Java 提交中击败了81.69%的用户
