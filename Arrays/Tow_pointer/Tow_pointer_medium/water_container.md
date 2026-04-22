#Container With Most Water

##Problem Statement

You are given an integer array `height` of length `n`.

* Each element represents the height of a vertical line at index `i`
* Two lines together with the x-axis form a container

Find two lines that form a container such that it holds the **maximum amount of water**

---

##Example

### Input:

```id="ex1"
height = [1,8,6,2,5,4,8,3,7]
```

### Output:

```id="ex2"
49
```

---

##Approach (Two Pointer Technique)

###Idea (Simple English)

* Water is limited by:

  * **Width** = distance between two lines
  * **Height** = minimum of two heights

Formula:

```
Area = (right - left) * min(height[left], height[right])
```

---

###Key Observation

* We start with the **widest container**
* To improve area:

  * Move the pointer with **smaller height**
  * Because moving the taller one won’t increase area

---

##Steps

1. Initialize:

   * `left = 0`
   * `right = n - 1`
   * `max_water = 0`
2. While `left < right`:

   * Calculate width
   * Find minimum height
   * Compute area
   * Update max_water
   * Move pointer with smaller height
3. Return `max_water`

---

##Dry Run

### Input:

```id="dr1"
height = [1,8,6,2,5,4,8,3,7]
```

| Step | left | right | height[left] | height[right] | width | min height | area | max_water |
| ---- | ---- | ----- | ------------ | ------------- | ----- | ---------- | ---- | --------- |
| 1    | 0    | 8     | 1            | 7             | 8     | 1          | 8    | 8         |
| 2    | 1    | 8     | 8            | 7             | 7     | 7          | 49   | 49        |
| 3    | 1    | 7     | 8            | 3             | 6     | 3          | 18   | 49        |
| 4    | 1    | 6     | 8            | 8             | 5     | 8          | 40   | 49        |
| 5    | 1    | 5     | 8            | 4             | 4     | 4          | 16   | 49        |
| 6    | 1    | 4     | 8            | 5             | 3     | 5          | 15   | 49        |
| 7    | 1    | 3     | 8            | 2             | 2     | 2          | 4    | 49        |
| 8    | 1    | 2     | 8            | 6             | 1     | 6          | 6    | 49        |

---

###Final Output:

```id="dr2"
49
```

---

##Code (Python)

```python id="code1"
from typing import List

class Solution:
    def maxArea(self, height: List[int]) -> int:
        left = 0
        right = len(height) - 1
        max_water = 0

        while left < right:
            width = right - left
            h = min(height[left], height[right])
            area = width * h

            max_water = max(max_water, area)

            if height[left] < height[right]:
                left += 1
            else:
                right -= 1

        return max_water
```

---

##Time & Space Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(1)

---

##Key Insight

* Always move the pointer with **smaller height**
* Because area depends on minimum height
* Two pointer approach avoids brute force O(n²)

---

##Tags

* Array
* Two Pointers
* Greedy
* Medium

---

##Practice Link

* LeetCode: https://leetcode.com/problems/container-with-most-water/

---

##Author

**Gokulakrishnan G**
Aspiring Software Engineer | DSA Learner 
