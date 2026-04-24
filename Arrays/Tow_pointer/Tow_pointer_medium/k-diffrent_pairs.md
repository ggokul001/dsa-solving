#K-diff Pairs in an Array

##Problem Statement

Given an integer array `nums` and an integer `k`, return the number of **unique k-diff pairs** in the array.

A **k-diff pair** is a pair `(nums[i], nums[j])` such that:

* `0 <= i, j < nums.length`
* `i != j`
* `|nums[i] - nums[j]| == k`

`|x|` means absolute value.

---

##Example

### Input

```python
nums = [3,1,4,1,5]
k = 2
```

### Output

```python
2
```

### Explanation

The unique pairs are:

* `(1, 3)`
* `(3, 5)`

So the answer is `2`.

---

##Approach (Sorting + Two Pointers)

###Idea (Simple English)

* First, sort the array.
* Use two pointers:

  * `left` → first number
  * `right` → second number
* Since the array is sorted:

  * If difference is too small, move `right`
  * If difference is too large, move `left`
  * If difference equals `k`, we found a valid pair

To avoid duplicates, skip repeated values after counting a pair.

---

##Algorithm Steps

1. If `k < 0`, return `0` (absolute difference can never be negative).
2. Sort the array.
3. Initialize:

   * `left = 0`
   * `right = 1`
   * `count = 0`
4. While `right < n`:

   * If `left == right` or difference `< k`, move `right`
   * If difference `> k`, move `left`
   * If difference `== k`:

     * Increment count
     * Move both pointers
     * Skip duplicate values for `right`

---

##Dry Run

### Input

```python
nums = [3,1,4,1,5]
k = 2
```

### After Sorting

```python
nums = [1,1,3,4,5]
```

| Step | left | right | Pair  | Difference | Action       | Count |
| ---- | ---- | ----- | ----- | ---------- | ------------ | ----- |
| 1    | 0    | 1     | (1,1) | 0          | Move `right` | 0     |
| 2    | 0    | 2     | (1,3) | 2          | Valid pair ✅ | 1     |
| 3    | 1    | 3     | (1,4) | 3          | Move `left`  | 1     |
| 4    | 2    | 3     | (3,4) | 1          | Move `right` | 1     |
| 5    | 2    | 4     | (3,5) | 2          | Valid pair ✅ | 2     |

### Final Answer

```python
2
```

---

##Python Code

```python
from typing import List

class Solution:
    def findPairs(self, nums: List[int], k: int) -> int:
        if k < 0:
            return 0

        nums.sort()
        left, right = 0, 1
        count = 0
        n = len(nums)

        while right < n:
            if left == right or nums[right] - nums[left] < k:
                right += 1

            elif nums[right] - nums[left] > k:
                left += 1

            else:
                count += 1
                left += 1
                right += 1

                while right < n and nums[right] == nums[right - 1]:
                    right += 1

        return count
```

---

##Time and Space Complexity

* **Time Complexity:** `O(n log n)`

  * Sorting takes `O(n log n)`
  * Two-pointer traversal takes `O(n)`

* **Space Complexity:** `O(1)`

  * No extra space used (excluding sorting space)

---

##Key Insight

* Sorting helps us efficiently compare differences.
* Two pointers avoid checking all pairs.
* Skipping duplicates ensures only **unique pairs** are counted.

---

##Tags

* Array
* Two Pointers
* Sorting
* Hashing (alternative approach)

---

##Practice Link

* LeetCode: https://leetcode.com/problems/k-diff-pairs-in-an-array/

---

##Author

**Gokulakrishnan G**
Aspiring Software Engineer | Python & DSA Enthusiast 
