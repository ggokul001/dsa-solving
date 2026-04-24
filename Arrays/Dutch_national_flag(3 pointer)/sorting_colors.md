# 🇳🇱 Sort Colors (Dutch National Flag Algorithm)

##Problem Statement

Given an array `nums` with `n` objects colored:

* `0` → Red
* `1` → White
* `2` → Blue

Sort the array **in-place** so that:

All `0`s come first, then `1`s, then `2`s

You must NOT use built-in sort functions.

---

##Example

### Input:

```id="ex1"
nums = [2,0,2,1,1,0]
```

### Output:

```id="ex2"
[0,0,1,1,2,2]
```

---

##Approach (Dutch National Flag Algorithm)

###Idea (Simple English)

We divide the array into **3 regions**:

```
[ 0s | 1s | Unknown | 2s ]
   ↑     ↑       ↑     ↑
  low   mid            high
```

* `low` → next position for `0`
* `mid` → current element being checked
* `high` → next position for `2`

---

##Rules

While `mid <= high`:

###Case 1: nums[mid] == 0

* Swap with `low`
* Move both `low` and `mid`

###Case 2: nums[mid] == 1

* Just move `mid`

###Case 3: nums[mid] == 2

* Swap with `high`
* Move `high` only (do NOT move mid)

---

##Dry Run

### Input:

```id="dr1"
nums = [2,0,2,1,1,0]
```

| Step | low | mid | high | nums[mid] | Action                      | Array State   |
| ---- | --- | --- | ---- | --------- | --------------------------- | ------------- |
| 1    | 0   | 0   | 5    | 2         | Swap(mid,high), high--      | [0,0,2,1,1,2] |
| 2    | 0   | 0   | 4    | 0         | Swap(low,mid), low++, mid++ | [0,0,2,1,1,2] |
| 3    | 1   | 1   | 4    | 0         | Swap(low,mid), low++, mid++ | [0,0,2,1,1,2] |
| 4    | 2   | 2   | 4    | 2         | Swap(mid,high), high--      | [0,0,1,1,2,2] |
| 5    | 2   | 2   | 3    | 1         | mid++                       | [0,0,1,1,2,2] |
| 6    | 2   | 3   | 3    | 1         | mid++                       | [0,0,1,1,2,2] |

---

###Final Output:

```id="dr2"
[0,0,1,1,2,2]
```

---

##Code (Python)

```python id="code1"
from typing import List

class Solution:
    def sortColors(self, nums: List[int]) -> None:
        low = 0
        mid = 0
        high = len(nums) - 1

        while mid <= high:
            if nums[mid] == 0:
                nums[low], nums[mid] = nums[mid], nums[low]
                low += 1
                mid += 1

            elif nums[mid] == 1:
                mid += 1

            else:
                nums[mid], nums[high] = nums[high], nums[mid]
                high -= 1
```

---

##Time & Space Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(1)

---

##Key Insight

* This is a **3-pointer partitioning problem**
* Avoids sorting (O(n log n))
* Solves in **single pass**
* Very common interview pattern

---

##Tags

* Array
* Two Pointers
* Sorting
* Medium

---

##Practice Link

* LeetCode: https://leetcode.com/problems/sort-colors/

---

##Author

**Gokulakrishnan G**
Aspiring Software Engineer | DSA Learner 
