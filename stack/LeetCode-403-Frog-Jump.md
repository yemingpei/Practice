### LeetCode-403-Frog-Jump

> 题目链接

[LeetCode-403-Frog-Jump](https://leetcode.com/problems/frog-jump/)

> 思路

用set来保存能站的石头，然后用双栈来保存跳的步数和石头，能达到终点就提前剪枝

> 代码

```java
class Solution {
    public boolean canCross(int[] stones) {
        for (int i = 3; i < stones.length ; i++){
            if(stones[i] > stones[i-1] * 2) return false;
        }
        int lastStone = stones[stones.length-1];
        HashSet<Integer> set = new HashSet<>();
        for(int stone: stones){
            set.add(stone);
        }
        Stack<Integer> positions = new Stack<>();
        Stack<Integer> jumps = new Stack<>();
        positions.add(0);
        jumps.add(0); 
        while(!positions.isEmpty()){
            int position = positions.pop();
            int jumpD = jumps.pop();
            for(int i = jumpD - 1; i <= jumpD + 1 ; i++){
                if(i <= 0) continue;
                int nextPosition = position + i;
                if(nextPosition == lastStone)  return true;
                else if(set.contains(nextPosition)){
                    positions.add(nextPosition);
                    jumps.add(i);
                }
            }
        }
        return false;
    }
}
```

> 复杂度分析

用栈模拟青蛙跳，每次k到k - 1步，时间复杂度O(n ^ 2)

额外使用了栈和set辅助，来保存数据，空间复杂度O(n)

> 总结

Runtime: 5 ms, faster than 90.25% of Java online submissions for Frog Jump.

Memory Usage: 39.1 MB, less than 91.72% of Java online submissions for Frog Jump.
