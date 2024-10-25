## **Anagram Grouping**

You are given a list of words. Your task is to group the words that are **anagrams** of each other. An anagram is a word formed by rearranging the letters of another word. For example, `"listen"` and `"silent"` are anagrams.


### **Constraints:**
- _1 <= T <= 5_
- _1 <= K <= 50 (Where K is number of words per test case)_


### **Input Format:**
- The first line contains the number of test cases `T`.
- For next `T` lines: a list of strings, each consisting of lowercase alphabetic characters, separated by spaces


### **Output Format:**
- For each test case, print the sizes of the anagram groups sorted in **descending order** by the number of words in each group

### **Sample Input:**
```
2
eat tea tan ate nat bat
listen silent enlist google goolge

```

### **Sample Output:**
```
3 2 1
3 2

```

### **Explanation:**

- In the first test case, the words are grouped into the following anagrams:

  `['eat', 'tea', 'ate']` (3 words) \
  `['tan', 'nat']` (2 words) \
  `['bat']` (1 word) \
   _The sizes of the anagram groups are 3, 2, and 1, printed in descending order._

- In the second test case:

  `['listen', 'silent', 'enlist']` (3 words) \
  `['google', 'goolge']` (2 words) \
   _The sizes of the anagram groups are 3 and 2, printed in descending order._




### **Efficient Code [O(n^KlogK)]:**

```python
from collections import defaultdict

def group_and_sort_anagrams(words):
    anagrams = defaultdict(list)

    for word in words:
        sorted_word = ''.join(sorted(word))
        anagrams[sorted_word].append(word)

    grouped_anagrams = list(anagrams.values())

    group_sizes = sorted([len(group) for group in grouped_anagrams], reverse=True)

    return group_sizes


def process_test_cases():
    t = int(input())

    for _ in range(t):
        words = input().split()
        result = group_and_sort_anagrams(words)
        print(' '.join(map(str, result)))


process_test_cases()


```
