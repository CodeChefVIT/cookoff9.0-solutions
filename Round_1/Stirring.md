## **Stirring**

Chef is renowned for his world-famous stews, and the secret to their rich, unforgettable flavour lies in the way they are stirred. Each stew recipe comes with its own unique stirring pattern, involving both clockwise and anticlockwise stirs.  
Every recipe specifies three important values:
- `n`: the maximum number of stirs that can be performed in one direction at one time (clockwise or anticlockwise).
- `c`: the required and maximum number of clockwise stirs.
- `a`: the required and maximum number of anticlockwise stirs.

The chef always starts by stirring in the clockwise direction. After he stirs clockwise, he switches to anticlockwise stirs, and this back-and-forth pattern continues. Once he finishes a series of anticlockwise stirs, he must return to clockwise stirs, and vice versa. However, there’s a twist. If the chef completes all the clockwise stirs before the anticlockwise stirs are done (or vice versa), he can't stir in the same direction anymore. Instead, he dips the stirrer once into the stew for each extra move that can no longer be completed in the same direction.

### Possible moves:
- Clockwise Stir
- Anticlockwise Stir
- Dipping

Your task is to help the chef determine the minimum number of moves required to successfully stir the stew, including the stirs (both clockwise and anticlockwise) and any necessary dips.

**Note**: Up to `n` stirs in any direction will count as one move.

### **Input Format**:
- The first line will contain a number `t`.  
- The next `t` lines will each have 3 numbers: `n`, `c`, `a`.  
- `n`: the maximum number of stirs allowed in any direction before switching.  
- `c`: the number of clockwise stirs required.  
- `a`: the number of anticlockwise stirs required.

### **Output Format**:
Return the minimum number of moves (clockwise stirs, anticlockwise stirs, and dips) needed to brew the stew according to the recipe's rules for each of the `t` rows.


### **Sample Input**
```
2
3 9 11
8 0 10
```

### **Sample Output**
```
8
4
```

### **Solution O(1):**

```python
t = int(input())
for i in range(t):
    n, c ,a = input().split()
    n, c ,a = int(n), int(c), int(a)
    moves_c = int((c + n -1)/n)
    moves_a = int((a + n -1)/n)
    total_moves = 0

    if moves_c > moves_a:
        total_moves = 2*moves_c -1
    else:
        total_moves = 2*moves_a    

    print(total_moves)
```
