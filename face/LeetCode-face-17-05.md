### LeetCode-face-17-05

> 题目链接

[LeetCode-face-17-05](https://leetcode-cn.com/problems/find-longest-subarray-lcci/)

> 思路

先计算前缀和，字母代表 -1 ，数字代表加 1，然后求相同的前缀的最大范围。

> 代码

```java
class Solution {
    public String[] findLongestSubarray(String[] array) {
        HashMap<Integer, Integer> map = new HashMap<>();
        map.put(0, -1);
        int max = 0;
        int start = 0;
        int end = 0;
        int count = 0;
        for(int i = 0; i < array.length; i++){
            char ch = array[i].charAt(0);
            if(ch < '0' || ch > '9'){
                count--;
                if(map.containsKey(count)){
                    int gap = i - map.get(count);
                    if(gap > max){
                        max = gap;
                        start = map.get(count) + 1;
                        end = i + 1;
                    }
                }else{
                    map.put(count, i);
                }
            }else{
                count++;
                if(map.containsKey(count)){
                    int gap = i - map.get(count);
                    if(gap > max){
                        max = gap;
                        start = map.get(count) + 1;
                        end = i + 1;
                    }
                }else{
                    map.put(count, i);
                }
            }
        }
        return start == end ? new String[0] : Arrays.copyOfRange(array, start, end); 
    }
}
```

> 复杂度分析

遍历一遍数组，时间复杂度O(n)

额外使用map保存前缀和第一个出现的位置，空间复杂度O(n)

> 总结

执行用时：19 ms, 在所有 Java 提交中击败了73.59%的用户

内存消耗：53.6 MB, 在所有 Java 提交中击败了86.97%的用户
