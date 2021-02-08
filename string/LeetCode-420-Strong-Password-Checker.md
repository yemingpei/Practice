### LeetCode-420-Strong-Password-Checker

> 题目链接

[LeetCode-420-Strong-Password-Checker](https://leetcode.com/problems/strong-password-checker/)

> 思路

长度 <6 ，步数=缺失类型和缺失长度取大者。

长度 (6,20)，这时候我们不需要低效的插入和删除来处理连续字符，直接替换步数就等于处理连续字和缺失类型取大者。

比较负载的是 >20，我们需要知道优先级，一样优先处理连续数组。

优先处理缺失类型，用替换的方式来处理，这时候要替换的连续组的连续数 %3==2 -> 连续数%3==1 -> 连续数%3==0，然后处理多余字符，删除的优先级是连续组的连续数 %3==0 -> 连续数%3==1 -> 连续数%3==2。

> 代码

```java
class Solution {
    public int strongPasswordChecker(String s) {
	    int res = 0, a = 1, A = 1, d = 1;
	    char[] carr = s.toCharArray();
	    int[] arr = new int[carr.length];
	        
	    for (int i = 0; i < arr.length;) {
	        if (Character.isLowerCase(carr[i])) a = 0;
	        if (Character.isUpperCase(carr[i])) A = 0;
	        if (Character.isDigit(carr[i])) d = 0;
	            
	        int j = i;
	        while (i < carr.length && carr[i] == carr[j])
                i++;
	        arr[j] = i - j;
	    }
	        
	    int total_missing = (a + A + d);

	    if (arr.length < 6) 
	        res += total_missing + Math.max(0, 6 - (arr.length + total_missing));
	    else {
	        int over_len = Math.max(arr.length - 20, 0), left_over = 0;
	        res += over_len;
	            
	        for (int k = 1; k < 3; k++) {
	            for (int i = 0; i < arr.length && over_len > 0; i++) {
	                if (arr[i] < 3 || arr[i] % 3 != (k - 1)) continue;
	                arr[i] -= Math.min(over_len, k);
	                over_len -= k;
	            }
	        }
	            
	        for (int i = 0; i < arr.length; i++) {
	            if (arr[i] >= 3 && over_len > 0) {
	                int need = arr[i] - 2;
	                arr[i] -= over_len;
	                over_len -= need;
	            }
	                
	            if (arr[i] >= 3) left_over += arr[i] / 3;
	        }
	            
	        res += Math.max(total_missing, left_over);
	    }
	        
	    return res;
	}
}
```

> 复杂度分析

双重循环检测，时间复杂度O(n ^ 2)

额外使用数组来保存，空间复杂度O(n)。

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Strong Password Checker.

Memory Usage: 37 MB, less than 55.01% of Java online submissions for Strong Password Checker.
