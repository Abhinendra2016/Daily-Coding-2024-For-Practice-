# Reverse Words in a Given String

Given a string `S`, reverse the string without reversing its individual words. Words are separated by dots.

### Example 1:

**Input:**  
S = `i.like.this.program.very.much`  
**Output:**  
`much.very.program.this.like.i`  
**Explanation:**  
After reversing the whole string (not individual words), the input string becomes `much.very.program.this.like.i`.

### Example 2:

**Input:**  
S = `pqr.mno`  
**Output:**  
`mno.pqr`  
**Explanation:**  
After reversing the whole string, the input string becomes `mno.pqr`.

### Solution:

```python
class Solution:
    def reverseWords(self, S):
        return ".".join(S.split('.')[::-1])
```
