## **Long words**

Chef dislikes writing long words. Whenever he encounters a word with more than 10 characters, he abbreviates it using a special rule.

**Abbreviation Rule**  
Write the first letter of the word, followed by the number of characters between the first and last letter (excluding the first and last letters). This number must be in decimal format and should not have any leading zeros. Finally, write the last letter of the word.

For example:
- The word `"codechefvit"` will be abbreviated as `"c9t"`.
- The word `"homogeneous"` will be abbreviated as `"h9s"`.

If the word has 10 or fewer characters, it remains unchanged.

### Input Format
- The first line contains an integer `t` — the number of words.
- Each of the next `t` lines contains a single word `w`.

### Output Format
For each word, output either the original word (if it has 10 or fewer characters) or its abbreviated form (if it has more than 10 characters).

### Solution (O(1) Complexity)

```python
for i in range(int(input())):
    word = input()
    if len(word) > 10:
        print(word[0] + str(len(word) - 2) + word[-1])
    else:
        print(word)
```