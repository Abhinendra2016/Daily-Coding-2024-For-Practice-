# Generate Binary Numbers

Your friend Ninja has been learning about binary numbers lately. In order to understand binary numbers with perfection, Ninja asks you to generate a list of binary numbers from 1 to ‘N’, which he can use later for reference.

For every integer Ninja gives, your task is to generate all the binary numbers from 1 to ‘N’.

### Example

Consider N = 5,  
All the binary numbers from 1 to 5 are: 1, 10, 11, 100, 101.

## Solution

```python
def decimal_to_binary(x):
    if x < 2:
        return x
    return decimal_to_binary(x // 2) * 10 + (x % 2)

def generateBinaryNumbers(n):
    ans = []
    for i in range(1, n + 1):
        ans.append(decimal_to_binary(i))
    return ans
```
<h2>Time Complexity</h2>
The time complexity of this solution is On * log n), where n is the number of elements from 1 to N.<br>
This is because converting a decimal number to binary takes O(log n) time, and we are doing this for each number from 1 to N.<br>
<h2>Space Complexity</h2>
The space complexity of this solution is O(n * log n). This is due to the space required to store the binary <br>representations of numbers from 1 to N, where each binary number can have up to log n bits.<br>
<h2>Explanation</h2>
1. decimal_to_binary(x): This function converts a decimal number x to its binary representation using recursion. If x is less than 2, it returns *x* itself. Otherwise, it recursively calls itself with<br>
•x // 2' and concatenates the remainder of x* when divided by 2.<br>
2. generateBinaryNumbers(n): This function generates a list of binary numbers from 1 to 'n*. It initializes an empty list 'ans*. For each number "i from 1 to n', it converts 'i' to its binary representation using decimal_ to_binary(i) and <br>appends it to ans*. Finally, it returns the list 'ans'.
