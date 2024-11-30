# Problem 2097: Valid Arrangement of Pairs
You are given a 0-indexed 2D integer array `pairs` where `pairs[i] = [starti, endi]`.  
An arrangement of pairs is valid if for every index `i` where `1 <= i < pairs.length`, we have `endi-1 == starti`.

Your task is to **return any valid arrangement of pairs**.

**Note**: The inputs will be generated such that there exists a valid arrangement of pairs.

---

### Example 1

**Input**:  
pairs = [[5,1],[4,5],[11,9],[9,4]]

**Output**:  
[[11,9],[9,4],[4,5],[5,1]]

**Explanation**:  
This is a valid arrangement since:
- `end0 = 9 == 9 = start1`
- `end1 = 4 == 4 = start2`
- `end2 = 5 == 5 = start3`

---

### Example 2

**Input**:  
pairs = [[1,3],[3,2],[2,1]]

**Output**:  
[[1,3],[3,2],[2,1]]


**Explanation**:  
This is a valid arrangement since:
- `end0 = 3 == 3 = start1`
- `end1 = 2 == 2 = start2`

Other valid arrangements:
- `[[2,1],[1,3],[3,2]]`
- `[[3,2],[2,1],[1,3]]`

---

### Example 3

**Input**:  
pairs = [[1,2],[1,3],[2,1]]

**Output**:  
[[1,2],[2,1],[1,3]]

**Explanation**:  
This is a valid arrangement since:
- `end0 = 2 == 2 = start1`
- `end1 = 1 == 1 = start2`

---

## Constraints

- `1 <= pairs.length <= 10^5`
- `pairs[i].length == 2`
- `0 <= starti, endi <= 10^9`
- `starti != endi`
- No two pairs are exactly the same.
- There exists a valid arrangement of pairs.

---

## Solution

### Algorithm Overview

This problem can be solved using **Eulerian path** concepts from graph theory. An **Eulerian path** exists in a directed graph if:
1. All nodes with edges have their in-degrees and out-degrees balanced, except for at most one node with `out-degree - in-degree = 1` (start node) and one node with `in-degree - out-degree = 1` (end node).

#### Steps:
1. **Build the Graph**: Construct a directed graph where each pair `[start, end]` is an edge. Use a dictionary to maintain adjacency lists.
2. **Identify Start Node**:
   - If a node exists with `out-degree - in-degree = 1`, start from this node.
   - Otherwise, start from any node in the graph.
3. **Eulerian Path**: Perform a depth-first search (DFS) to construct the valid path.
4. **Reverse the Path**: The path constructed during DFS will be in reverse order, so reverse it before returning.

---

### Implementation

```python
import collections

class Solution:
    def validArrangement(self, pairs: list[list[int]]) -> list[list[int]]:
        ans = []
        graph = collections.defaultdict(list)
        outDegree = collections.Counter()
        inDegrees = collections.Counter()

        # Build the graph and calculate in-degrees and out-degrees
        for start, end in pairs:
            graph[start].append(end)
            outDegree[start] += 1
            inDegrees[end] += 1

        # Find the starting node
        def getStartNode() -> int:
            for u in graph.keys():
                if outDegree[u] - inDegrees[u] == 1:
                    return u
            return pairs[0][0]  

        # Perform Eulerian path traversal
        def euler(u: int) -> None:
            stack = graph[u]
            while stack:
                v = stack.pop()
                euler(v)
                ans.append([u, v])

        # Find Eulerian path and return the result
        euler(getStartNode())
        return ans[::-1]
```