### LeetCode-556-next-greater-element-iii

> 题目链接

[LeetCode-556-next-greater-element-iii](https://leetcode-cn.com/problems/next-greater-element-iii/)

> 思路

右边开始遍历，寻找第一个递减的位置，然后用该位置右边第一个比它大的位置的数字和他交换，然后把右边的数字倒序

> 代码

```java
class Solution {
    public int nextGreaterElement(int n) {
        char[] chars = String.valueOf(n).toCharArray();
        if (chars.length <= 1) {
            return -1;
        }
        int position = -1;
        for(int j = chars.length - 2; j >= 0; j--){
            if(chars[j] < chars[j + 1]){
                position = j;
                break;
            }
        }
        if(position == -1) return -1;
        for(int j = chars.length - 1; j > position; j--){
            if(chars[j] > chars[position]){
                char c = chars[j];
                chars[j] = chars[position];
                chars[position] = c;
                break;
            }
        }
        int start = position + 1;
        int right = chars.length - 1;
        while(right > start){
            char c = chars[right];
            chars[right] = chars[start];
            chars[start] = c;
            right--;
            start++;
        }
        long result = Long.parseLong(new String(chars));
        return result > Integer.MAX_VALUE ? -1 : (int) result;
    }
}
```

> 复杂度分析

遍历字符串，时间复杂度O(n)

额外使用char数组，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：34.9 MB, 在所有 Java 提交中击败了94.58%的用户
