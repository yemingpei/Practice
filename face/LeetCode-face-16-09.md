### LeetCode-face-16-09

> 题目链接

[LeetCode-face-16-09](https://leetcode-cn.com/problems/operations-lcci/)

> 思路

先统计不同次幂的正负数，然后转换为加法

> 代码

```java
class Operations {
    int ne = Integer.MAX_VALUE + Integer.MAX_VALUE + 1;
    long[] neCache = new long[32];// 放置 -1,-2,-4,-8...
    long[] poCache = new long[32];// 放置 1,2,4,8...
    long[] cache = new long[32];// 存放乘数或除数的倍数，1*a,2*a,4*a,8*a...主要用于快速计算，不然容易超时
    long[] cache1 = new long[32];// 存放乘数或除数的倍数 负数-1*a,-2*a,-4*a,-8*a
    public Operations() {
        neCache[0] = ne;
        poCache[0] = 1;
        for (int i = 1; i < 32; ++i) {
            neCache[i] = neCache[i + ne] + neCache[i + ne];
            poCache[i] = poCache[i + ne] + poCache[i + ne];
        }
    }
    public int minus(int a, int b) {
        if (a == b) return 0;
        int index = 31;// 从最大值开始比较
        while (b != 0) {
            if (b > 0) {
                if (b >= poCache[index]) { // 如果b大于2的index次方，
                    b += neCache[index];// a与b同时减
                    a += neCache[index];
                } else {
                    index += ne;
                }
            } else { // b小于0时同理
                if (b <= neCache[index]) {
                    b += poCache[index];
                    a += poCache[index];
                } else {
                    index += ne;
                }
            }
        }
        return a;
    }

    public int multiply(int a, int b) {
        if (a == 0 || b == 0) return 0;
        if (a == 1) return b;
        if (b == 1) return a;
        if (a == ne) return minus(0, b);
        if (b == ne) return minus(0, a);
        int sign = (a > 0 && b > 0) || (a < 0 && b < 0) ? 1 : ne;
        // 把b变成正数
        if (b < 0) {
            b = minus(0, b);
        }

        cache[0] = a;
        for (int i = 1; i < 32; i++) {
            cache[i] = cache[i + ne] + cache[i + ne];
        }
        int index = 30; // 从31开始应该也是可以的
        int ret = 0;
        int retSign = a > 0 ? 1 : ne; // 记录返回值的符号
        while (b > 0) {
            if (b >= poCache[index]) {
                b += neCache[index];
                ret += cache[index];
                retSign = ret > 0 ? 1 : ne;// 记录返回值的符号
            } else {
                index += ne;
            }
        }
        // 根据初始值改变返回值的符号
        if ((sign < 0 && ret > 0) || (sign > 0 && ret < 0)) {
            ret = minus(0, ret);
        }
        // 结果溢出，返回值的符号会变成相反的
        if (retSign != (a > 0 ? 1 : ne)) {
            ret = minus(0, ret);
        }
        return ret;
    }

    public int divide(int a, int b) {
        if (a == 0) return 0;
        if (b == 1) return a;
        if (b == ne) return minus(0, a);
        int ret = 0;
        int sign = (a > 0 && b > 0) || (a < 0 && b < 0) ? 1 : ne;
        long nb = b;
        long pb = b;
        if (b < 0) {
            b = minus(0, b);
        } else {
            nb = minus(0, b);
        }
        if (a < 0) {
            a = minus(0, a);
        }
        cache[0] = b;
        cache1[0] = nb;
        int index = 1;
        for (; index < 32; ++index) {
            cache[index] = cache[index + ne] + cache[index + ne];
            cache1[index] = cache1[index + ne] + cache1[index + ne];
            if (cache[index] >= a) {
                break; // 找到最大值就可以返回了，不用计算完
            }
        }
        if (index >= 32) index = 31;
        while (a >= b) {
            if (a >= cache[index]) {
                ret += poCache[index];// 注意这里是2的index次方的值
                a += cache1[index];
            } else {
                index += ne;
            }
        }
        if (sign < 0) {
            ret = minus(0, ret);
        }
        return ret;
    }
}
```

> 复杂度分析

操作不超过32次，时间复杂度O(1)

额外使用固定长度的long数组，空间复杂度O(1)

> 总结

执行用时：19 ms, 在所有 Java 提交中击败了72.03%的用户

内存消耗：38.4 MB, 在所有 Java 提交中击败了62.24%的用户
