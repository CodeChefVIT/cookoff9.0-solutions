## **Help chef to find the ingredients**

Chef is experimenting with new recipes, and he needs to find a specific ingredient among a collection of magical ingredients. The ingredients are stored in a sorted list based on their magical power. Chef wants to efficiently determine if a particular ingredient is available in the list and, if so, its position.
Task: Given a list of magical ingredients (sorted in ascending order of their magical power) and a target ingredient, implement a program to determine if the target ingredient is present. If it is, return its index; otherwise, return -1.

### **Constraints:**
- 1 ≤ T ≤ 10
- 1 ≤ T ≤ 10
- 1 ≤ T ≤ 10


### **Input Format:**
1. The first line contains an integer **T** (1 ≤ T ≤ 10), the number of test cases.
2. For each test case:
   - The first line contains an integer **N** (1 ≤ N ≤ 10^9), the number of magical ingredients.
   - The second line contains **N** space-separated integers representing the magical power of the ingredients (sorted in ascending order).
   - The third line contains an integer **M** (1 ≤ M ≤ 10^9), the magical power of the ingredient Chef is searching for.


### **Output Format:**
For each test case, output a single line containing the index of the magical ingredient (0-based) if found; otherwise, output -1.


### **Sample Input:**
```
2
5
1 3 5 7 9
5
4
10 20 30 40
25
```

### **Sample Output:**
```
2
-1
```
### **Python Code [O(log(n)]**:

```python
def find_ingredient(arr, target):
    low, high = 0, len(arr) - 1

    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1

    return -1


def process_test_cases():
    t = int(input())

    for _ in range(t):
        n = int(input())
        arr = list(map(int, input().split()))
        target = int(input())

        result = find_ingredient(arr, target)
        print(result)


process_test_cases()

```
