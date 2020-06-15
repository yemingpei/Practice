### LeetCode-401-Binary-Watch

> 题目链接

[LeetCode-401-Binary-Watch](https://leetcode.com/problems/binary-watch/)

> 思路

贪心算法，先列出所有可能，一一遍历

> 代码

```java
class Solution {
    public List<String> readBinaryWatch(int num) {
        List<String> ans = new ArrayList<String>();
        String[][] hstrs = {{"0"}, {"1","2","4","8"}, {"3","5","6","9","10"}, {"7","11"}};
        String[][] mstrs = {{"00"}, {"01","02","04","08","16","32"}, {"03","05","06","09","10","12","17","18","20","24","33","34","36","40","48"}, {"07","11","13","14","19","21","22","25","26","28","35","37","38","41","42","44","49","50","52","56"}, {"15","23","27","29","30","39","43","45","46","51","53","54","57","58"}, {"31","47","55","59"}};
        int min = Math.min(3,num);
        StringBuilder tmp = new StringBuilder();
        for(int i = 0; i <= min; i++) {
            if (num - i > 5) continue;
            String[] hstr = hstrs[i];
            String[] mstr = mstrs[num - i];
            for(int j = 0; j < hstr.length; j++) {
                for(int k = 0; k < mstr.length; k++) {
                    tmp.setLength(0);
                    tmp.append(hstr[j]).append(":").append(mstr[k]);
                    ans.add(tmp.toString());
                };
            };
        };
        return ans;
    }
}
```

> 复杂度分析

双循环有限次，时间复杂度O(1)

额外使用有限个数组空间，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Binary Watch.

Memory Usage: 38.3 MB, less than 70.80% of Java online submissions for Binary Watch.
