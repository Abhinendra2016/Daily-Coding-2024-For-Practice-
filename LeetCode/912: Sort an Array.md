# Problem 912: Sort an Array

## Problem Description

Given an array of integers `nums`, sort the array in ascending order and return it.

You must solve the problem without using any built-in functions in `O(nlog(n))` time complexity and with the smallest space complexity possible.

## Examples

**Example 1:**

- **Input:** `nums = [5, 2, 3, 1]`
- **Output:** `[1, 2, 3, 5]`
- **Explanation:** After sorting the array, the positions of some numbers are not changed (for example, 2 and 3), while the positions of other numbers are changed (for example, 1 and 5).

**Example 2:**

- **Input:** `nums = [5, 1, 1, 2, 0, 0]`
- **Output:** `[0, 0, 1, 1, 2, 5]`
- **Explanation:** Note that the values of nums are not necessarily unique.

## Constraints

- `1 <= nums.length <= 5 * 10^4`
- `-5 * 10^4 <= nums[i] <= 5 * 10^4`

## Solution

```python
class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        def mergeSort(A: List[int], l: int, r: int) -> None:
            if l >= r:
                return

            def merge(A: List[int], l: int, m: int, r: int) -> None:
                sorted = [0] * (r - l + 1)
                k = 0  # sorted's index
                i = l  # left's index
                j = m + 1  # right's index

                while i <= m and j <= r:
                    if A[i] < A[j]:
                        sorted[k] = A[i]
                        k += 1
                        i += 1
                    else:
                        sorted[k] = A[j]
                        k += 1
                        j += 1

                # Put the possible remaining left part into the sorted array.
                while i <= m:
                    sorted[k] = A[i]
                    k += 1
                    i += 1

                # Put the possible remaining right part into the sorted array.
                while j <= r:
                    sorted[k] = A[j]
                    k += 1
                    j += 1

                A[l:l + len(sorted)] = sorted

            m = (l + r) // 2
            mergeSort(A, l, m)
            mergeSort(A, m + 1, r)
            merge(A, l, m, r)

        mergeSort(nums, 0, len(nums) - 1)
        return nums
```

<h2>Time Complexity</h2>

The time complexity of the solution is O(nlog(n)) due to the merge sort algorithm used.<br>

<h2>Space Complexity</h2>

The space complexity of the solution is O(n) due to the auxiliary space needed for the temporary sorted array used in the merge process.<br>

<h2>Explanation</h2>

This solution uses the merge sort algorithm, which is a divide-and-conquer algorithm that works as follows:<br>

Divide: The array is recursively divided into two halves until each half contains a single element or is empty.<br>
Conquer: The halves are recursively sorted.<br>
Combine: The sorted halves are merged together to form a sorted array.<br>
The merge sort algorithm is used because it guarantees a time complexity of O(nlog(n)) and is stable, which means it maintains the relative order of equal elements.<br>
