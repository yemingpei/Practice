### LeetCode-offer-11

> 题目链接

[LeetCode-offer-11](https://leetcode-cn.com/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/)

> 思路

分为三种情况，如果mid > right，则在右边，否则 mid > left，则最小值在左边区间，其他情况右边界不断变小

> 代码

```java
class Solution {
    public int minArray(int[] numbers) {
        int left = 0;
        int right = numbers.length - 1;
        while(right > left){
            int mid = (right - left) / 2 + left;
            if(numbers[mid] > numbers[right])
                left = mid + 1;
            else if(numbers[mid] > numbers[left])
                right = mid - 1;
            else right--;
        }
        return numbers[left];
    }
}
```

> 复杂度分析

二分查询，时间复杂度O(logn)

只保存两个常量值，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.2 MB, 在所有 Java 提交中击败了70.61%的用户
