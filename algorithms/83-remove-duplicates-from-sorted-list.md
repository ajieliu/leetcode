# [83. 删除排序链表中的重复元素](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list/) - easy

<p>存在一个按升序排列的链表，给你这个链表的头节点 <code>head</code> ，请你删除所有重复的元素，使每个元素 <strong>只出现一次</strong> 。</p>

<p>返回同样按升序排列的结果链表。</p>

<p> </p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/01/04/list1.jpg" style="width: 302px; height: 242px;" />
<pre>
<strong>输入：</strong>head = [1,1,2]
<strong>输出：</strong>[1,2]
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/01/04/list2.jpg" style="width: 542px; height: 222px;" />
<pre>
<strong>输入：</strong>head = [1,1,2,3,3]
<strong>输出：</strong>[1,2,3]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li>链表中节点数目在范围 <code>[0, 300]</code> 内</li>
	<li><code>-100 <= Node.val <= 100</code></li>
	<li>题目数据保证链表已经按升序排列</li>
</ul>


## Solutions

这个简单。复杂版本 [82. 删除排序链表中的重复元素 II](./82-remove-duplicates-from-sorted-list-ii.md)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        
        p = head
        while p and p.next:
            if p.val == p.next.val:
                while p.next and p.val == p.next.val:
                    p.next = p.next.next
            else:
                p = p.next
        return head
```
