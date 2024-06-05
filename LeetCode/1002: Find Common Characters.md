# Problem 1002: Find Common Characters

Given a string array `words`, return an array of all characters that show up in all strings within the `words` (including duplicates). You may return the answer in any order.

## Example 1

**Input:** words = ["bella", "label", "roller"]

**Output:** ["e", "l", "l"]

## Example 2

**Input:** words = ["cool", "lock", "cook"]

**Output:** ["c", "o"]

## Constraints

- 1 <= words.length <= 100
- 1 <= words[i].length <= 100
- words[i] consists of lowercase English letters.

## Solution

```python
from typing import List
from collections import Counter

class Solution:
    def commonChars(self, A: List[str]) -> List[str]:
        if not A:
            return []
        # Initialize with the first word's character counts
        commonCount = Counter(A[0])
        # Update commonCount with the minimum frequency counts
        for a in A[1:]:
            commonCount &= Counter(a)
        # Convert the counter to the result list
        ans = []
        for char, count in commonCount.items():
            ans.extend([char] * count)
        
        return ans
```
<h2>Time Complexity</h2>
The time complexity of the solution is ON • M), where N is the number of words and M is the length of the longest word.<br>
This is because we iterate through each character in each word to count their frequencies.<br>
<h2>Space Complexity</h2>
The space complexity of the solution is O (1). Although we use a Counter to store the character counts, the size of this Counter is limited to 26 lowercase English letters, which is a constant.<br>
<h2>Explanation</h2>
1. Initialization: We start by initializing a 'Counter with the character counts from the first word in the list. This will serve as our reference for the minimum counts of each character.<br>
2. Update Common Counts: We then iterate through the rest of the words in the list. For each word, we create a new 'Counter' and use the bitwise AND operator (*&=*) to update our<br>
'commonCount. This operation ensures that we only keep the minimum counts of each character across all words.<br>
3. Result Construction: Finally, we construct the result list by iterating through the items in<br>
"commonCount'. For each character and its count, we extend the result list with the character repeated count times.<br>