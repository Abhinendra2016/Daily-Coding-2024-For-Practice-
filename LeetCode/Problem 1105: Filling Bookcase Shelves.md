# Problem 1105: Filling Bookcase Shelves

You are given an array `books` where `books[i] = [thickness_i, height_i]` indicates the thickness and height of the ith book. You are also given an integer `shelfWidth`.

We want to place these books in order onto bookcase shelves that have a total width `shelfWidth`.

We choose some of the books to place on this shelf such that the sum of their thickness is less than or equal to `shelfWidth`, then build another level of the shelf of the bookcase so that the total height of the bookcase has increased by the maximum height of the books we just put down. We repeat this process until there are no more books to place.

Note that at each step of the above process, the order of the books we place is the same order as the given sequence of books.

For example, if we have an ordered list of 5 books, we might place the first and second book onto the first shelf, the third book on the second shelf, and the fourth and fifth book on the last shelf.

Return the minimum possible height that the total bookshelf can be after placing shelves in this manner.

## Example 1


Input: books = [[1,1],[2,3],[2,3],[1,1],[1,1],[1,1],[1,2]], shelfWidth = 4
Output: 6
Explanation:
The sum of the heights of the 3 shelves is 1 + 3 + 2 = 6.
Notice that book number 2 does not have to be on the first shelf.

## Example 2
Input: books = [[1,3],[2,4],[3,2]], shelfWidth = 6
Output: 4

# Constraints

1 <= books.length <= 1000
1 <= thickness_i <= shelfWidth <= 1000
1 <= height_i <= 1000

```python
class Solution:
  def minHeightShelves(self, books: List[List[int]], shelfWidth: int) -> int:
    # dp[i] := the minimum height to place the first i books
    dp = [0] + [math.inf] * len(books)

    for i in range(len(books)):
      sumThickness = 0
      maxHeight = 0
      # Place books[j..i] on a new shelf.
      for j in range(i, -1, -1):
        thickness, height = books[j]
        sumThickness += thickness
        if sumThickness > shelfWidth:
          break
        maxHeight = max(maxHeight, height)
        dp[i + 1] = min(dp[i + 1], dp[j] + maxHeight)

    return dp[-1]
```
<h2>Time Complexity</h2>

The time complexity of the solution is O(n^2), where n is the number of books. This is because for each book, we might look back at all the previous books to decide whether to place it on the same shelf or start a new shelf.<br>

<h2>Space Complexity</h2>

The space complexity of the solution is O(n), where n is the number of books. This is due to the use of the dp array, which stores the minimum height for placing the first i books.<br>

<h2>Explanation</h2>

The problem is solved using dynamic programming. The dp array is used to store the minimum height to place the first i books. We iterate over each book and consider placing it on the current shelf or starting a new shelf. The decision is based on whether the total thickness of the books on the current shelf exceeds shelfWidth or not. If it does, we start a new shelf and update the height accordingly. The result is the minimum height of the bookshelf after placing all the books.