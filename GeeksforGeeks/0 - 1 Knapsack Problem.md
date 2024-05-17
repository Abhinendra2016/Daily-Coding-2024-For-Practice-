# 0-1 Knapsack Problem

## Problem Description

You are given weights and values of `N` items and a knapsack of capacity `W`. The goal is to maximize the total value in the knapsack by selecting items such that their total weight does not exceed `W`. Each item can either be included in its entirety or excluded (0-1 property).

## Example 1 


Input:
N = 3
W = 4
values[] = {1,2,3}
weight[] = {4,5,1}
Output: 3
Explanation: Choose the last item that weighs 1 unit and holds a value of 3. 

## Example 2

Input:
N = 3
W = 3
values[] = {1,2,3}
weight[] = {4,5,6}
Output: 0
Explanation: Every item has a weight exceeding the knapsack's capacity (3)

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


