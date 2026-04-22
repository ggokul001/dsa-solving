# 🧹 Remove Duplicates from Sorted Array

## 📌 Problem Statement

Given an integer array `nums` sorted in **non-decreasing order**, remove the duplicates **in-place** such that each unique element appears only once.

Return the number of unique elements `k`.

* The first `k` elements of `nums` should contain the unique elements
* The remaining elements can be ignored

---

## 🧪 Example

### Input:

```id="ex1"
nums = [1, 1, 2]
```

### Output:

```id="ex2"
k = 2
nums = [1, 2, _]
```

---

### Input:

```id="ex3"
nums = [0,0,1,1,1,2,2,3,3,4]
```

### Output:

```id="ex4"
k = 5
nums = [0,1,2,3,4,_,_,_,_,_]
```

---

## 🧠 Approach (Two Pointer Technique)

### 💡 Idea (Simple English)

* Since the array is already **sorted**, duplicates will be **next to each other**
* We use **two pointers**:

  * `i` → tracks position of last unique element
  * `j` → scans the array

---

## 🚀 Steps

1. Start `i = 0`
2. Loop `j` from 1 to end:

   * If `nums[j] != nums[i]`:

     * Move `i` forward
     * Update `nums[i] = nums[j]`
3. Return `i + 1` (count of unique elements)

---

## 🔄 Dry Run

### Input:

```
nums = [0,0,1,1,1,2,2,3,3,4]
```

| Step | i | j | nums[j] | nums[i] | Action               | Array State           |
| ---- | - | - | ------- | ------- | -------------------- | --------------------- |
| 1    | 0 | 1 | 0       | 0       | Same → skip          | [0,0,1,1,1,2,2,3,3,4] |
| 2    | 0 | 2 | 1       | 0       | New → i=1, nums[1]=1 | [0,1,1,1,1,2,2,3,3,4] |
| 3    | 1 | 3 | 1       | 1       | Same → skip          | [0,1,1,1,1,2,2,3,3,4] |
| 4    | 1 | 4 | 1       | 1       | Same → skip          | [0,1,1,1,1,2,2,3,3,4] |
| 5    | 1 | 5 | 2       | 1       | New → i=2, nums[2]=2 | [0,1,2,1,1,2,2,3,3,4] |
| 6    | 2 | 6 | 2       | 2       | Same → skip          | [0,1,2,1,1,2,2,3,3,4] |
| 7    | 2 | 7 | 3       | 2       | New → i=3, nums[3]=3 | [0,1,2,3,1,2,2,3,3,4] |
| 8    | 3 | 8 | 3       | 3       | Same → skip          | [0,1,2,3,1,2,2,3,3,4] |
| 9    | 3 | 9 | 4       | 3       | New → i=4, nums[4]=4 | [0,1,2,3,4,2,2,3,3,4] |

---

### ✅ Final Output:

```
k = 5
nums = [0,1,2,3,4,_,_,_,_,_]
```

---

## 🧾 Code (Python)

```python id="code1"
from typing import List

class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        i = 0

        for j in range(1, len(nums)):
            if nums[j] != nums[i]:
                i += 1
                nums[i] = nums[j]

        return i + 1
```

---

## ⚡ Time & Space Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(1) (in-place)

---

## 💡 Key Insight

* Sorted array helps us detect duplicates easily
* Two pointer approach avoids extra space
* We overwrite duplicates instead of removing them

---

## 🚀 Tags

* Array
* Two Pointers
* In-place
* Easy

---

## 📚 Practice Link

* LeetCode: https://leetcode.com/problems/remove-duplicates-from-sorted-array/

---

## ✨ Author

**Gokulakrishnan G**
Aspiring Software Engineer | DSA Learner 🚀
