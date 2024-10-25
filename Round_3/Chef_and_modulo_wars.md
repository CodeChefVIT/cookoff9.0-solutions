## **Kitchen**
Chef and Chefina are playing a game with two integers, `a` and `b`. Chefina wants to know how many integers from `1` to `n` satisfy the condition: `i % a ≠ i % b`, Where `i % a` is the remainder when `i` is divided by `a`, and `i % b` is the remainder when `i` is divided by `b`; and `i` is any number from `1` to `n` (inclusive).

Chefina finds this game interesting and wants your help in calculating the answer for any given `a`, `b`, and `n`. 
Your task is to calculate how many integers `i` (where `1 ≤ i ≤ n`) satisfy `i % a ≠ i % b`


### **Constraints:**
- _1 ≤ T ≤ 100_
- _1 ≤ a, b, n ≤ 10^10_

### **Input Format:**
- The first line contains an integer `T`, the number of test cases.
- Each test case consists of three integers `a`, `b`, and `n`.

### **Output Format:**
- For each test case, output the number of integers from `1` to `n` where `i % a ≠ i % b`.

The program should run efficiently for the maximum constraint `T = 100`. Note: The maximum treasure can be collected from multiple paths; however, only the path that yields the highest total treasure should be considered for the output.


### **Sample Input:**
```
2 
2 3 6
3 5 10
```

### **Sample Output:**
```
4
8
```

### **Explanation:**

Calculate lcm to determine the cycle after which the remainders will be repeated, Calculate the valid numbers in a cycle and multiply to number of cycles existing, add the remaining valid numbers in incomplete cycle

### **Solution [O(T×(lcm(a,b)+log(min(a,b)))]:**

```cpp
#include <iostream>
#include <vector>
using namespace std;

long long gcd(long long x, long long y) {
    while (y) {
        long long temp = y;
        y = x % y;
        x = temp;
    }
    return x;
}

long long lcm(long long x, long long y) {
    return (x / gcd(x, y)) * y;
}

long long count_non_equal_remainders(long long a, long long b, long long n) {
    long long lcm_ab = lcm(a, b);
    long long count_in_lcm = 0;

    for (long long i = 1; i <= lcm_ab; ++i) {
        if (i % a != i % b) {
            count_in_lcm++;
        }
    }

    long long complete_cycles = n / lcm_ab;

    long long remaining = n % lcm_ab;
    long long count_in_remaining = 0;

    for (long long i = 1; i <= remaining; ++i) {
        if (i % a != i % b) {
            count_in_remaining++;
        }
    }

    return (complete_cycles * count_in_lcm) + count_in_remaining;
}

int main() {
    int T;
    cin >> T;
    vector<long long> results;

    for (int i = 0; i < T; ++i) {
        long long a, b, n;
        cin >> a >> b >> n; 
        results.push_back(count_non_equal_remainders(a, b, n));
    }

    for (int i = 0; i < results.size(); i++) {
        cout << results[i] << endl;
    }

    return 0;
}

```
