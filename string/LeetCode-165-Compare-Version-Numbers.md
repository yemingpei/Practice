### LeetCode-165-Compare-Version-Numbers

> 题目链接

[LeetCode-165-Compare-Version-Numbers](https://leetcode.com/problems/compare-version-numbers/)

> 思路

先遍历到第一个数，然后转换数字比较，不想等则提前退出

> 代码

```java
class Solution {
    public int compareVersion(String version1, String version2) {
        int length1 = version1.length();
        int length2 = version2.length();
        int firstPosition = 0;
        int secondPosition = 0;
        while(length1 > firstPosition || length2 > secondPosition){
            int first = 0;
            int second = 0;
            boolean firstBreak = length1 != firstPosition;
            boolean secondBreak = length2 != secondPosition;
            for(int i = firstPosition; i < length1; i++){
                if(version1.charAt(i) == '.'){
                    first = Integer.parseInt(version1.substring(firstPosition, i));
                    firstPosition = i + 1;
                    firstBreak = false;
                    break;
                }
            }
            if(firstBreak) {
                first = Integer.parseInt(version1.substring(firstPosition, length1));
                firstPosition = length1;
            }
            for(int i = secondPosition; i < length2; i++){
                if(version2.charAt(i) == '.'){
                    second = Integer.parseInt(version2.substring(secondPosition, i));
                    secondPosition = i + 1;
                    secondBreak = false;
                    break;
                }
            }
            if(secondBreak) {
                second = Integer.parseInt(version2.substring(secondPosition, length2));
                secondPosition = length2;
            }
            if(first > second) return 1;
            else if(first < second) return -1;
        }
        return 0;
    }
}
```

> 复杂度分析

最多遍历两个字符串 ，时间复杂度O(n + m)

最多8个辅助变量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Compare Version Numbers.

Memory Usage: 36.8 MB, less than 99.78% of Java online submissions for Compare Version Numbers.
