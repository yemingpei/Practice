### LeetCode-183-Customers-Who-Never-Order

> 题目链接

[LeetCode-183-Customers-Who-Never-Order](https://leetcode.com/problems/customers-who-never-order/)

> 思路

SQL如下

> 代码

```java
select customers.name as 'Customers'
from customers
where customers.id not in
(
    select customerid from orders
);
```

> 总结

Runtime: 499 ms, faster than 72.59% of MySQL online submissions for Customers Who Never Order.

Memory Usage: 0B, less than 100.00% of MySQL online submissions for Customers Who Never Order.
