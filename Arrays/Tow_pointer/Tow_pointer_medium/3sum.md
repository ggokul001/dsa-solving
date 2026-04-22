#3Sum

##Problem Statement

Given an integer array `nums`, return all the **unique triplets** `[nums[i], nums[j], nums[k]]` such that:

* `i != j`, `i != k`, `j != k`
* `nums[i] + nums[j] + nums[k] == 0`

The solution must **not contain duplicate triplets**

---

##Example

### Input:

```id="ex1"
nums = [-1,0,1,2,-1,-4]
```

### Output:

```id="ex2"
[[-1,-1,2], [-1,0,1]]
```

---

##Approach (Sorting + Two Pointer)

###Idea (Simple English)

* First, **sort the array**
* Fix one element (`i`)
* Use **two pointers** (`left`, `right`) to find pairs such that:

  ```
  nums[i] + nums[left] + nums[right] = 0
  ```

---

##Steps

1. Sort the array
2. Loop through each index `i`:

   * Skip duplicates for `i`
3. Set:

   * `left = i + 1`
   * `right = n - 1`
4. While `left < right`:

   * Calculate sum
   * If sum == 0 → store result
   * Skip duplicates for `left` and `right`
   * Move both pointers
   * If sum < 0 → move `left++`
   * If sum > 0 → move `right--`

---

##Dry Run

### Input:

```id="dr1"
nums = [-1,0,1,2,-1,-4]
```

### After Sorting:

```id="dr2"
[-4, -1, -1, 0, 1, 2]
```

| i | nums[i] | left | right | Triplet          | Action     |
| - | ------- | ---- | ----- | ---------------- | ---------- |
| 0 | -4      | 1    | 5     | [-4,-1,2] = -3   | left++     |
|   |         | 2    | 5     | [-4,-1,2] = -3   | left++     |
|   |         | 3    | 5     | [-4,0,2] = -2    | left++     |
|   |         | 4    | 5     | [-4,1,2] = -1    | left++     |
| 1 | -1      | 2    | 5     | [-1,-1,2] = 0 ✅  | Add result |
|   |         | 3    | 4     | [-1,0,1] = 0 ✅   | Add result |
| 2 | -1      | —    | —     | Duplicate → skip |            |
| 3 | 0       | 4    | 5     | [0,1,2] = 3      | right--    |

---

###Final Output:

```id="dr3"
[[-1,-1,2], [-1,0,1]]
```

---

##Code (Python)

```python id="code1"
from typing import List

class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        nums.sort()
        result = []

        for i in range(len(nums)):
            if i > 0 and nums[i] == nums[i - 1]:
                continue

            left = i + 1
            right = len(nums) - 1

            while left < right:
                total = nums[i] + nums[left] + nums[right]

                if total == 0:
                    result.append([nums[i], nums[left], nums[right]])

                    left += 1
                    right -= 1

                    while left < right and nums[left] == nums[left - 1]:
                        left += 1

                    while left < right and nums[right] == nums[right + 1]:
                        right -= 1

                elif total < 0:
                    left += 1
                else:
                    right -= 1

        return result
```

---

##Time & Space Complexity

* **Time Complexity:** O(n²)
* **Space Complexity:** O(1) (excluding output)

---

##Key Insight

* Sorting helps to:

  * Use two pointer technique
  * Avoid duplicates easily
* Skip duplicate values to ensure unique triplets
* Reduces brute force O(n³) → O(n²)

---

##Tags

* Array
* Two Pointers
* Sorting
* Medium

---

##Practice Link

* LeetCode: https://leetcode.com/problems/3sum/

---

##Author

**Gokulakrishnan G**
Aspiring Software Engineer | DSA Learner 
