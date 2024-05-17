# Frequency In A Sorted Array

## Problem Statement

You are given a sorted array 'ARR' and a number 'X'. Your task is to count the number of occurrences of 'X' in 'ARR'.

### Note:
1. If 'X' is not found in the array, return 0.
2. The given array is sorted in non-decreasing order.

## Solution

```python
def firstOcc(arr, x):
    """
    Function to find the first occurrence of 'x' in 'arr'.
    :param arr: List of integers.
    :param x: Integer to find.
    :return: Index of the first occurrence of 'x', or -1 if not found.
    """
    s, e = 0, len(arr) - 1
    ans = -1
    
    while s <= e:
        mid = s + (e - s) // 2
        
        if arr[mid] == x:
            ans = mid
            e = mid - 1  # Continue to search in the left half
        elif arr[mid] < x:
            s = mid + 1  # Continue to search in the right half
        else:
            e = mid - 1  # Continue to search in the left half
            
    return ans

def lastOcc(arr, x):
    """
    Function to find the last occurrence of 'x' in 'arr'.
    :param arr: List of integers.
    :param x: Integer to find.
    :return: Index of the last occurrence of 'x', or -1 if not found.
    """
    s, e = 0, len(arr) - 1
    ans = -1
    
    while s <= e:
        mid = s + (e - s) // 2
        
        if arr[mid] == x:
            ans = mid
            s = mid + 1  # Continue to search in the right half
        elif arr[mid] < x:
            s = mid + 1  # Continue to search in the right half
        else:
            e = mid - 1  # Continue to search in the left half
            
    return ans

def countOccurrences(arr, x):
    """
    Function to count the total number of occurrences of 'x' in 'arr'.
    :param arr: List of integers.
    :param x: Integer to count.
    :return: Count of occurrences of 'x'.
    """
    fOcc = firstOcc(arr, x)
    lOcc = lastOcc(arr, x)
    
    if fOcc == -1 or lOcc == -1:
        return 0
    
    return (lOcc + 1) - fOcc
```
<h2>Time Complexity</h2>
The time complexity of this solution is O (log n), where n is the length of the array "arr'.<br> This complexity arises from performing binary search twice (once for the first occurrence and once for the last occurrence).
<h2>Space Complexity</h2>
The space complexity is O (1), as the solution uses a constant amount of extra space.<br>