## **Help the Steve**

Steve is in a mystical land where he needs to travel through a grid of size `m x n`. He starts at the top-left corner `(1, 1)` and needs to reach the bottom-right corner `(m, n)`. Steve can only move right or down at any point in time. However, some cells in the grid are blocked by obstacles, meaning Steve cannot step on these cells. You are tasked with finding the number of unique paths Steve can take from the start to the destination, avoiding the obstacles.

### **Input Format:**
- The first line contains an integer `t` — the number of grids to be parsed.
- The second line contains two integers `m` and `n`, representing the dimensions of the grid.
- The third line contains an integer `k`, the number of obstacles in the grid.
- The next `k` lines contain two integers `x` and `y`, where each pair represents a cell that contains an obstacle. Steve cannot step on these cells.

### **Output Format:**
Output a single integer, the number of unique paths Steve can take to reach the bottom-right corner of the grid from the top-left corner. If no valid path exists, return `0`.

### **Constraints:**
- _1<= T <= 5_
- _2 ≤ N ≤ 10^5_
- _1 ≤ A[i] ≤ 10^9_


### **Sample Input:**
```
2
3 3
0 0 0
1 1 0
0 0 0
3 3
0 0 0
1 1 0
1 1 1
```

### **Sample Output:**
```
1
0
```

### **Solution:**

#### **Brute Force Approach (O(2^(M+N)))**:
```python
def unique_paths_brute_force(grid):
    m, n = len(grid), len(grid[0])
    
    def dfs(x, y):
        if x >= m or y >= n or grid[x][y] == 1:
            return 0
        if x == m - 1 and y == n - 1:
            return 1
        return dfs(x + 1, y) + dfs(x, y + 1)
    
    return dfs(0, 0)
```

#### **Efficient Approach (O(M*N)):**
```python
def unique_paths_brute_force(test_cases):
    results = []
    for _ in range(test_cases):
        m, n = map(int, input().split())
        
        grid = []
        for _ in range(m):
            grid.append(list(map(int, input().split())))

        def dfs(x, y):
            if x >= m or y >= n or grid[x][y] == 1:
                return 0
            if x == m - 1 and y == n - 1:
                return 1
            return dfs(x + 1, y) + dfs(x, y + 1)

        results.append(dfs(0, 0))
    
    for result in results:
        print(result)

test_cases = int(input())
unique_paths_brute_force(test_cases)

```

