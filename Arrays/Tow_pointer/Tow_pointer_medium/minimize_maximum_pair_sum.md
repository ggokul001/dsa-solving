#Minimize Maximum Pair Sum in Array

##Problem Statement

Given an array `nums` of even length `n`, divide it into `n / 2` pairs such that:

* Each element is used exactly once.
* The **maximum pair sum** among all pairs is as small as possible.

Return the **minimum possible value** of this maximum pair sum.

---

##Example

### Input

```python id="ex1"
nums = [3, 5, 2, 3]
```

### Output

```python id="ex2"
7
```

### Explanation

Possible pairing:

* `(2, 5)` → sum = 7
* `(3, 3)` → sum = 6

Maximum pair sum = `7`

This is the smallest possible maximum.

---

##Approach (Sorting + Two Pointers)

###Idea (Simple English)

To minimize the maximum pair sum:

* Pair the **smallest** number with the **largest** number.
* Pair the second smallest with the second largest.
* Continue this process.

Why?

* This balances the sums evenly.
* It prevents any single pair from becoming too large.

This is a classic **greedy strategy**.

---

##Algorithm Steps

1. Sort the array.
2. Initialize two pointers:

   * `left = 0` (smallest element)
   * `right = n - 1` (largest element)
3. For each pair:

   * Compute `nums[left] + nums[right]`
   * Update the maximum pair sum seen so far
   * Move both pointers inward
4. Return the maximum pair sum.

---

##Dry Run

### Input

```python id="dr1"
nums = [3, 5, 2, 3]
```

### After Sorting

```python id="dr2"
nums = [2, 3, 3, 5]
```

| Step | left | right | Pair   | Pair Sum | Maximum So Far |
| ---- | ---- | ----- | ------ | -------- | -------------- |
| 1    | 0    | 3     | (2, 5) | 7        | 7              |
| 2    | 1    | 2     | (3, 3) | 6        | 7              |

---

##Final Answer

```python id="ans1"
7
```

---

##Python Code

```python id="code1"
from typing import List

class Solution:
    def minPairSum(self, nums: List[int]) -> int:
        nums.sort()

        left = 0
        right = len(nums) - 1
        max_pair = 0

        while left < right:
            pair_sum = nums[left] + nums[right]
            max_pair = max(max_pair, pair_sum)

            left += 1
            right -= 1

        return max_pair
```

---

##Time and Space Complexity

* **Time Complexity:** `O(n log n)`

  * Sorting dominates the runtime.

* **Space Complexity:** `O(1)`

  * No extra space used (excluding sorting).

---

##Key Insight

* Pairing the smallest with the largest keeps pair sums balanced.
* This greedy approach guarantees the minimum possible maximum pair sum.

---

##Tags

* Array
* Two Pointers
* Greedy
* Sorting

---

##Practice Link

* LeetCode: https://leetcode.com/problems/minimize-maximum-pair-sum-in-array/

---

## ✨ Author

**Gokulakrishnan G**
Aspiring Software Engineer | Python & DSA Enthusiast 🚀
