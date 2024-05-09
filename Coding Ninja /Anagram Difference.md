# Problem: Arrange Consonants and Vowels

Given a singly linked list having n nodes containing English alphabets ('a'-'z'). Rearrange the linked list in such a way that all the vowels come before the consonants while maintaining the order of their arrival. 

## Example

Input:
n = 9
linked list: a -> b -> c -> d -> e -> f -> g -> h -> i 
Output: 
a -> e -> i -> b -> c -> d -> f -> g -> h
Explanation: 
After rearranging the input linked list according to the condition, the resultant linked list will be as shown in the output.

Input:
n = 8
linked list: a -> b -> a -> b -> d -> e -> e -> d 
Output: 
a -> a -> e -> e -> b -> b -> d -> d
Explanation: 
After rearranging the input linked list according to the condition, the resultant linked list will be as shown in the output.

## Solution

```python
class Solution:
    # Function to reverse a linked list.
    def arrangeCV(self, head):
        # Separate vowels and consonants
        vowels = []
        consonants = []
        current = head
        while current:
            if current.data in "aeiouAEIOU":
                vowels.append(current.data)
            else:
                consonants.append(current.data)
            current = current.next
        
        # Merge vowels and consonants
        result = vowels + consonants
        
        # Create a new linked list with the arranged characters
        dummy = Node(0)
        current = dummy
        for char in result:
            current.next = Node(char)
            current = current.next
        
        return dummy.next
```
<h2>Time Complexity</h2>

The time complexity of this solution is O(n), where n is the number of nodes in the linked list. This is because we iterate through the linked list once to separate vowels and consonants, and then iterate through the result to create a new linked list.

<h2>Space Complexity</h2>

The space complexity of this solution is O(n), where n is the number of nodes in the linked list. This is because we use two lists (vowels and consonants) to store the separated characters, each of which can have up to n elements in the worst case.

<h2>Explanation</h2>

We iterate through the linked list to separate vowels and consonants into two separate lists.<br>
We then merge the two lists to create a new list where vowels come before consonants.<br>
Finally, we create a new linked list using the characters in the merged list and return its head.