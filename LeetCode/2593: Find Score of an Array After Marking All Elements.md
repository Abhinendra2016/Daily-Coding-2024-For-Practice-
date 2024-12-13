# Problem 2593: Find Score of an Array After Marking All Elements

## Problem Description
You are given an array `nums` consisting of positive integers.

Starting with `score = 0`, apply the following algorithm:

1. Choose the smallest integer of the array that is not marked. If there is a tie, choose the one with the smallest index.
2. Add the value of the chosen integer to `score`.
3. Mark the chosen element and its two adjacent elements if they exist.
4. Repeat until all the array elements are marked.

Return the score you get after applying the above algorithm.

### Example 1:
**Input:**
nums = [2,1,3,4,5,2]
**Output:**
```
7
```
**Explanation:**
We mark the elements as follows:
- `1` is the smallest unmarked element, so we mark it and its two adjacent elements: `[2,1,3,4,5,2]`.
- `2` is the smallest unmarked element, so we mark it and its left adjacent element: `[2,1,3,4,5,2]`.
- `4` is the only remaining unmarked element, so we mark it: `[2,1,3,4,5,2]`.

Our score is `1 + 2 + 4 = 7`.

### Example 2:
**Input:**

nums = [2,3,5,1,3,2]

**Output:**
5

**Explanation:**
We mark the elements as follows:
- `1` is the smallest unmarked element, so we mark it and its two adjacent elements: `[2,3,5,1,3,2]`.
- `2` is the smallest unmarked element, since there are two of them, we choose the left-most one, so we mark the one at index `0` and its right adjacent element: `[2,3,5,1,3,2]`.
- `2` is the only remaining unmarked element, so we mark it: `[2,3,5,1,3,2]`.

Our score is `1 + 2 + 2 = 5`.

### Constraints:
- `1 <= nums.length <= 10^5`
- `1 <= nums[i] <= 10^6`

---

## Solution

### Approach:
1. Create a sorted list of tuples containing each element and its index.
2. Use a `set` to keep track of marked indices.
3. For each element in the sorted list:
   - Skip the element if its index is already marked.
   - Mark the current index and its adjacent indices.
   - Add the value of the element to the score.
4. Return the final score.

### Python Code:
```python
class Solution:
  def findScore(self, nums: list[int]) -> int:
    ans = 0
    seen = set()
    for num, i in sorted([(num, i) for i, num in enumerate(nums)]):
      if i in seen:
        continue
      seen.add(i - 1)
      seen.add(i + 1)
      seen.add(i)
      ans += num
    return ans
```

---

## Time Complexity
- Sorting the array takes **O(n log n)**.
- Iterating over the sorted array takes **O(n)**.

Overall complexity: **O(n log n)**

## Space Complexity
- The `seen` set uses **O(n)** space.
- The sorted array uses **O(n)** space.

Overall space complexity: **O(n)**

---

## Explanation
- **Step 1:** Sort the array based on values. This ensures that the smallest values are processed first.
- **Step 2:** Use a set to mark elements and their adjacent indices as processed.
- **Step 3:** For each unmarked element, add its value to the score and mark it along with its neighbors.
- **Step 4:** Return the total score after processing all elements.

---

## Example Walkthrough
### Example 1:
**Input:**

nums = [2,1,3,4,5,2]

**Execution:**
1. Sorted list with indices: `[(1, 1), (2, 0), (2, 5), (3, 2), (4, 3), (5, 4)]`
2. Initialize `score = 0` and `seen = {}`.
3. Process each element:
   - Choose `1` at index `1`, add to score, mark `0, 1, 2`. `score = 1`.
   - Choose `2` at index `0`, skip (already marked).
   - Choose `2` at index `5`, add to score, mark `4, 5`. `score = 3`.
   - Choose `3` at index `2`, skip (already marked).
   - Choose `4` at index `3`, add to score, mark `3`. `score = 7`.

**Output:**

7
