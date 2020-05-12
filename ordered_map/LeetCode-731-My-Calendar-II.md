### LeetCode-731-My-Calendar-II

> 题目链接

[LeetCode-731-My-Calendar-II](https://leetcode.com/problems/my-calendar-ii/)

> 思路

利用二叉搜索树的思想，完成二分查找的时间复杂度，插入数据也方便，和节点比较，大的就去右子树找，小的就去左子树找

> 代码

```java
class MyCalendarTwo {

    Node root;

    class Node {
		int start, end;
		Node left, right;
		boolean overlap;

		Node(int s, int e) {
			start = s;
			end = e;
		}
	}
    
    public MyCalendarTwo() {
    }

	public boolean book(int start, int end) {
		if (root == null) {
			root = new Node(start, end);
			return true;
		}

		if (!isInsertable(root, start, end)) {
			return false;
		}

		insert(root, start, end);

		return true;
	}

	private Node insert(Node node, int start, int end) {
		if (node == null)
			return new Node(start, end);

		if (node.start >= end)
			node.left = insert(node.left, start, end);
		else if (node.end <= start)
			node.right = insert(node.right, start, end);
		else {
			node.overlap = true;

			int minS = Math.min(node.start, start);
			int maxS = Math.max(node.start, start);
			int minE = Math.min(node.end, end);
			int maxE = Math.max(node.end, end);

			if (minS != maxS) {
				node.left = insert(node.left, minS, maxS);
			}
			if (minE != maxE) {
				node.right = insert(node.right, minE, maxE);
			}
			if (maxS != minE) {
				node.start = maxS;
				node.end = minE;
			}
		}

		return node;
	}

	private boolean isInsertable(Node node, int start, int end) {
		if (node == null)
			return true;
		if (node.start >= end)
			return isInsertable(node.left, start, end);
		if (node.end <= start)
			return isInsertable(node.right, start, end);

		if (node.overlap)
			return false;
		if (node.start <= start && node.end >= end)
			return true;
		return isInsertable(node.left, start, end) && isInsertable(node.right, start, end);
	}
    
}

/**
 * Your MyCalendarTwo object will be instantiated and called as such:
 * MyCalendarTwo obj = new MyCalendarTwo();
 * boolean param_1 = obj.book(start,end);
 */
```

> 复杂度分析

利用二叉搜索树的概念，小的在左边，大的在右边，最坏情况是O(n)，时间均摊复杂度O(logn)

额外使用树结构，空间复杂度O(n)

> 总结

Runtime: 11 ms, faster than 99.64% of Java online submissions for My Calendar II.

Memory Usage: 39.9 MB, less than 100.00% of Java online submissions for My Calendar II.
