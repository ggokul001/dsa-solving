#Rearrange Array Elements by Sign

##Problem Statement

Given an integer array `nums`:

* The array has an **even length**
* It contains an equal number of:

  * Positive integers
  * Negative integers

Rearrange the array such that:

1. Every adjacent pair has opposite signs.
2. The array starts with a **positive** integer.
3. The relative order of positive numbers remains the same.
4. The relative order of negative numbers remains the same.

---

##Example

### Input

```python id="ex1"
nums = [3, 1, -2, -5, 2, -4]
```

### Output

```python id="ex2"
[3, -2, 1, -5, 2, -4]
```

---

##Approach (Separate Positives and Negatives)

###Idea (Simple English)

* First, separate all positive numbers into one list.
* Separate all negative numbers into another list.
* Since the result must start with a positive number:

  * Add one positive
  * Then one negative
  * Repeat until all elements are used

This automatically preserves the original order of positives and negatives.

---

##Algorithm Steps

1. Create three empty lists:

   * `positives`
   * `negatives`
   * `result`
2. Traverse the array:

   * If number is positive, add to `positives`
   * Otherwise, add to `negatives`
3. Loop through both lists:

   * Add one positive
   * Add one negative
4. Return the final `result`

---

##Dry Run

### Input

```python id="dr1"
nums = [3, 1, -2, -5, 2, -4]
```

---

### Step 1: Separate Numbers

```python id="dr2"
positives = [3, 1, 2]
negatives = [-2, -5, -4]
```

---

### Step 2: Build Result

| Iteration | Add Positive | Add Negative | Result                |
| --------- | ------------ | ------------ | --------------------- |
| 1         | 3            | -2           | [3, -2]               |
| 2         | 1            | -5           | [3, -2, 1, -5]        |
| 3         | 2            | -4           | [3, -2, 1, -5, 2, -4] |

---

##Final Answer

```python id="ans1"
[3, -2, 1, -5, 2, -4]
```

---

##Python Code

```python id="code1"
from typing import List

class Solution:
    def rearrangeArray(self, nums: List[int]) -> List[int]:
        positives = []
        negatives = []
        result = []

        for num in nums:
            if num > 0:
                positives.append(num)
            else:
                negatives.append(num)

        for i in range(len(positives)):
            result.append(positives[i])
            result.append(negatives[i])

        return result
```

---

##Time and Space Complexity

* **Time Complexity:** `O(n)`

  * One pass to separate numbers
  * One pass to build the result

* **Space Complexity:** `O(n)`

  * Additional lists are used

---

##Key Insight

* Since order must be preserved, separating positives and negatives is the easiest approach.
* Then simply alternate them starting with a positive number.

---

##Tags

* Array
* Simulation
* Two Pointers
* Rearrangement

---

## Practice Link

* LeetCode: https://leetcode.com/problems/rearrange-array-elements-by-sign/

---

## ✨ Author

**Gokulakrishnan G**
Aspiring Software Engineer | Python & DSA Enthusiast 🚀
