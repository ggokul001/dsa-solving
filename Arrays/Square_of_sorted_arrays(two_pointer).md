#Squares of a Sorted Array

##Problem Statement

Given an integer array `nums` sorted in **non-decreasing order**, return an array of the **squares of each number** also sorted in non-decreasing order.

---

##Example

### Input:

```
nums = [-4, -1, 0, 3, 10]
```

### Output:

```
[0, 1, 9, 16, 100]
```

### Explanation:

After squaring → `[16, 1, 0, 9, 100]`
After sorting → `[0, 1, 9, 16, 100]`

---

##Approach (Two Pointer Technique)

###Key Observation:

* Negative numbers become **positive after squaring**
* Largest square will come from either:

  * Leftmost (negative large value)
  * Rightmost (positive large value)

---

###Steps:

1. Initialize two pointers:

   * `left = 0`
   * `right = n - 1`
2. Create a result array of size `n`
3. Fill result from **end to start**
4. Compare:

   * `nums[left]^2` vs `nums[right]^2`
5. Place the **larger square** at current index
6. Move corresponding pointer
7. Repeat until `left > right`

---

##Time & Space Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(n)

---

##Iteration Table

| Step | Left | Right | nums[left] | nums[right] | Square Left | Square Right | Placed Value | Result Array       |
| ---- | ---- | ----- | ---------- | ----------- | ----------- | ------------ | ------------ | ------------------ |
| 1    | 0    | 4     | -4         | 10          | 16          | 100          | 100          | [_, _, _, _, 100]  |
| 2    | 0    | 3     | -4         | 3           | 16          | 9            | 16           | [_, _, _, 16, 100] |
| 3    | 1    | 3     | -1         | 3           | 1           | 9            | 9            | [_, _, 9, 16, 100] |
| 4    | 1    | 2     | -1         | 0           | 1           | 0            | 1            | [_, 1, 9, 16, 100] |
| 5    | 2    | 2     | 0          | 0           | 0           | 0            | 0            | [0, 1, 9, 16, 100] |

---

##Code (Python)

```python
from typing import List

class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        n = len(nums)
        result = [0] * n

        left, right = 0, n - 1
        index = n - 1

        while left <= right:
            if abs(nums[left]) > abs(nums[right]):
                result[index] = nums[left] ** 2
                left += 1
            else:
                result[index] = nums[right] ** 2
                right -= 1

            index -= 1

        return result
```

---

##Key Insight

* Instead of sorting after squaring (O(n log n)), we use **two pointers** for O(n)
* Compare absolute values to determine the largest square
* Fill from the back to maintain sorted order

---

##Tags

* Array
* Two Pointers
* Sorting
* Easy

---

##Practice Link

* LeetCode: https://leetcode.com/problems/squares-of-a-sorted-array/

---

##Author

**Gokulakrishnan G**
Aspiring Software Engineer | DSA Learner 
