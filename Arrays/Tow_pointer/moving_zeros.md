#Move Zeroes (Swap Approach)

##Problem Statement

Given an integer array `nums`, move all `0`s to the **end** while maintaining the **relative order of non-zero elements**.

* Must be done **in-place**
* Do not return anything, modify the array directly

---

##Example

### Input:

```id="ex1"
nums = [0,1,0,3,12]
```

### Output:

```id="ex2"
[1,3,12,0,0]
```

---

##Approach (Two Pointer + Swapping)

###Idea (Simple English)

* Use two pointers:

  * `fast` → scans the array
  * `slow` → tracks position to place next non-zero element
* When a non-zero element is found:

  * Swap it with position `slow`
  * Move `slow` forward

This way, all non-zero elements move to the front
Zeros automatically shift to the end

---

##Steps

1. Initialize `slow = 0`
2. Loop `fast` from 0 to end:

   * If `nums[fast] != 0`:

     * Swap `nums[slow]` and `nums[fast]`
     * Increment `slow`
3. Done (array modified in-place)

---

##Dry Run

### Input:

```id="dr1"
nums = [0,1,0,3,12]
```

| Step | slow | fast | nums[fast] | Action            | Array State  |
| ---- | ---- | ---- | ---------- | ----------------- | ------------ |
| 1    | 0    | 0    | 0          | Skip              | [0,1,0,3,12] |
| 2    | 0    | 1    | 1          | Swap(0,1), slow=1 | [1,0,0,3,12] |
| 3    | 1    | 2    | 0          | Skip              | [1,0,0,3,12] |
| 4    | 1    | 3    | 3          | Swap(1,3), slow=2 | [1,3,0,0,12] |
| 5    | 2    | 4    | 12         | Swap(2,4), slow=3 | [1,3,12,0,0] |

---

###Final Output:

```id="dr2"
[1,3,12,0,0]
```

---

##Code (Python)

```python id="code1"
from typing import List

class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        slow = 0
        for fast in range(len(nums)):
            if nums[fast] != 0:
                nums[slow], nums[fast] = nums[fast], nums[slow]
                slow += 1
```

---

##Time & Space Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(1)

---

##Key Insight

* Swapping places non-zero elements directly in correct position
* Maintains relative order automatically
* No need for extra loop to fill zeros
* More optimal and clean compared to overwrite method

---

##Tags

* Array
* Two Pointers
* In-place
* Easy

---

##Practice Link

* LeetCode: https://leetcode.com/problems/move-zeroes/

---

##Author

**Gokulakrishnan G**
Aspiring Software Engineer | DSA Learner 
