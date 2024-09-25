# Problem 2416: Sum of Prefix Scores of Strings

You are given an array `words` of size `n` consisting of non-empty strings.

We define the **score** of a string `word` as the number of strings `words[i]` such that `word` is a prefix of `words[i]`.

For example, if `words = ["a", "ab", "abc", "cab"]`, then the score of `"ab"` is `2`, since `"ab"` is a prefix of both `"ab"` and `"abc"`.

Return an array `answer` of size `n` where `answer[i]` is the sum of scores of every non-empty prefix of `words[i]`.

**Note**: A string is considered a prefix of itself.

### Example 1

**Input**:  
`words = ["abc","ab","bc","b"]`

**Output**:  
`[5, 4, 3, 2]`

**Explanation**: 
- `"abc"` has 3 prefixes: `"a"`, `"ab"`, and `"abc"`.
  - There are 2 strings with the prefix `"a"`, 2 strings with the prefix `"ab"`, and 1 string with the prefix `"abc"`.  
  - The total score for `"abc"` is `2 + 2 + 1 = 5`.
- `"ab"` has 2 prefixes: `"a"` and `"ab"`.
  - There are 2 strings with the prefix `"a"` and 2 strings with the prefix `"ab"`.  
  - The total score for `"ab"` is `2 + 2 = 4`.
- `"bc"` has 2 prefixes: `"b"` and `"bc"`.
  - There are 2 strings with the prefix `"b"`, and 1 string with the prefix `"bc"`.  
  - The total score for `"bc"` is `2 + 1 = 3`.
- `"b"` has 1 prefix: `"b"`.
  - There are 2 strings with the prefix `"b"`.  
  - The total score for `"b"` is `2`.

### Example 2

**Input**:  
`words = ["abcd"]`

**Output**:  
`[4]`

**Explanation**:  
- `"abcd"` has 4 prefixes: `"a"`, `"ab"`, `"abc"`, and `"abcd"`.  
- Each prefix has a score of `1`, so the total is `1 + 1 + 1 + 1 = 4`.

### Constraints

- `1 <= words.length <= 1000`
- `1 <= words[i].length <= 1000`
- `words[i]` consists of lowercase English letters.

## Solution

The problem can be efficiently solved using a **Trie** (prefix tree). Here's the approach:

### Approach:

1. **Trie Data Structure**: 
   - We use a Trie to store the words from the `words` array. Each node in the Trie will also store a `count` of how many times that prefix has appeared across all words.

2. **Insert Words into Trie**: 
   - For each word in `words`, we insert it into the Trie, and at each node corresponding to a character in the word, we increment the count for that prefix.

3. **Calculate Scores**: 
   - For each word in `words`, we traverse the Trie from the root to the end of the word, summing the counts of each prefix along the way to get the score for the word.


```python
class TrieNode:
  def __init__(self):
    self.children: dict[str, TrieNode] = {}
    self.count = 0

class Solution:
  def sumPrefixScores(self, words: list[str]) -> list[int]:
    root = TrieNode()

    def insert(word: str) -> None:
      node: TrieNode = root
      for c in word:
        node = node.children.setdefault(c, TrieNode())
        node.count += 1

    # Insert all words into the Trie
    for word in words:
      insert(word)

    def getScore(word: str) -> int:
      node: TrieNode = root
      score = 0
      for c in word:
        node = node.children[c]
        score += node.count
      return score

    # Calculate and return the scores for all words
    return [getScore(word) for word in words]
```
<h2>Time Complexity</h2>

Insertion into Trie: Inserting a word into the Trie takes O(L) time, where L is the length of the word.
Score Calculation: For each word, calculating the score also takes O(L) time.
The total time complexity is O(n * L), where n is the number of words and L is the maximum length of a word. Given the constraints, this approach is efficient.<br>
<h2>Space Complexity</h2>

The space complexity is O(T), where T is the total number of characters across all words. This space is required to store the Trie nodes.<br>