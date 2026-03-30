#Group Anagrams

##Problem Statement

Given an array of strings `strs`, group the anagrams together. You can return the answer in any order.

An **Anagram** is a word formed by rearranging the letters of another word using all original letters exactly once.

---

##Approach (HashMap + Sorted String Key)

To group anagrams efficiently:

1. Create a dictionary (`hashmap`) to store groups
2. For each word in the list:

   * Sort the word → this becomes the key
   * If key exists → append the word to the list
   * Else → create a new list with that word
3. Return all values of the dictionary

---

##Time & Space Complexity

* **Time Complexity:** O(n * k log k)
  (where `n` = number of strings, `k` = max length of a string)

* **Space Complexity:** O(n * k)

---

##Example

### Input:

```id="a2k9s1"
strs = ["eat","tea","tan","ate","nat","bat"]
```

### Output:

```id="j3h7l9"
[["eat","tea","ate"],["tan","nat"],["bat"]]
```

---

##Code (Python)

```python id="z8x2pq"
from typing import List

class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        hashmap = {}

        for word in strs:
            key = ''.join(sorted(word))

            if key in hashmap:
                hashmap[key].append(word)
            else:
                hashmap[key] = [word]

        return list(hashmap.values())
```

---

##Key Insight

* Sorting each word ensures all anagrams share the same key
* HashMap groups words with identical sorted keys
* Efficient grouping without comparing every pair

---

##Tags

* Hash Table
* String
* Sorting
* Medium

---

##Practice Link

* LeetCode: https://leetcode.com/problems/group-anagrams/

---

##Author

**Gokulakrishnan G**
Aspiring Software Engineer | DSA Learner
