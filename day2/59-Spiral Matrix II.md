# 59. Spiral Matrix II
**Problem**  
Given a positive integer `n`, generate an `n × n` matrix filled with numbers from `1` to `n²` in spiral order (clockwise, from outer layer to inner layer).

**Example**  
<img width="339" alt="image" src="https://github.com/user-attachments/assets/35368963-9d7b-4d59-b107-12d87812b171" />

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
            for i in range(left, right + 1):# 左闭右开区间,循环从left 到right
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

# 54. Spiral Matrix II
**Problem**  
Given an `m x n` matrix, return all elements of the matrix in spiral order (clockwise, from outer layer to inner layer).

**Example**  
<img width="383" alt="image" src="https://github.com/user-attachments/assets/a7b49244-c5a9-4ac4-833d-7c5726a9274a" />

**My Understanding**  
和上一题类似


**Solution Code**
```python
class Solution:
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        if not matrix or not matrix[0]:
            return []
        m = len(matrix)
        n = len(matrix[0])
        rematrix = [0]*(n*m)
        up, down, left, right = 0, m-1, 0, n-1
        num = 0
        while True:
            for i in range(left,right+1):
                rematrix[num] = matrix[up][i]
                num+=1
            up+=1
            if up > down:
                break
            for i in range(up, down+1):
                rematrix[num] = matrix[i][right]
                num+=1
            right-=1
            if right<left:
                break
            for i in range(right,left-1,-1):
                rematrix[num] = matrix[down][i]
                num+=1
            down-=1
            if down < up:
                break
            for i in range(down,up-1,-1):
                rematrix[num] = matrix[i][left]
                num+=1
            left+=1
            if left>right:
                break
        return rematrix
```
---



# Range Sum (Prefix‐Sum) 区间和
**Problem**  
Given an integer array `Array`, compute the sum of its elements over each specified interval.

### Input

1. The first line contains an integer `n`, the length of `Array`.  
2. The next `n` lines each contain one integer, the elements of `Array` in order.  
3. Each subsequent line contains two integers `a` and `b` (with `b ≥ a`), representing a query for the sum of the subarray from index `a` to index `b`. Queries continue until end of file.

### Output

For each query `a b`, print a single integer on its own line—the value of  Array[a] + Array[a+1] + … + Array[b]

**Example**  
```text
Input:
5
1
2
3
4
5
1 3
0 4

Output:
9    # 2 + 3 + 4
15   # 1 + 2 + 3 + 4 + 5 
```
**My Understanding**  
```text

```
**Approach: Prefix Sum**
```text
To answer multiple range‐sum queries on an array `vec`, we first build a **prefix sum** array `p` of the same length:
p[i] = vec[0] + vec[1] + ... + vec[i]
The sum of any subarray vec[l..r] (0 ≤ l ≤ r < n) can be computed in O(1) time as:
sum(vec[l..r]) = v[l] + ... + v[r] = p[r]-p[l-1]
<img width="720" alt="image" src="https://github.com/user-attachments/assets/86b7503e-bba5-46df-b510-cd0ab7645f9f" />

```

**Solution Code**
```python
import sys

def main():
    data = sys.stdin.read().strip().split()
    if not data:
        return

    # 读取数组长度和元素
    n = int(data[0])
    arr = list(map(int, data[1:1+n]))

    # 构建前缀和数组，p[i] = sum(arr[0..i-1])
    p = [0] * (n + 1)
    for i in range(n):
        p[i+1] = p[i] + arr[i]

    # 处理每个查询 [a, b]
    idx = 1 + n
    out = []
    while idx + 1 < len(data):
        a = int(data[idx])
        b = int(data[idx+1])
        idx += 2
        out.append(str(p[b+1] - p[a])) # 区间和 = p[b+1] - p[a]

    sys.stdout.write("\n".join(out))

if __name__ == "__main__":
    main()

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





