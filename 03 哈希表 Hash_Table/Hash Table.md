# HashMap
**当我们遇到了要快速判断一个元素是否出现在集合里的时候，就要考虑哈希法**

Whenever you need to perform fast membership checks—i.e., to quickly determine if an element exists in a collection—you should consider using a hash-based approach (e.g., a hash table).
<img width="754" alt="image" src="https://github.com/user-attachments/assets/35079197-c9b7-486d-99de-537f831eb845" />
<img width="754" alt="image" src="https://github.com/user-attachments/assets/2f7fa5fd-d23b-4575-92b0-720d42e590a0" />
<img width="756" alt="image" src="https://github.com/user-attachments/assets/885cb451-0521-4af4-b519-78f8e332f1f4" />
<img width="756" alt="image" src="https://github.com/user-attachments/assets/01a503de-ef1d-49ec-812a-818090938457" />


When your raw hashCode exceeds the number of buckets (tableSize), you map it back into the valid range by taking the modulus:
- **`index = hashCode % tableSize`**  
  - 直接取模，**如果** `hashCode` 为负数，那么 `index` 也可能是负的（落在 `[-tableSize+1 .. tableSize-1]`）。  
  - 在某些语言中（如 Java），负 `%` 结果会导致数组下标越界或运行时错误。

- **`bucketIndex = (hashCode % tableSize + tableSize) % tableSize`**  
  - 先对 `hashCode` 取模，再加上 `tableSize` 保证结果非负，最后再取一次模：  
    ```text
    bucketIndex = (rawIndex + tableSize) % tableSize
    ```  
  - 无论 `hashCode` 原始是正是负，`bucketIndex` 最终都会落在 `[0 .. tableSize-1]`，安全可用作数组下标。

## Collision Resolution Strategies
When two keys hash to the same `bucketIndex`, you must resolve the collision. Common methods include:

1. **Separate Chaining**  
   - Each bucket holds a linked list (or dynamic array) of entries.  
   - On insert, append the new `(key, value)` to the list at `bucketIndex`.  
   - On lookup/delete, scan the list and compare keys.
   - <img width="766" alt="image" src="https://github.com/user-attachments/assets/8a12884e-f8a1-4f40-aa43-f01e36adccbb" />


2. **Open Addressing**  
   Store all entries directly in the hash table array, probing for the next free slot:

   - **Linear Probing**  
     ```text
     idx = (bucketIndex + i) % tableSize
     ```
     Increment `i = 0,1,2…` until you find an empty slot or the target key.
      <img width="732" alt="image" src="https://github.com/user-attachments/assets/e2fa3eca-b68f-49dd-9bdf-7cef10cb875e" />
      <img width="381" alt="image" src="https://github.com/user-attachments/assets/bcade7ea-2266-459f-bf68-f5ddea51c0fd" />


   - **Quadratic Probing**  
     ```text
     idx = (bucketIndex + i*i) % tableSize
     ```
     Reduces clustering compared to linear.

   - **Double Hashing**  
     ```text
     idx = (bucketIndex + i * step(hash2(key))) % tableSize
     ```
     Uses a second hash function `hash2` to compute the probe step.

3. **Resizing & Rehashing**  
   - If load factor `(numEntries/tableSize)` exceeds a threshold (e.g. 0.7), allocate a larger table (often double size).  
   - Recompute `bucketIndex` for every existing key and insert into the new table.
     
## Common Hash‐Based Data Structures

When we want to apply hashing to solve problems, we typically choose one of the following three data structures:

- **Array**  
- **Set**  
- **Map**  

> By choosing the right strategy and keeping the load factor low, you can maintain **O(1)** average‐case performance for insert, lookup, and delete—even when collisions occur.  

**牺牲了空间换取了时间**


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

```
---
