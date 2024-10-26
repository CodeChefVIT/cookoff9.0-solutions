## **Restaurant**

Chef recently opened a restaurant and wants a catchy advertisement for it. Chef's restaurant is a unique one where you give the restaurant a dish type to cook, and they will provide the dish with a unique set of flavors each time for each customer. 

For each dish manual, Chef has:
- A set number of ingredients that Chef is required to use in the dish (`x`)
- Total ingredients available for the dish (including flavoring) (`n`)
- Number of ingredients that are essential for the dish and cannot be replaced (non-flavoring ingredients) (`z`)

Chef has a total of `T` types of dishes in the restaurant. Chef wants to advertise the total number of unique dishes the restaurant can provide. Chef doesn't want to count recipes that are impossible to implement.

**Hint:** To select `n` from `r` items:  
C(n, r) = n! / (r!(n-r)!)

### **Input Format**:
1. An integer representing the number of test cases `T`
2. For each test case, an integer representing the number of recipes
3. For each recipe, a series of numbers:\
    `x1 n1 z1`\
    `x2 n2 z2`\
    `.....`\
    `xT nT zT`

**Constraints:**
- _Z < X < N_

### **Output Format**:
Output an integer representing the total number of unique dishes for each test case.:

### **Sample Input**:
```
1
2
3 5 1
4 6 2
```
### **Sample Output**:
```
12
```


### **Solution**

```cpp
#include <iostream>
#include <vector>
using namespace std;

// Function to calculate factorial
long long factorial(int n) {
    if (n == 0 || n == 1) return 1;
    long long fact = 1;
    for (int i = 2; i <= n; ++i) {
        fact *= i;
    }
    return fact;
}

// Function to calculate combinations C(n, r)
long long combination(int n, int r) {
    if (r > n) return 0;  
    return factorial(n) / (factorial(r) * factorial(n - r));
}

int main() {
    int T;
    cin >> T; // Number of test cases

    vector<long long> results; // Vector to store results for each test case

    for (int t = 0; t < T; ++t) {
        long long total_dishes = 0;
        
        int num_recipes;
        cin >> num_recipes; // Number of recipes for this test case

        for (int i = 0; i < num_recipes; ++i) {
            int x, n, z;
            cin >> x >> n >> z;

            // Calculate the number of ways to choose (x - z) ingredients from (n - z) available ones
            int ingredients_to_choose = x - z;
            int available_ingredients = n - z;

            if (available_ingredients >= ingredients_to_choose) {
                total_dishes += combination(available_ingredients, ingredients_to_choose);
            }
        }

        results.push_back(total_dishes); // Store the result for this test case
    }

    // Output all results together
    for (long long result : results) {
        cout << result << endl;
    }

    return 0;
}

```
