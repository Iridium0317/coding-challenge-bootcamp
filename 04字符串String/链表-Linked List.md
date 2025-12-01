# 链表-Linked List
<img width="753" alt="image" src="https://github.com/user-attachments/assets/43873263-c476-429f-9a9f-e48c0b53e649" />
<img width="747" alt="image" src="https://github.com/user-attachments/assets/fe249c33-eb22-4159-9cc1-f41efe578198" />
<img width="501" alt="image" src="https://github.com/user-attachments/assets/d0ec6bde-e7f3-4ce3-b55b-cc45b577a7e9" />
<img width="733" alt="image" src="https://github.com/user-attachments/assets/458cbabd-acee-4378-8056-73a3c3ac07e2" />

手写链表
```python
class ListNode:
    def __init__(self, val, next=None):
        self.val = val
        self.next = next
```
<img width="769" alt="image" src="https://github.com/user-attachments/assets/36719523-7f00-4ac2-b1e2-77966b2bfcc0" />
<img width="768" alt="image" src="https://github.com/user-attachments/assets/d94b35ec-c4c3-4bb2-beec-13e355666559" />
<img width="760" alt="image" src="https://github.com/user-attachments/assets/bb79405e-3b56-4ae3-9cfe-01a15874996b" />

# 203. Remove Linked List Elements
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
**Approach (Sliding-Window)**
```text
1.  
2. 
3. 
4.
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
---
# 59. Spiral Matrix II

**Problem**  

**Example**  
```text

```

**My Understanding**  
```text

```

**Approach (Sliding-Window)**
```text
1.  
2. 
3. 
4.
```

**Solution Code**
```python

```
---


