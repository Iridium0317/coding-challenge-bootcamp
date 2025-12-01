# 704. 二分查找 – Binary Search

**Problem**  
给定一个排序好的整数数组 …

**Solution**  
二分查找，时间复杂度 O(log n)…

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        lo, hi = 0, len(nums)-1
        while lo <= hi:
            mid = (lo+hi)//2
            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                lo = mid+1
            else:
                hi = mid-1
        return -1
