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
```text
给一串数字，要你找出最长的一段连续子数组，里面只能包含两种不同的数字。
Given a sequence of numbers, find the longest contiguous subarray that contains at most two distinct numbers.
```
**Approach (Sliding-Window)**
```text
1. Use two pointers `left` and `right` and a hashmap `count` to track fruit frequencies in the window.  
2. Expand `right`, adding `fruits[right]` to `count`.  
3. While the window contains more than 2 distinct fruits, shrink from the left:
   - Decrement `count[fruits[left]]`; if it becomes 0, remove that key.
   - `left += 1`  
4. Track `max_len = max(max_len, right - left + 1)` at each step.
```
**Solution Code**
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
- 如果水果种类是有规律连续出现（比如 [1,1,2,2,2,3]）：
  - 那么每次收缩窗口时，最左边那个水果的种类就是该被删除的。
  - 因为这种水果已经吃完了，后面没有它了。
- 但是如果数字是交杂出现的（比如 [1,2,1,2,1,3]）：
  - 随着窗口移动，最左边的水果只是当前窗口最左的，但不一定可以直接删除该种类。
  - 因为它可能在窗口其他地方还有出现（比如后面的1还在）。

所以必须要小心地：
- 先数量减一
- 只有数量真正减到0，才能删掉这个水果种类。
---
# 76. Minimum Window Substring (Sliding‐Window + Hash Map) （Hard）

**Problem**  
Given two strings `s` and `t`, return the minimum window in `s` which will contain all the characters in `t`. If there is no such window, return an empty string `""`.  

**My Understanding**  
```text
> 我们需要在 `s` 中找到一个最短的子串，这个子串必须“包含”字符串 `t` 中的所有字符（包括重复）。  
> 用滑动窗口加哈希表来记录当前窗口内字符频次，动态收缩和扩展窗口，直到窗口刚好覆盖 `t` 中所有字符，再尝试收缩寻找最短解。
```
**Example**  
```text
Input: s = "ADOBECODEBANC", t = "ABC"
Output: "BANC"
Explanation: "BANC" is the smallest window containing 'A', 'B', and 'C'.
```
**Approach (Sliding-Window)**

**Solution Code**

```python
class Solution:
    def minWindow(self, s: str, t: str) -> str:
        from collections import Counter
        need = Counter(t)  # 统计t中每个字母需要的次数
        window = {}  # 当前窗口中各字母的次数
        have, need_count = 0, len(need)
        res, res_len = [-1, -1], float("inf")
        left = 0
        for right in range(len(s)):
            c = s[right]
            window[c] = window.get(c, 0) + 1
            if c in need and window[c] == need[c]:
                have += 1
            while have == need_count:
                if (right - left + 1) < res_len: # 更新最小窗口
                    res = [left, right]
                    res_len = right - left + 1
                window[s[left]] -= 1 # 开始缩小窗口
                if s[left] in need and window[s[left]] < need[s[left]]:
                    have -= 1
                left += 1
        l, r = res
        return s[l:r+1] if res_len != float("inf") else ""
```
# 🍎 Python `collections` 常用工具速查表

| 工具 | 导入方式 | 用途 | 简单例子 |
|:---|:---|:---|:---|
| `defaultdict` | `from collections import defaultdict` | 字典不存在的 key 时，自动创建默认值（比如默认是0） | `d = defaultdict(int); d['a'] += 1` |
| `Counter` | `from collections import Counter` | 快速统计元素出现的次数（常用于字符串、数组） | `Counter('aabc') ➔ {'a':2, 'b':1, 'c':1}` |
| `deque` | `from collections import deque` | 双端队列，可以在队头或队尾快速插入和删除（比 list 高效） | `q = deque(); q.append(1); q.appendleft(2)` |
| `OrderedDict` | `from collections import OrderedDict` | 记住元素插入的顺序（Python 3.7之后普通dict也有顺序了，较少用） | `od = OrderedDict(); od['a']=1; od['b']=2` |
| `namedtuple` | `from collections import namedtuple` | 类似小型轻量级的类，用来创建简单的不可变对象 | `Point = namedtuple('Point', ['x', 'y']); p = Point(1, 2)` |

# 🧡 小小温柔版总结

- `defaultdict` 👉 **遇到新key也不会出错**，适合累加/减
- `Counter` 👉 **自动数数**，适合统计字符串、数组里的元素
- `deque` 👉 **双头快进快出**，适合 BFS、滑动窗口
- `OrderedDict` 👉 **记住插入顺序**（现在不常用）
- `namedtuple` 👉 **简单的数据类**，适合定义小对象（像Point、Student）

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
**Approach (Sliding-Window)**
```text
1.  
2. 
3. 
4.
```
**Solution Code**
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



