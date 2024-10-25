## **Treasure Hunt**

You are on a treasure hunt! You start at the coordinates `(0, 0)` on a 2D plane. You will follow a series of steps given in an integer array. Depending on the value of each step and its index in the array, you will move in specific directions.

### **Movement Rules:**
- For a positive integer `n`: 
  - If it’s at an even index, move **north** (increase y-coordinate by `n`).
  - If it’s at an odd index, move **east** (increase x-coordinate by `n`).
  
- For a negative integer `n`: 
  - If it’s at an even index, move **south** (decrease y-coordinate by `|n|`).
  - If it’s at an odd index, move **west** (decrease x-coordinate by `|n|`).

### **Constraints:**
- _1 ≤ len(steps) ≤ 1000_
- _-10^9 ≤ steps[i] ≤ 10^9_


### **Input Format:**
1. The first line will be the number of test cases `t`.
2. A list of integers `steps` where 
- 1 ≤ len(steps) ≤ 1000.
- -10^9 ≤ steps[i] ≤ 10^9.

This describes the valid range for the length of the steps array and the values inside it.
### **Output Format:**
- Output a string in the format `"x y"` representing the final coordinates of the treasure.



### **Sample Input:**
```
1
6
3 -2 4 -1 -5 2
```

### **Sample Output:**
```
-1 2
```

### **Explanation:**

**Movement Rules Breakdown**:
- **Starting Point**: You begin at the origin `(0, 0)`.
- **Step Interpretation**:
  - Positive Integers:  
    - At even indices (0, 2, 4,...): Move **north** (increase the y-coordinate).  
    - At odd indices (1, 3, 5,...): Move **east** (increase the x-coordinate).
  - Negative Integers:  
    - At even indices: Move **south** (decrease the y-coordinate).  
    - At odd indices: Move **west** (decrease the x-coordinate).



### **Efficient Code [O(n)]:**

```python
def treasure_hunt(steps):
    x, y = 0, 0

    for index, step in enumerate(steps):
        if index % 2 == 0:  # Even index
            y += step
        else:  # Odd index
            x += step

    return [x, y]

if __name__ == "__main__":
    t = int(input())
    for _ in range(t):
        n = int(input())
        steps = [int(i) for i in input().split()]
        print(" ".join(map(str, treasure_hunt(steps))))
```
