# Problem 1813: Sentence Similarity III
You are given two strings `sentence1` and `sentence2`, each representing a sentence composed of words. A sentence is a list of words that are separated by a single space with no leading or trailing spaces. Each word consists of only uppercase and lowercase English characters.

Two sentences, `sentence1` and `sentence2`, are considered similar if it is possible to insert an arbitrary sentence (possibly empty) inside one of these sentences such that the two sentences become equal. The inserted sentence must be separated from the existing words by spaces.

### Example 1:

**Input:**  
`sentence1 = "My name is Haley"`  
`sentence2 = "My Haley"`  
**Output:** `true`  
**Explanation:**  
`sentence2` can be turned into `sentence1` by inserting `"name is"` between `"My"` and `"Haley"`.

### Example 2:

**Input:**  
`sentence1 = "of"`  
`sentence2 = "A lot of words"`  
**Output:** `false`  
**Explanation:**  
No single sentence can be inserted inside one of the sentences to make it equal to the other.

### Example 3:

**Input:**  
`sentence1 = "Eating right now"`  
`sentence2 = "Eating"`  
**Output:** `true`  
**Explanation:**  
`sentence2` can be turned into `sentence1` by inserting `"right now"` at the end of the sentence.

### Constraints:

- `1 <= sentence1.length, sentence2.length <= 100`
- `sentence1` and `sentence2` consist of lowercase and uppercase English letters and spaces.
- The words in `sentence1` and `sentence2` are separated by a single space.

## Solution

```python
class Solution:
    def areSentencesSimilar(self, sentence1: str, sentence2: str) -> bool:
        if len(sentence1) == len(sentence2):
            return sentence1 == sentence2

        words1 = sentence1.split()
        words2 = sentence2.split()
        m, n = map(len, (words1, words2))

        if m > n:
            return self.areSentencesSimilar(sentence2, sentence1)

        i = 0
        # Match the words from the start
        while i < m and words1[i] == words2[i]:
            i += 1

        # Match the words from the end
        while i < m and words1[i] == words2[i + n - m]:
            i += 1

        return i == m
```
<h2>Time Complexity</h2>

O(min(m, n)): The solution compares the two sentences word by word. The time complexity is determined by the smaller of the two sentence lengths.<br>
<h2>Space Complexity</h2>

O(m + n): The space complexity comes from storing the split versions of the two sentences, where m and n are the number of words in sentence1 and sentence2, respectively.
<h2>Explanation</h2>

First, check if both sentences are of the same length. If yes, compare them directly.
Split both sentences into words.
Ensure that the shorter sentence is compared against the longer one by swapping if necessary.
Compare words from both the start and end of the sentences:
Start from the beginning of both sentences and find the matching words.
Then, match words from the end of both sentences.
Return true if all words in the shorter sentence match a portion of the longer sentence.
<h2>Conclusion</h2>

This approach ensures that we can determine whether one sentence can be transformed into the other by inserting an arbitrary sentence. The solution efficiently handles the comparison by leveraging both the start and end matches of the sentence.