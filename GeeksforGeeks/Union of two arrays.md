# Problem: Union of Two Arrays

Given two arrays a[] and b[] of size n and m respectively. The task is to find the number of elements in the union between these two arrays.

Union of the two arrays can be defined as the set containing distinct elements from both the arrays. If there are repetitions, then only one occurrence of the element should be counted in the union.

## Example

Input:
5 3
1 2 3 4 5
1 2 3
Output: 
5
Explanation: 
1, 2, 3, 4, and 5 are the elements which are present in the union set of both arrays. So, the count is 5.

## Solution

```python
class Solution:    
    # Function to return the count of number of elements in the union of two arrays.
    def doUnion(self, a, n, b, m):
        a = set(a)
        b = set(b)
        c = a.union(b)
        return len(c)
```
<h2>Explanation</h2>

We convert both arrays a and b into sets to remove duplicates.<br>
Then, we find the union of the two sets a and b using the union method, which returns a new set containing all distinct elements from both sets.<br>
Finally, we return the length of the union set, which gives us the count of the number of elements in the union of the two arrays.<br>