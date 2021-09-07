### LeetCode-face-17-08

> 题目链接

[LeetCode-face-17-08](https://leetcode-cn.com/problems/circus-tower-lcci/)

> 思路

先根据身高升序，体重降序排序，然后再通过二分查找，配合贪心算法，寻找最长递增序列

> 代码

```java
class Solution {
    public int bestSeqAtIndex(int[] height, int[] weight) {
        int length = height.length;
        Person[] person = new Person[length];
        for (int i = 0; i < length; i++) 
            person[i] = new Person(height[i], weight[i]);
        Arrays.sort(person, (a, b) -> a.height != b.height ? a.height - b.height : b.weight - a.weight);
        int[] dp = new int[length];
        int res = 0;
        for (Person ps : person) {
            int i = 0, j = res;
            while (i < j) {
                int mid = i + (j - i) / 2;
                if (dp[mid] < ps.weight) i = mid + 1;
                else j = mid;
            }
            dp[i] = ps.weight;
            if (res == j) res++;
        }
        return res;
    }

    public static class Person {
        private int height;
        private int weight;

        public Person(int height, int weight) {
            this.height = height;
            this.weight = weight;
        }
    }
}
```

> 复杂度分析

排序，时间复杂度O(nlogn)

额外使用int数组辅助，空间复杂度O(n)

> 总结

执行用时：49 ms, 在所有 Java 提交中击败了93.95%的用户

内存消耗：40.4 MB, 在所有 Java 提交中击败了86.48%的用户
