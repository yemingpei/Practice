### LeetCode-face-08-14

> 题目链接

[LeetCode-face-08-14](https://leetcode-cn.com/problems/boolean-evaluation-lcci/)

> 思路

动态规划，x和y坐标分别代表起点和结束点，y坐标表示boolean的结果，保存的值是个数

> 代码

```java
class Solution {
    public int countEval(String s, int result) {
        int length = s.length();
        int[][][] nums = new int[length][length][2];
        for(int i = 0; i < length; i+=2){
            nums[i][i][0] = s.charAt(i) == '0' ? 1 : 0;
            nums[i][i][1] = s.charAt(i) == '1' ? 1 : 0;
        }
        for(int k = 3; k <= length; k+=2){
            for(int i = 0, j = i + k - 1; j < length; i += 2,j += 2){
                for(int z = i + 1; z < j; z += 2){
                    switch(s.charAt(z)){
                        case '&':
                            nums[i][j][0] += nums[i][z - 1][0] * nums[z + 1][j][0];
                            nums[i][j][0] += nums[i][z - 1][1] * nums[z + 1][j][0];
                            nums[i][j][0] += nums[i][z - 1][0] * nums[z + 1][j][1];
                            nums[i][j][1] += nums[i][z - 1][1] * nums[z + 1][j][1];
                            break;
                        case '|':
                            nums[i][j][0] += nums[i][z - 1][0] * nums[z + 1][j][0];
                            nums[i][j][1] += nums[i][z - 1][1] * nums[z + 1][j][0];
                            nums[i][j][1] += nums[i][z - 1][0] * nums[z + 1][j][1];
                            nums[i][j][1] += nums[i][z - 1][1] * nums[z + 1][j][1];
                            break;
                        case '^':
                            nums[i][j][0] += nums[i][z - 1][0] * nums[z + 1][j][0];
                            nums[i][j][1] += nums[i][z - 1][1] * nums[z + 1][j][0];
                            nums[i][j][1] += nums[i][z - 1][0] * nums[z + 1][j][1];
                            nums[i][j][0] += nums[i][z - 1][1] * nums[z + 1][j][1];
                            break;
                    }
                }
            }
        }
        return nums[0][length - 1][result];
    }
}
```

> 复杂度分析

需要三重遍历，检索长度固定的值，时间复杂度O(n ^ 3) 

额外使用int三维数组，z坐标长度是2，固定，所以可以略去，空间复杂度O(n ^ 2)

> 总结

执行用时：5 ms, 在所有 Java 提交中击败了69.87%的用户

内存消耗：38.3 MB, 在所有 Java 提交中击败了16.59%的用户
