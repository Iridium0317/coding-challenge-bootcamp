# coding-challenge-bootcamp
A collection of LeetCode and algorithm solutions with insights for U.S. tech interviews.

## day2 数组 part02

### 209. 长度最小的子数组

**Problem**  
给定一个含有 n 个正整数的数组 `nums` 和一个正整数 `target`，找出该数组中满足其和 ≥ `target` 的长度最小的连续子数组，并返回它的长度。如果不存在，返回 0。

**Solution**  
```python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        left = 0
        curr_sum = 0
        ans = float('inf')
        for right, x in enumerate(nums):
            curr_sum += x
            while curr_sum >= target:
                ans = min(ans, right - left + 1)
                curr_sum -= nums[left]
                left += 1
        return ans if ans != float('inf') else 0
