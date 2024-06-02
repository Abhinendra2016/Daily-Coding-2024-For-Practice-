# Problem 344: Reverse String

Write a function that reverses a string. The input string is given as an array of characters `s`.

You must do this by modifying the input array in-place with O(1) extra memory.

## Example 1

**Input:** `s = ["h","e","l","l","o"]`

**Output:** `["o","l","l","e","h"]`

## Example 2

**Input:** `s = ["H","a","n","n","a","h"]`

**Output:** `["h","a","n","n","a","H"]`

## Constraints

- `1 <= s.length <= 10^5`
- `s[i]` is a printable ASCII character.

## Solution

```python
class Solution:
  def reverseString(self, s: List[str]) -> None:
    l = 0
    r = len(s) - 1

    while l < r:
      s[l], s[r] = s[r], s[l]
      l += 1
      r -= 1
```
<h2>Time Complexity</h2>

The time complexity of this solution is O(n), where n is the length of the input list s. This is because we are using a single while loop that iterates through half of the list.<br>

<h2>Space Complexity</h2>

The space complexity of this solution is O(1). This is because we are reversing the string in place and not using any additional data structures that grow with the input size.<br>

<h2>Explanation</h2>

The provided solution uses a two-pointer technique to reverse the input string in place. Here’s a step-by-step explanation of the process:<br>

Initialize Pointers:<br>

l is initialized to the start of the list (0).<br>
r is initialized to the end of the list (len(s) - 1).<br>
Swap Elements:<br>

A while loop runs as long as l is less than r.<br>
Inside the loop, the elements at indices l and r are swapped.<br>
After swapping, the l pointer is incremented by 1 and the r pointer is decremented by 1.<br>
Termination:<br>

The loop terminates when l is no longer less than r, which means that the entire list has been reversed.<br>
This approach ensures that the reversal is done in-place with O(1) extra space, meeting the problem's constraints.<br>