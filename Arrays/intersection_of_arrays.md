#Intersection of Two Arrays

##Problem Statement

Given two integer arrays `nums1` and `nums2`, return an array of their **intersection**.

Each element in the result must be **unique**, and you may return the result in any order.

---

##Approach (Using Set for Efficient Lookup)

To find the intersection efficiently:

1. Convert `nums1` into a **set** for O(1) lookup
2. Create an empty set `result` to store unique common elements
3. Traverse through `nums2`:

   * If element exists in `set1`, add it to `result`
4. Convert result set to list and return

---

##Time & Space Complexity

* **Time Complexity:** O(n + m)
* **Space Complexity:** O(n)

---

##Example

### Input:

```
nums1 = [1,2,2,1]
nums2 = [2,2]
```

### Output:

```
[2]
```

---

##Code (Python)

```python
from typing import List

class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        set1 = set(nums1)
        result = set()

        for num in nums2:
            if num in set1:
                result.add(num)

        return list(result)
```

---

##Key Insight

* Using a **set** allows constant time lookup O(1)
* Another set ensures **unique elements only**
* Avoids duplicates automatically

---

## Tags

* Hash Table
* Set
* Array
* Easy

---

##Practice Link

* LeetCode: https://leetcode.com/problems/intersection-of-two-arrays/

---

##Author

**Gokulakrishnan G**
Aspiring Software Engineer | DSA Learner 🚀
