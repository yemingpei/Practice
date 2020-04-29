### LeetCode-179-Largest-Number

> 题目链接

[LeetCode-179-Largest-Number](https://leetcode.com/problems/largest-number/)

> 思路
```java
//例子1： 789  90（很简单，顺着比大小）       结果 90789
//例子2： 3   334（等价于 333 和 334顺着比）  结果 3343
//例子3： 121  12（等价于 121 和1212顺着比）  结果 12121
```

转成字符串，然后比较大小，数字a和b如果使用”ab“和“ba”比较，比较长度会变长，时间会变慢，所以自己比较。例子1很简单，顺着从头到尾比较，谁大，谁就大，例子2和例子3
其实是一样的，短的是长的前缀，根据两者要前后合并，则需要复制短的使长度等于或者大于长的，在比较

> 代码

```java
class Solution {
    public String largestNumber(int[] nums) {
        String[] strings = new String[nums.length];
        for (int i = 0; i < nums.length; i++) {
            strings[i] = String.valueOf(nums[i]);
        }
        Arrays.sort(strings, new Comparator<String>() {
            @Override
            public int compare(String s1, String s2) {
                return compareNum(s2, s1);
            }
        });
        if("0".equals(strings[0])){
            return "0";
        }
        StringBuilder stringBuilder = new StringBuilder();
        for (int i = 0; i < strings.length; i++) {
            stringBuilder.append(strings[i]);
        }
        return stringBuilder.toString();
    }
    
    public int compareNum(String s1, String s2) {
		if (s1.equals(s2)) return 0;
		if (s1.startsWith(s2)) return compareNum(s1.substring(s2.length()), s2);
		if (s2.startsWith(s1)) return compareNum(s1, s2.substring(s1.length()));
		int index = 0;
		while (index < s1.length() && index < s2.length()) {
			char ch1 = s1.charAt(index);
			char ch2 = s2.charAt(index);
			if (ch1 > ch2) return 1;
			else if (ch1 < ch2) return -1;
			index++;
		}

		return 0;
	}
}
```

> 复杂度分析

快速排序，时间复杂度O(nlgn)

额外使用string数组，空间复杂度O(n)

> 总结

Runtime: 3 ms, faster than 99.75% of Java online submissions for Largest Number.
Memory Usage: 38.7 MB, less than 6.67% of Java online submissions for Largest Number.
