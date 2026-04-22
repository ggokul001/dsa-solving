# 🧹 Remove Element

## 📌 Problem Statement

Given an integer array `nums` and an integer `val`, remove all occurrences of `val` **in-place**.

Return the number of elements `k` which are **not equal to `val`**.

* The first `k` elements of `nums` should contain the values not equal to `val`
* The order of elements **can be changed**
* Remaining elements can be ignored

---

## 🧪 Example

### Input:

```id="ex1"
nums = [3,2,2,3]
val = 3
```

### Output:

```id="ex2"
k = 2
nums = [2,2,_,_]
```

---

### Input:

```id="ex3"
nums = [0,1,2,2,3,0,4,2]
val = 2
```

### Output:

```id="ex4"
k = 5
nums = [0,1,3,0,4,_,_,_]
```

---

## 🧠 Approach (Two Pointer Technique)

### 💡 Idea (Simple English)

* We need to remove all elements equal to `val`
* Use two pointers:

  * `i` → position to place next valid element
  * `j` → scans the array

---

## 🚀 Steps

1. Initialize `i = 0`
2. Loop `j` from 0 to end:

   * If `nums[j] != val`:

     * Place it at index `i`
     * Increment `i`
3. Return `i` (count of valid elements)

---

## 🔄 Dry Run

### Input:

```id="dr1"
nums = [0,1,2,2,3,0,4,2]
val = 2
```

| Step | i | j | nums[j] | Action                | Array State       |
| ---- | - | - | ------- | --------------------- | ----------------- |
| 1    | 0 | 0 | 0       | Keep → nums[0]=0, i=1 | [0,1,2,2,3,0,4,2] |
| 2    | 1 | 1 | 1       | Keep → nums[1]=1, i=2 | [0,1,2,2,3,0,4,2] |
| 3    | 2 | 2 | 2       | Skip (val)            | [0,1,2,2,3,0,4,2] |
| 4    | 2 | 3 | 2       | Skip (val)            | [0,1,2,2,3,0,4,2] |
| 5    | 2 | 4 | 3       | Keep → nums[2]=3, i=3 | [0,1,3,2,3,0,4,2] |
| 6    | 3 | 5 | 0       | Keep → nums[3]=0, i=4 | [0,1,3,0,3,0,4,2] |
| 7    | 4 | 6 | 4       | Keep → nums[4]=4, i=5 | [0,1,3,0,4,0,4,2] |
| 8    | 5 | 7 | 2       | Skip (val)            | [0,1,3,0,4,0,4,2] |

---

### ✅ Final Output:

```id="dr2"
k = 5
nums = [0,1,3,0,4,_,_,_]
```

---

## 🧾 Code (Python)

```python id="code1"
from typing import List

class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        i = 0

        for j in range(len(nums)):
            if nums[j] != val:
                nums[i] = nums[j]
                i += 1

        return i
```

---

## ⚡ Time & Space Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(1) (in-place)

---

## 💡 Key Insight

* We overwrite elements equal to `val`
* No need to delete elements physically
* Two pointer approach is efficient and simple

---

## 🚀 Tags

* Array
* Two Pointers
* In-place
* Easy

---

## 📚 Practice Link

* LeetCode: https://leetcode.com/problems/remove-element/

---

## ✨ Author

**Gokulakrishnan G**
Aspiring Software Engineer | DSA Learner 🚀
