# 🔢 Squares of a Sorted Array (Two Pointer Approach)

## 📌 Problem Statement

Given an integer array `nums` sorted in **non-decreasing order**, return an array of the **squares of each number** also sorted in non-decreasing order.

---

## 🧪 Example

### Input:

```id="ex1"
nums = [-4, -1, 0, 3, 10]
```

### Output:

```id="ex2"
[0, 1, 9, 16, 100]
```

---

## 🧠 Approach (Two Pointer Technique)

### 💡 Idea (Simple English)

* The array is sorted, but squaring negative numbers makes them positive
* The **largest square** will come from:

  * Either the **leftmost (negative large value)**
  * Or the **rightmost (positive large value)**

👉 So we compare both ends and place the larger square at the end

---

## 🚀 Steps

1. Create a result array of same size
2. Use three pointers:

   * `left = 0`
   * `right = n - 1`
   * `pos = n - 1` (to fill from end)
3. Compare `abs(nums[left])` and `abs(nums[right])`
4. Place the larger square at `result[pos]`
5. Move the corresponding pointer
6. Decrease `pos`
7. Repeat until `left > right`

---

## 🔄 Dry Run

### Input:

```id="dr1"
nums = [-4, -1, 0, 3, 10]
```

| Step | left | right | nums[left] | nums[right] | Chosen | Result Position | Result Array       |
| ---- | ---- | ----- | ---------- | ----------- | ------ | --------------- | ------------------ |
| 1    | 0    | 4     | -4         | 10          | 100    | 4               | [_, _, _, _, 100]  |
| 2    | 0    | 3     | -4         | 3           | 16     | 3               | [_, _, _, 16, 100] |
| 3    | 1    | 3     | -1         | 3           | 9      | 2               | [_, _, 9, 16, 100] |
| 4    | 1    | 2     | -1         | 0           | 1      | 1               | [_, 1, 9, 16, 100] |
| 5    | 2    | 2     | 0          | 0           | 0      | 0               | [0, 1, 9, 16, 100] |

---

### ✅ Final Output:

```id="dr2"
[0, 1, 9, 16, 100]
```

---

## 🧾 Code (Python)

```python id="code1"
from typing import List

class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        n = len(nums)
        result = [0] * n

        left = 0
        right = n - 1
        pos = n - 1

        while left <= right:
            if abs(nums[left]) > abs(nums[right]):
                result[pos] = nums[left] * nums[left]
                left += 1
            else:
                result[pos] = nums[right] * nums[right]
                right -= 1

            pos -= 1

        return result
```

---

## ⚡ Time & Space Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(n)

---

## 💡 Key Insight

* Compare absolute values to find the largest square
* Fill from the end to maintain sorted order
* Avoids extra sorting (better than O(n log n))

---

## 🚀 Tags

* Array
* Two Pointers
* Sorting
* Easy

---

## 📚 Practice Link

* LeetCode: https://leetcode.com/problems/squares-of-a-sorted-array/

---

## ✨ Author

**Gokulakrishnan G**
Aspiring Software Engineer | DSA Learner 🚀
