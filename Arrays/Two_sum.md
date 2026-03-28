# Two Sum (LeetCode - Easy)

## Problem Statement

Given an array of integers `nums` and an integer `target`, return the indices of the two numbers such that they add up to the target.

- Each input has exactly one solution  
- You cannot use the same element twice  
- Return the answer in any order  

---

## Approach: Hashing (Optimal Solution)

### Idea

Instead of checking all pairs (which takes O(n²)), we use a **hashmap (dictionary)** to store numbers we have already seen.

For each element, we check whether the required complement exists.

---

### Key Insight

For any number `num`, we check:

target - num

If this value already exists in the hashmap → we found the solution.

---

## Step-by-Step Algorithm

1. Create an empty hashmap `seen`
2. Traverse the array using a loop
3. For each element:
   - Calculate `complement = target - num`
   - If `complement` exists in hashmap → return indices
   - Else → store current number with index in hashmap

---

## Example Walkthrough

Input:  
nums = [2, 7, 11, 15], target = 9  

Step 1:  
i = 0, num = 2  
complement = 9 - 2 = 7  
Not found → store {2: 0}  

Step 2:  
i = 1, num = 7  
complement = 9 - 7 = 2  
Found in hashmap → Answer = [0, 1]  

---

## Python Code

```python
def twoSum(nums, target):
    seen = {}  # hashmap to store value:index

    for i, num in enumerate(nums):
        complement = target - num

        if complement in seen:
            return [seen[complement], i]

        seen[num] = i
