# 27. Remove Element
[LeetCode Link](https://leetcode.cn/problems/remove-element/)

**Problem**  
Given an integer array `nums` and an integer `val`, remove all occurrences of `val` in `nums` **in-place**. The order of the elements may be changed. Then return *the number of elements in* `nums` *which are not equal to* `val`.

Consider the number of elements in `nums` which are not equal to `val` be `k`, to get accepted, you need to do the following things:

1.  Change the array `nums` such that the first `k` elements of `nums` contain the elements which are not equal to `val`. The remaining elements of `nums` are not important as well as the size of `nums`.
2.  Return `k`.

**Example**

```text
Input: nums = [3,2,2,3], val = 3
Output: 2, nums = [2,2,_,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 2.
It does not matter what you leave beyond the returned k (hence they are underscores).

Input: nums = [0,1,2,2,3,0,4,2], val = 2
Output: 5, nums = [0,1,4,0,3,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums containing 0, 0, 1, 3, and 4.
Note that the five elements can be returned in any order.
It does not matter what you leave beyond the returned k (hence they are underscores).
```

**Constraints:**
*   0 <= nums.length <= 100
*   0 <= nums[i] <= 50
*   0 <= val <= 100

## My Understanding

### Note
```text

```

### Solution
```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:

        slow = 0  
        for _,num in enumerate(nums):
            if num != val:
                nums[slow] = num
                slow+=1
        
        return slow
```
**Complexity**

*   Time Complexity: 
*   Space Complexity: 

---
# 26. Remove Duplicates from Sorted Array
[LeetCode Link](https://leetcode.cn/problems/remove-duplicates-from-sorted-array/)

**Problem**  
Given an integer array `nums` sorted in **non-decreasing order**, remove the duplicates **in-place** such that each unique element appears only once. The **relative order** of the elements should be kept the same. Then return *the number of unique elements in* `nums`.

Consider the number of unique elements of `nums` to be `k`, to get accepted, you need to do the following things:

1.  Change the array `nums` such that the first `k` elements of `nums` contain the unique elements in the order they were present in `nums` initially. The remaining elements of `nums` are not important as well as the size of `nums`.
2.  Return `k`.

**Custom Judge:**

The judge will test your solution with the following code:

```java
int[] nums = [...]; // Input array
int[] expectedNums = [...]; // The expected answer with correct length

int k = removeDuplicates(nums); // Calls your implementation

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}
```
If all assertions pass, then your solution will be accepted.

**Example**

```text
Input: nums = [1,1,2]
Output: 2, nums = [1,2,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).

Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).
```

**Constraints:**
*   `1 <= nums.length <= 3 * 10^4`
*   `-100 <= nums[i] <= 100`
*   `nums` is sorted in **non-decreasing** order.

## My Understanding

### Note
```text
1. 不能用切片for i,num in enumerate(nums[1::]): Python 实际上复制了一份新的列表
```

### Solution
```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        if len(nums) == 1:
            return 1
        slow = 1
        for fast in range(1,len(nums)):
            if nums[fast] != nums[fast-1]:
                nums[slow] = nums[fast]
                slow+=1
        return slow
```
**Complexity**

*   Time Complexity: 
*   Space Complexity: 

---

