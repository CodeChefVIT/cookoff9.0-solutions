## **Chef and Chefina's Array Challenge**

Chef and Chefina are computer science students. Chefina gives Chef an array of numbers and a series of commands to perform on the array. Chef's goal is to determine the largest sum of any contiguous sequence of numbers in the array after applying all commands. 

Chefina provides an array **A** with **N** integers and a string of operations with **O** commands (not separated). The commands are:

- `'R'`: Reverse the array.
- `'S'`: Shift the array elements to the right by one position (cyclic shift).

Chef must apply each command in the order given by **ops** and then find the largest sum of any contiguous subarray that can be formed after the commands are applied.


### **Input format**:
1. The first line contains an integer **T**, the number of test cases.
2. For each test case:
   - A line with an integer **N**, the number of elements in the array **A**.
   - A line with **N** space-separated integers representing the array **A**.
   - A line with an integer **O**, the number of commands.
   - A line with a string of length **O** consisting of the commands ('R' and 'S').


### **Output format**:
For each test case, output a single integer: the largest sum of any contiguous sequence of numbers in the array after all commands have been applied.


### **Constraints**:
- 1 ≤ T ≤ 10
- 1 ≤ N ≤ 10^5
- 1 ≤ O ≤ 10^5
- -10^9 <= A[i] <= 10^9.


### **Sample Input**:
```
2
5
1 -2 3 4 -5
3
RSR
4
2 -1 3 -2
2
SR
```

### **Sample Output**:
```
7
4
```


### **Explanation**:
Apply the operations in the given sequence to the array, and use Kadane’s algorithm to find the maximum sum of any contiguous subarray.


### **Efficient Code (O(n)):**

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int findMaxSubarraySum(const vector<int> &arr) {
    int max_ending_here = arr[0];
    int max_so_far = arr[0];
    for (size_t i = 1; i < arr.size(); ++i) {
        max_ending_here = max(arr[i], max_ending_here + arr[i]);
        max_so_far = max(max_so_far, max_ending_here);
    }
    return max_so_far;
}

void shiftRight(vector<int> &arr) {
    if (!arr.empty()) {
        int last = arr.back();
        arr.pop_back();
        arr.insert(arr.begin(), last);
    }
}

int max_contiguous_sum_after_operations(int N, vector<int> &A, int O, const string &ops) {
    for (int i = 0; i < O; ++i) {
        if (ops[i] == 'R') {
            reverse(A.begin(), A.end());
        } else if (ops[i] == 'S') {
            shiftRight(A);
        }
    }
    return findMaxSubarraySum(A);
}

int main() {
    int T;
    cin >> T;
    vector<int> results;
    while (T--) {
        int N, O;
        cin >> N;
        vector<int> A(N);
        for (int i = 0; i < N; ++i) {
            cin >> A[i];
        }
        cin >> O;
        string ops;
        cin >> ops;
        int result = max_contiguous_sum_after_operations(N, A, O, ops);
        results.push_back(result);
    }
    for (int i = 0; i < results.size(); i++) {
        cout << results[i] << endl;
    }
    return 0;
}
```