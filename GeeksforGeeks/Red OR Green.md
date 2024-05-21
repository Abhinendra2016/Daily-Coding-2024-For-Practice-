# Red OR Green

Given a string of length N, made up of only uppercase characters 'R' and 'G', where 'R' stands for Red and 'G' stands for Green. Find out the minimum number of characters you need to change to make the whole string of the same color.

## Example 1:

Input:  
N=5  
S="RGRGR"  
Output:  
2  
Explanation:  
We need to change only the 2nd and 4th (1-index based) characters to 'R', so that the whole string becomes the same color.

## Example 2:

Input:  
N=7  
S="GGGGGGR"  
Output:  
1  
Explanation:  
We need to change only the last character to 'G' to make the string same-colored.

## Solution

```python
class Solution:
    @staticmethod
    def RedOrGreen(N, S):
        a = S.count('R')
        b = S.count('G')
        return N - max(a, b)
```