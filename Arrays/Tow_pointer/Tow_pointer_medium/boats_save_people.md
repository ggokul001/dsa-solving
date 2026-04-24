#Boats to Save People

##Problem Statement

You are given an array `people` where `people[i]` represents the weight of the `i-th` person.

* Each boat can carry at most **2 people**
* The total weight on a boat must not exceed `limit`

Return the **minimum number of boats** needed to rescue everyone.

---

##Example

### Input

```python id="ex1"
people = [3, 2, 2, 1]
limit = 3
```

### Output

```python id="ex2"
3
```

### Explanation

* Boat 1 → `(1, 2)`
* Boat 2 → `(2)`
* Boat 3 → `(3)`

So, the minimum boats required = **3**

---

##Approach (Greedy + Two Pointers)

###Idea (Simple English)

* Sort the array first.
* Use two pointers:

  * `left` → lightest person
  * `right` → heaviest person

### Why this works?

* The heaviest person must go on a boat.
* Try to pair them with the lightest person.
* If they fit together, send both.
* Otherwise, send the heaviest person alone.

This greedy choice always gives the optimal answer.

---

##Algorithm Steps

1. Sort the array.
2. Initialize:

   * `left = 0`
   * `right = len(people) - 1`
   * `boats = 0`
3. While `left <= right`:

   * If `people[left] + people[right] <= limit`:

     * Pair them together
     * Move `left` forward
   * Always move `right` backward (heaviest person boards)
   * Increment boat count
4. Return `boats`

---

##Dry Run

### Input

```python id="dr1"
people = [3, 2, 2, 1]
limit = 3
```

### After Sorting

```python id="dr2"
people = [1, 2, 2, 3]
```

| Step | left | right | Pair  | Action                   | Boats |
| ---- | ---- | ----- | ----- | ------------------------ | ----- |
| 1    | 0    | 3     | (1,3) | Too heavy → 3 goes alone | 1     |
| 2    | 0    | 2     | (1,2) | Pair together            | 2     |
| 3    | 1    | 1     | (2)   | Goes alone               | 3     |

---

##Final Answer

```python id="ans1"
3
```

---

##Python Code

```python id="code1"
from typing import List

class Solution:
    def numRescueBoats(self, people: List[int], limit: int) -> int:
        people.sort()
        left, right = 0, len(people) - 1
        boats = 0

        while left <= right:
            if people[left] + people[right] <= limit:
                left += 1

            right -= 1
            boats += 1

        return boats
```

---

##Time and Space Complexity

* **Time Complexity:** `O(n log n)`

  * Sorting takes `O(n log n)`
  * Two-pointer traversal takes `O(n)`

* **Space Complexity:** `O(1)`

  * No extra space used

---

##Key Insight

* Always place the heaviest person first.
* Pair them with the lightest person whenever possible.
* This greedy strategy minimizes the number of boats.

---

##Tags

* Array
* Two Pointers
* Greedy
* Sorting

---

##Practice Link

* LeetCode: https://leetcode.com/problems/boats-to-save-people/

---

##Author

**Gokulakrishnan G**
Aspiring Software Engineer | Python & DSA Enthusiast 
