#Partition Array According to Given Pivot

##Problem Statement

Given an integer array `nums` and an integer `pivot`, rearrange the array such that:

1. All elements **less than** `pivot` come first.
2. All elements **equal to** `pivot` come next.
3. All elements **greater than** `pivot` come last.

### Important

* The relative order of elements less than `pivot` must remain the same.
* The relative order of elements greater than `pivot` must also remain the same.

This means the partitioning must be **stable**.

---

##Example

### Input

```python id="ex1"
nums = [9, 12, 5, 10, 14, 3, 10]
pivot = 10
```

### Output

```python id="ex2"
[9, 5, 3, 10, 10, 12, 14]
```

---

##Approach (Three Separate Lists)

###Idea (Simple English)

We divide the array into three groups:

* `less` → elements smaller than `pivot`
* `equal` → elements equal to `pivot`
* `greater` → elements greater than `pivot`

Since we traverse the array from left to right and append elements in order, the relative order is automatically preserved.

Finally, combine all three lists.

---

##Algorithm Steps

1. Create three empty lists:

   * `less`
   * `equal`
   * `greater`
2. Traverse each element in `nums`:

   * If element `< pivot`, add to `less`
   * If element `== pivot`, add to `equal`
   * If element `> pivot`, add to `greater`
3. Return:

   ```python
   less + equal + greater
   ```

---

##Dry Run

### Input

```python id="dr1"
nums = [9, 12, 5, 10, 14, 3, 10]
pivot = 10
```

| Element | Condition | List Updated       |
| ------- | --------- | ------------------ |
| 9       | `< 10`    | less = [9]         |
| 12      | `> 10`    | greater = [12]     |
| 5       | `< 10`    | less = [9, 5]      |
| 10      | `== 10`   | equal = [10]       |
| 14      | `> 10`    | greater = [12, 14] |
| 3       | `< 10`    | less = [9, 5, 3]   |
| 10      | `== 10`   | equal = [10, 10]   |

---

### Final Lists

```python id="dr2"
less    = [9, 5, 3]
equal   = [10, 10]
greater = [12, 14]
```

---

### Final Result

```python id="dr3"
[9, 5, 3, 10, 10, 12, 14]
```

---

##Python Code

```python id="code1"
from typing import List

class Solution:
    def pivotArray(self, nums: List[int], pivot: int) -> List[int]:
        less = []
        equal = []
        greater = []

        for num in nums:
            if num < pivot:
                less.append(num)
            elif num == pivot:
                equal.append(num)
            else:
                greater.append(num)

        return less + equal + greater
```

---

##Time and Space Complexity

* **Time Complexity:** `O(n)`

  * We traverse the array once.

* **Space Complexity:** `O(n)`

  * We use three additional lists.

---

##Key Insight

* This is a **stable partitioning** problem.
* Using three separate lists makes the solution simple and easy to understand.
* Relative order is preserved automatically.

---

##Tags

* Array
* Partitioning
* Simulation
* Stable Rearrangement

---

##Practice Link

* LeetCode: https://leetcode.com/problems/partition-array-according-to-given-pivot/

---

##Author

**Gokulakrishnan G**
Aspiring Software Engineer | Python & DSA Enthusiast
