### LeetCode-384-Shuffle-an-Array

> 题目链接

[LeetCode-384-Shuffle-an-Array](https://leetcode.com/problems/shuffle-an-array/)

> 思路

Fisher-Yates 洗牌算法，遍历的时候，每个数字随机交换一次，确保结果为n!

> 代码

```java
class Solution {
    private int[] array;
    private int[] original;
    Random rand = new Random();
    
    private int randRange(int min, int max) {
        return rand.nextInt(max - min) + min;
    }

    private void swapAt(int i, int j) {
        int temp = array[i];
        array[i] = array[j];
        array[j] = temp;
    }

    public Solution(int[] nums) {
        array = nums;
        original = nums.clone();
    }
    
    public int[] reset() {
        return original;
    }
    
    public int[] shuffle() {
        for (int i = 0; i < array.length; i++) {
            swapAt(i, randRange(i, array.length));
        }
        return array;
    }
}
```

> 复杂度分析

需要遍历一遍数组，时间复杂度O(n)

需要保存原来的数组，空间复杂度O(n)

> 总结

Runtime: 74 ms, faster than 76.37% of Java online submissions for Shuffle an Array.

Memory Usage: 47.8 MB, less than 21.18% of Java online submissions for Shuffle an Array.
