# Problem 2490: Circular Sentence

A sentence is defined as a list of words separated by a single space with no leading or trailing spaces. In this problem, the goal is to determine if a sentence is "circular." 

A **circular sentence** is a sentence in which:
- The last character of each word matches the first character of the next word.
- The last character of the last word matches the first character of the first word.

For instance:
- "leetcode exercises sound delightful" is circular.
- "Leetcode is cool" is not circular.

### Examples
**Example 1**
- **Input:** `"leetcode exercises sound delightful"`
- **Output:** `true`
- **Explanation:** The sentence's words are `["leetcode", "exercises", "sound", "delightful"]`. Each word’s last character matches the first character of the following word, and the last character of the last word matches the first character of the first word.

**Example 2**
- **Input:** `"eetcode"`
- **Output:** `true`
- **Explanation:** The word `"eetcode"` starts and ends with the same character.

**Example 3**
- **Input:** `"Leetcode is cool"`
- **Output:** `false`
- **Explanation:** The last character of `"Leetcode"` does not match the first character of `"is"`.

### Constraints
- `1 <= sentence.length <= 500`
- The sentence consists of only uppercase and lowercase English letters and spaces.
- Each word in the sentence is separated by a single space.
- There are no leading or trailing spaces.

## Solution

The solution is implemented as follows:

```python
class Solution:
    def isCircularSentence(self, sentence: str) -> bool:
        for i, c in enumerate(sentence):
            if c == ' ' and sentence[i - 1] != sentence[i + 1]:
                return False
        return sentence[0] == sentence[-1]
```
<h2>Explanation</h2>
Loop Through Characters: The function loops through each character in sentence to check if any space character separates two words where the last character of the preceding word does not match the first character of the following word.
Check Circular Condition: Finally, it verifies that the first character of the first word matches the last character of the last word to confirm circularity.<br>


<h2>Time Complexity:</h2> <br>
O(n), where n is the length of the sentence. The function iterates over each character once.

<h2>Space Complexity:</h2><br>
 O(1), as no additional data structures are used.

Edge Cases
Single word where the first and last characters are the same, e.g., "eetcode" (Expected output: true).
A sentence with mixed case letters, where case sensitivity could affect the outcome, e.g., "Leetcode is cool" (Expected output: false).
Circularity at the sentence level but not within the words, e.g., "a aa a" (Expected output: true).