# 209. Minimum Size Subarray Sum（sliding‐window）

**Problem**  
Given an array of positive integers `nums` and a positive integer `target`, return the minimal length of a contiguous subarray of which the sum is at least `target`. If there is no such subarray, return 0.

**Example**  
```text
Input: target = 7, nums = [2,3,1,2,4,3]
Output: 2
Explanation: The subarray [4,3] has the minimal length under the problem constraint.
```
**Solution Code**
```python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        l = len(nums)
        left = 0
        right = 0
        min_len = float('inf') # 无穷大
        cur_sum = 0 #当前的累加值
        
        while right < l:
            cur_sum += nums[right]
            
            while cur_sum >= target: # 当前累加值大于目标值
                min_len = min(min_len, right - left + 1) #right - left + 1 窗口长度
                cur_sum -= nums[left]
                left += 1
            
            right += 1
        
        return min_len if min_len != float('inf') else 0
```

---
# 904. Fruit Into Baskets（Medium）

**Problem**  
You have an integer array `fruits` where `fruits[i]` is the type of fruit on the *i*-th tree.  
You want to pick as much fruit as possible with **two baskets**.  
Starting at any tree, you must pick one fruit per tree moving to the right until you reach a tree whose fruit cannot fit in your baskets.  
Return the maximum number of fruits you can pick.

**Example**  
```text
Input: fruits = [1,2,1]
Output: 3
Explanation: You can pick [1,2,1].
```
**My Understanding**
给一串数字，要你找出最长的一段连续子数组，里面只能包含两种不同的数字。
Given a sequence of numbers, find the longest contiguous subarray that contains at most two distinct numbers.
## Approach (Sliding-Window)
1. Use two pointers `left` and `right` and a hashmap `count` to track fruit frequencies in the window.  
2. Expand `right`, adding `fruits[right]` to `count`.  
3. While the window contains more than 2 distinct fruits, shrink from the left:
   - Decrement `count[fruits[left]]`; if it becomes 0, remove that key.
   - `left += 1`  
4. Track `max_len = max(max_len, right - left + 1)` at each step.
## Solution Code

```python
class Solution:
    def totalFruit(self, fruits: List[int]) -> int:
        from collections import defaultdict

        basket = defaultdict(int)  # 创建一个哈希表（字典），默认值是 0
        left = 0
        max_fruits = 0

        for right in range(len(fruits)):
            basket[fruits[right]] += 1  # 把 右边的水果种类fruits[right] 放进篮子里

 # 不断把最左边的水果数量减掉，直到篮子里只剩下 2 种水果。
            while len(basket) > 2:  # 如果篮子里超过2种水果
                basket[fruits[left]] -= 1  # 把最左边的水果数量减1
                if basket[fruits[left]] == 0:
                    del basket[fruits[left]]  # 如果这个水果数量是0，完全移除
                left += 1  # 收缩左边界
           
            max_fruits = max(max_fruits, right - left + 1)  # 更新最大水果数

        return max_fruits
```
如果水果种类是有规律连续出现（比如 [1,1,2,2,2,3]），

那么每次收缩窗口时，最左边那个水果的种类就是该被删掉的。

因为这种水果已经吃完了，后面没有它了。

但是如果数字是交杂出现的（比如 [1,2,1,2,1,3]），

随着窗口移动，最左边的水果只是当前窗口最左的，但不是一定可以直接删种类。

因为它可能在窗口其他地方还有出现（比如后面的1还在）。

所以必须要小心地：

- 先数量减一
- 只有数量真正减到0，才能删掉这个水果种类。

<img width="674" alt="image" src="https://github.com/user-attachments/assets/a5a88fc5-5afd-4b66-9125-39a5fd601ecc" />

---

# 674. Longest Continuous Increasing Subsequence (Sliding‐Window)

**Problem**  
Given an integer array `nums`, return the length of the longest continuous strictly increasing subsequence.

**Example**  
```text
Input: nums = [1,3,5,4,7]
Output: 3
Explanation: The longest continuous increasing subsequence is [1,3,5], so its length is 3.
```
## Approach (Sliding-Window)
1.  
2. 
3. 
4.

## Solution Code
```python
def findLengthOfLCIS(self, nums: List[int]) -> int:
        left = 0
        right = 0
        sum = 1
        l = len(nums)
        while right <l-1:
            if nums[right] < nums[right+1]:
                right+=1
                sum = max(sum, right - left + 1)
            else:
                right+=1
                left = right
        return sum
```
---



