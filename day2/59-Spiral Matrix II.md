# 59. Spiral Matrix II
**Problem**  
Given a positive integer `n`, generate an `n × n` matrix filled with numbers from `1` to `n²` in spiral order (clockwise, from outer layer to inner layer).

**Example**  
```text
<img width="339" alt="image" src="https://github.com/user-attachments/assets/35368963-9d7b-4d59-b107-12d87812b171" />
```
**My Understanding**  
```text

```
**Approach**
```text
1.  
2. 
3. 
4.
```
**Solution Code**
```python
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        if n <= 0:
            return []
        up, down, left, right = 0, n-1, 0, n-1
        num = 1
        matrix = [[0]*n for _ in range(n)]  # 初始化 n x n 矩阵
        while True: 
            for i in range(left, right + 1):# 左闭右开区间
                matrix[up][i] = num
                num += 1
            up += 1
            if up > down:
                break

            for i in range(up, down + 1):
                matrix[i][right] = num
                num += 1
            right -= 1
            if right < left:
                break

            for i in range(right, left - 1, -1):
                matrix[down][i] = num
                num += 1
            down -= 1
            if down < up:
                break

            for i in range(down, up - 1, -1):
                matrix[i][left] = num
                num += 1
            left += 1
            if left > right:
                break
        return matrix
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





