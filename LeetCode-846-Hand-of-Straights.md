### LeetCode-846-Hand-of-Straights

> 题目链接

[LeetCode-846-Hand-of-Straights](https://leetcode.com/problems/hand-of-straights/)

> 思路

要求能分成大小是W的若干数组，则hand的长度，必然整除W，存在规律，每个元素% W 为一个桶，必然每个桶的个数都为hand.length / W，再证明数字是连续的就可以了

> 代码

```java
class Solution {
    public boolean isNStraightHand(int[] hand, int W) {
        if (hand.length % W != 0) return false;
        int[] count = new int[W];
        int H = hand.length / W;
        Set<Integer> set = new HashSet<Integer>();
        for (int card : hand){ 
        	int position = card % W;
            count[position]++;
            if(count[position]>H) return false;
            set.add(card);
        }
        Set<Integer> filterSet = new HashSet<Integer>();
        for (int key : set) {
        	if(filterSet.contains(key)) continue;
            int start = key;
            int end = key;
            filterSet.add(key);
            while (set.contains(start - 1)) {
                start--;
                filterSet.add(start);
            }
            while (set.contains(end + 1)) {
                end++;
                filterSet.add(end);
            }
            if (end - start + 1 < W) return false;
            break;
        }
        return true;
    }
}
```

> 复杂度分析

for循环遍历了一遍数组记录位置，如果有超出hand.length / W 直接返回 false 再遍历一次set，看里面的数字是否是连续的，时间复杂度O(n)

使用了两个set集合来记录元素，一个int数组来统计位数，空间复杂度O(n)

> 总结

Runtime: 18 ms, faster than 91.90% of Java online submissions for Hand of Straights.

Memory Usage: 52.4 MB, less than 6.25% of Java online submissions for Hand of Straights.
