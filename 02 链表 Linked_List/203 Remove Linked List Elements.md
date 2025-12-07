# 203. Remove Linked List Elements
[LeetCode Link](https://leetcode.cn/problems/remove-linked-list-elements/)


**Problem**  
Given the `head` of a singly linked list and an integer `val`, remove **all** the nodes of the linked list that have `Node.val == val`, and return the new head of the list.

**Example**

```text
Input: head = [1,2,6,3,4,5,6], val = 6
Output: [1,2,3,4,5]
Explanation: Nodes with value 6 are removed.
```

**My Understanding**

```text

```

**Solution Code**

```python
（版本一）虚拟头节点法删除头节点
class Solution:
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
        # 创建虚拟头部节点以简化删除过程
        dummy_head = ListNode(next = head) # 创建一个新节点，其 next 指针指向原链表的头节点

        # 遍历列表并删除值为val的节点
        current = dummy_head
        while current.next:
            if current.next.val == val:
                current.next = current.next.next #通过跳过当前节点的下一个节点，将其从链表中移除，从而实现删除效果。
            else:
                current = current.next

        return dummy_head.next
```
