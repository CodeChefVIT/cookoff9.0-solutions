## **Potion Crafter**

In the world of Minecraft, there was a wise old potion maker who lived on the outskirts of a small village. She was famous for crafting powerful potions that adventurers sought after. One day, she decided to restock her inventory from the nearby Potion Ingredient Shop.
In her inventory, she could only carry **9** different types of ingredients at once, and each ingredient had a specific cost and value (the value represents the power or usefulness of the ingredient in brewing stronger potions). Also, the potion maker can carry only up to a certain weight `W` of ingredients. However, her goal was to minimise the total cost while ensuring she collects ingredients that have at least a combined value of `V` (the minimum required value to brew her potions).
Your task is to help the old potion maker fill her inventory by selecting the most suitable ingredients, so she spends as little gold as possible but still meets the minimum value requirement.


### **Constraints:**
- _1 ≤ t ≤ 4 (Number of test cases)_
- _1 ≤ W ≤ 1000 (Maximum weight of the bag)_
- _1 ≤ N ≤ 100 (Number of ingredients)_
- _1 ≤ weight of each ingredient ≤ W_
- _1 ≤ value of each ingredient ≤ 1000_


### **Input Format:**
- The first line is an integer `t` for the no of bags.
- The Second line contains two integers `W` (the maximum weight her bag can carry) and `N` (the number of ingredients in the market).
- The next `N` lines each contain two integers weight and value for each ingredient.


### **Output Format:**

Maximum total value the old woman can obtain without exceeding the weight limit `W` for each bag.

### **Sample Input:**
```
2
100 5
50 40
20 30
30 50
40 60
10 20
50 3
20 60
30 100
10 120

```

### **Sample Output:**
```
160 
220

```

### **Explanation:**

Given the maximum weight her bag can carry and the list of ingredients available in the market, help the old woman choose the ingredients that maximise the total magical value without exceeding the weight limit

### **Efficient Code [O(n*W)]:**

```python
def knapsack(W, ingredients):
    N = len(ingredients)
    dp = [[0 for _ in range(W + 1)] for _ in range(N + 1)]
    
    for i in range(1, N + 1):
        for w in range(W + 1):
            weight, value = ingredients[i - 1]
            if weight > w:
                dp[i][w] = dp[i - 1][w]
            else:
                dp[i][w] = max(dp[i - 1][w], dp[i - 1][w - weight] + value)
    
    return dp[N][W]

def main():
    t = int(input())
    results = []

    for _ in range(t):
        W, N = map(int, input().split())
        ingredients = [tuple(map(int, input().split())) for _ in range(N)]
        result = knapsack(W, ingredients)
        results.append(result)

    for res in results:
        print(res)

if __name__ == "__main__":
    main()

```
