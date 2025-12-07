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

**Solution**

```python
# 虚拟头节点法删除头节点
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
**Note**

*   Time Complexity: $O(log N)$
*   Space Complexity: $O(1)$

---

# 206. Reverse Linked List
[LeetCode Link](https://leetcode.cn/problems/reverse-linked-list/)


**Problem**  
Given the `head` of a singly linked list, reverse the list, and return *the reversed list*.

**Example**

```text
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```

**Example 2**

```text
Input: head = [1,2]
Output: [2,1]
```

**My Understanding**

```text

```

**Solution**

```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        prev = None   #已经处理好的node
        curr = head   #当前要处理的node

        while curr: # O(N)
            temp = curr.next  
            curr.next = prev  
            prev = curr      
            curr = temp       
            
        return prev
```
**Note**

*   Time Complexity: $O(N)$
*   Space Complexity: $O(1)$

---

# 24. Swap Nodes in Pairs
[LeetCode Link](https://leetcode.cn/problems/swap-nodes-in-pairs/)


**Problem**  
Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed).

**Example**

```text
Input: head = [1,2,3,4]
Output: [2,1,4,3]

Input: head = []
Output: []

Input: head = [1]
Output: [1]
```

**My Understanding**

```text

```

**Solution**

```python

class Solution:

```
**Note**

*   Time Complexity: $O(N)$
*   Space Complexity: $O(1)$

---

# 19. Remove Nth Node From End of List
[LeetCode Link](https://leetcode.cn/problems/remove-nth-node-from-end-of-list/)


**Problem**  
Given the `head` of a linked list, remove the $n^{th}$ node from the end of the list and return its head.

**Example**

```text
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
```

**My Understanding**

```text

```

**Solution**

```python

```
**Note**

*   Time Complexity: $O()$
*   Space Complexity: $O()$

---
# 160. Intersection of Two Linked Lists
[LeetCode Link](https://leetcode.cn/problems/intersection-of-two-linked-lists/)


**Problem**  
Given the heads of two singly linked-lists `headA` and `headB`, return the node at which the two lists intersect. If the two linked lists have no intersection at all, return `null`.

For example, the following two linked lists begin to intersect at node `c1`:
*   List A: a1 -> a2 -> c1 -> c2
*   List B: b1 -> b2 -> b3 -> c1 -> c2

The test cases are generated such that there are no cycles anywhere in the entire linked structure.
**Note** that the linked lists must **retain their original structure** after the function returns.

**Example**

```text
Input: intersectVal = 8, listA = [4,1,8,4,5], listB = [5,6,1,8,4,5], skipA = 2, skipB = 3
Output: Intersected at '8'
Explanation: The intersected node's value is 8 (note that this must not be 0 if the two lists intersect).
From the head of A, it reads as [4,1,8,4,5]. From the head of B, it reads as [5,6,1,8,4,5]. There are 2 nodes before the intersected node in A; There are 3 nodes before the intersected node in B.
```

**My Understanding**

```text

```

**Solution**

```python


```
**Note**

*   Time Complexity: $O()$ 
*   Space Complexity: $O()$

---
# 142. Linked List Cycle II
[LeetCode Link](https://leetcode.cn/problems/linked-list-cycle-ii/)


**Problem**  
Given the `head` of a linked list, return *the node where the cycle begins*. If there is no cycle, return `null`.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to (0-indexed). It is `-1` if there is no cycle. **Note that `pos` is not passed as a parameter**.

**Do not modify** the linked list.

**Example**

```text
Input: head = [3,2,0,-4], pos = 1
Output: tail connects to node index 1
Explanation: There is a cycle in the linked list, where tail connects to the second node.
```

**My Understanding**

```text

```

**Solution**

```python


```
**Note**

*   Time Complexity: $O()$
*   Space Complexity: $O()$

---
# 707. Design Linked List
[LeetCode Link](https://leetcode.cn/problems/design-linked-list/)


**Problem**  
Design your implementation of the linked list. You can choose to use a singly or doubly linked list.
A node in a singly linked list should have two attributes: `val` and `next`. `val` is the value of the current node, and `next` is a pointer/reference to the next node.
If you want to use the doubly linked list, you will need one more attribute `prev` to indicate the previous node in the linked list. Assume all nodes in the linked list are **0-indexed**.

Implement the `MyLinkedList` class:

*   `MyLinkedList()` Initializes the `MyLinkedList` object.
*   `int get(int index)` Get the value of the `index`th node in the linked list. If the index is invalid, return `-1`.
*   `void addAtHead(int val)` Add a node of value `val` before the first element of the linked list. After the insertion, the new node will be the first node of the linked list.
*   `void addAtTail(int val)` Append a node of value `val` as the last element of the linked list.
*   `void addAtIndex(int index, int val)` Add a node of value `val` before the `index`th node in the linked list. If `index` equals the length of the linked list, the node will be appended to the end of the linked list. If `index` is greater than the length, the node **will not be inserted**.
*   `void deleteAtIndex(int index)` Delete the `index`th node in the linked list, if the index is valid.

**Example**

```text
Input
["MyLinkedList", "addAtHead", "addAtTail", "addAtIndex", "get", "deleteAtIndex", "get"]
[[], [1], [3], [1, 2], [1], [1], [1]]

Output
[null, null, null, null, 2, null, 3]

Explanation
MyLinkedList myLinkedList = new MyLinkedList();
myLinkedList.addAtHead(1);
myLinkedList.addAtTail(3);
myLinkedList.addAtIndex(1, 2);    // linked list becomes 1->2->3
myLinkedList.get(1);              // return 2
myLinkedList.deleteAtIndex(1);    // now the linked list is 1->3
myLinkedList.get(1);              // return 3
```

**My Understanding**

```text

```

**Solution**

```python

```
**Note**

*   Time Complexity: $O()$
*   Space Complexity: $O()$

---
