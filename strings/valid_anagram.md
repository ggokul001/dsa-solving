# Valid Anagram

##Problem Statement

Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

An **Anagram** is a word or phrase formed by rearranging the letters of another, using all the original letters exactly once.

---

##Approach (Hashing / Frequency Count)

To determine if two strings are anagrams:

1. If lengths are not equal → return `False`
2. Count frequency of each character in string `s`
3. Traverse string `t`:

   * If character not found → return `False`
   * Decrease frequency count
   * If frequency becomes negative → return `False`
4. If all checks pass → return `True`

---

##Time & Space Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(n)

---

## Example

### Input:

```
s = "anagram"
t = "nagaram"
```

### Output:

```
True
```

---

## Code (Python)

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        freq = {}

        for ch in s:
            if ch in freq:
                freq[ch] += 1
            else:
                freq[ch] = 1

        for ch in t:
            if ch not in freq:
                return False
            freq[ch] -= 1
            if freq[ch] < 0:
                return False

        return True
```

---

##Key Insight

* Instead of sorting (O(n log n)), we use **hashing** to achieve O(n)
* Frequency count ensures:

  * Same characters
  * Same number of occurrences

---

##Tags

* Hash Table
* String
* Counting
* Easy

---

## Practice Link

* LeetCode: https://leetcode.com/problems/valid-anagram/

---

##Author

**Gokulakrishnan G**
Aspiring Software Engineer | DSA Learner
