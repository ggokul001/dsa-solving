#4Sum

##Problem Statement

Given an integer array `nums` of size `n`, return all the **unique quadruplets**:

```
[nums[a], nums[b], nums[c], nums[d]]
```

Such that:

* `0 <= a, b, c, d < n`
* All indices are **distinct**
* `nums[a] + nums[b] + nums[c] + nums[d] == target`

Return the answer in **any order**
The solution must **not contain duplicate quadruplets**

---

##Example

### Input:

```id="ex1"
nums = [1,0,-1,0,-2,2]
target = 0
```

### Output:

```id="ex2"
[[-2,-1,1,2], [-2,0,0,2], [-1,0,0,1]]
```

---

##Approach (Sorting + Two Pointer)

###Idea (Simple English)

* Similar to 3Sum, but with one extra loop
* First **sort the array**
* Fix two numbers (`i` and `j`)
* Use two pointers (`left`, `right`) to find remaining two numbers

---

##Steps

1. Sort the array
2. Loop `i` from 0 to n:

   * Skip duplicates for `i`
3. Loop `j` from `i+1` to n:

   * Skip duplicates for `j`
4. Set:

   * `left = j + 1`
   * `right = n - 1`
5. While `left < right`:

   * Calculate total sum
   * If sum == target → store result
   * Skip duplicates
   * Move pointers
   * If sum < target → `left++`
   * If sum > target → `right--`

---

##Dry Run

### Input:

```id="dr1"
nums = [1,0,-1,0,-2,2]
target = 0
```

### After Sorting:

```id="dr2"
[-2,-1,0,0,1,2]
```

| i | j | left | right | Quadruplet  | Sum | Action     |
| - | - | ---- | ----- | ----------- | --- | ---------- |
| 0 | 1 | 2    | 5     | [-2,-1,0,2] | -1  | left++     |
| 0 | 1 | 3    | 5     | [-2,-1,0,2] | -1  | left++     |
| 0 | 1 | 4    | 5     | [-2,-1,1,2] | 0   | Add result |
| 0 | 2 | 3    | 5     | [-2,0,0,2]  | 0   | Add result |
| 1 | 2 | 3    | 5     | [-1,0,0,2]  | 1   | right--    |
| 1 | 2 | 3    | 4     | [-1,0,0,1]  | 0   | Add result |

---

###Final Output:

```id="dr3"
[[-2,-1,1,2], [-2,0,0,2], [-1,0,0,1]]
```

---

##Code (Python)

```python id="code1"
from typing import List

class Solution:
    def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        nums.sort()
        n = len(nums)
        result = []

        for i in range(n):
            if i > 0 and nums[i] == nums[i - 1]:
                continue

            for j in range(i + 1, n):
                if j > i + 1 and nums[j] == nums[j - 1]:
                    continue

                left = j + 1
                right = n - 1

                while left < right:
                    total = nums[i] + nums[j] + nums[left] + nums[right]

                    if total == target:
                        result.append([nums[i], nums[j], nums[left], nums[right]])

                        left += 1
                        right -= 1

                        while left < right and nums[left] == nums[left - 1]:
                            left += 1

                        while left < right and nums[right] == nums[right + 1]:
                            right -= 1

                    elif total < target:
                        left += 1
                    else:
                        right -= 1

        return result
```

---

##Time & Space Complexity

* **Time Complexity:** O(n³)
* **Space Complexity:** O(1) (excluding output)

---

##Key Insight

* Extension of 3Sum problem
* Sorting helps avoid duplicates
* Two pointer reduces complexity from O(n⁴) → O(n³)

---

##Tags

* Array
* Two Pointers
* Sorting
* Medium / Hard

---

##Practice Link

* LeetCode: https://leetcode.com/problems/4sum/

---

##Author

**Gokulakrishnan G**
Aspiring Software Engineer | DSA Learner 
