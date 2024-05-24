# Problem: Remove Vowels

You are given a string STR of length N. Your task is to remove all the vowels present in that string and print the modified string.<br>

English alphabets ‘a’, ‘e’, ‘i’, ‘o’, ‘u’ are termed as vowels. All other alphabets are called consonants.<br>

Note: You have to only remove vowels from the string. There will be no change in the relative position of all other alphabets.

## Examples:
**Example 1:**
**Input:** 'CodeGeek'  
**Output:** 'CdGk'

**Example 2:**
**Input:** 'Odinson'  
**Output:** 'dnsn'

## Solution

```python
def removeVowels(inputString):
    vowels = "aeiouAEIOU"
    result = ""

    for char in inputString:
        if char not in vowels:
            result += char

    return result
```
<h2>Time Complexity</h2>
The time complexity of this solution is O(N), where N is the length of the input string. This is because we iterate through each character of the string once.<br>
<h2>Space Complexity</h2>
The space complexity of this solution is O(N), where N is the length of the input string. This is because the result string can be at most as long as the input string if there are no vowels.<br>
<h2>Explanation</h2>
The solution iterates through each character of the input string and checks if it is a vowel:<br>
- If the character is not a vowel, it is added to the result string.<br>
- If the character is a vowel, it is skipped.<br>
- Finally, the result string, which contains no vowels, is returned.<br>
