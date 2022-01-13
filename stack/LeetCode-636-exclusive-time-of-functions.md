### LeetCode-636-exclusive-time-of-functions

> 题目链接

[LeetCode-636-exclusive-time-of-functions](https://leetcode-cn.com/problems/exclusive-time-of-functions/)

> 思路

利用栈来还原调度的情况，并进行计算

> 代码

```java
class Solution {
    public int[] exclusiveTime(int n, List<String> logs) {
        int[] time = new int[n];
        Stack<Integer> st = new Stack<Integer>();
        int lastTime = 0;
        for(String log : logs){
            int i = 0;
            for(; log.charAt(i)!=':'; i++);
            int id = Integer.parseInt(log.substring(0,i));
            boolean isStart = log.charAt(i+1)=='s';
            if(isStart){
                int startTime = Integer.parseInt(log.substring(i + 7));
                if(!st.isEmpty()){
                    time[st.peek()]+= startTime - lastTime;
                }
                lastTime = startTime;
                st.push(id);
            }
            else{
                int endTime = Integer.parseInt(log.substring(i + 5)) + 1;
                time[st.peek()] += endTime - lastTime;
                st.pop();
                lastTime = endTime;
            }
        }
        return time;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用栈，空间复杂度O(n)

> 总结

执行用时：9 ms, 在所有 Java 提交中击败了97.09%的用户

内存消耗：39 MB, 在所有 Java 提交中击败了70.94%的用户
