# Problem 3243: Shortest Distance After Road Addition Queries I

## Problem Description

You are given an integer `n` and a 2D integer array `queries`.

- There are `n` cities numbered from `0` to `n - 1`.
- Initially, there is a unidirectional road from city `i` to city `i + 1` for all `0 <= i < n - 1`.
- `queries[i] = [u_i, v_i]` represents the addition of a new unidirectional road from city `u_i` to city `v_i`.

After processing each query, you need to find the **length of the shortest path** from city `0` to city `n - 1`.

### Return
Return an array `answer` where for each `i` in the range `[0, queries.length - 1]`, `answer[i]` is the length of the shortest path from city `0` to city `n - 1` after processing the first `i + 1` queries.

---

## Examples

### Example 1
**Input**:
n = 5 queries = [[2,4],[0,2],[0,4]]

**Output**:
[3,2,1]

**Explanation**:
- Initially, the shortest path from `0` to `4` is `0 -> 1 -> 2 -> 3 -> 4` (length 4).
- After adding the road `[2,4]`, the path becomes `0 -> 1 -> 2 -> 4` (length 3).
- After adding the road `[0,2]`, the path becomes `0 -> 2 -> 4` (length 2).
- After adding the road `[0,4]`, the path becomes `0 -> 4` (length 1).

---

### Example 2
**Input**:

n = 4 queries = [[0,3],[0,2]]

**Output**:

[1,1]

**Explanation**:
- Initially, the shortest path from `0` to `3` is `0 -> 1 -> 2 -> 3` (length 3).
- After adding the road `[0,3]`, the path becomes `0 -> 3` (length 1).
- Adding `[0,2]` does not reduce the shortest path length.

---

## Constraints

- `3 <= n <= 500`
- `1 <= queries.length <= 500`
- `queries[i].length == 2`
- `0 <= queries[i][0] < queries[i][1] < n`
- `1 < queries[i][1] - queries[i][0]`
- There are no repeated roads among the queries.

---

## Solution

### Python Code
```python
class Solution:
    def shortestDistanceAfterQueries(
        self,
        n: int,
        queries: list[list[int]],
    ) -> list[int]:
        ans = []
        dist = list(range(n))  # Distance from city 0 to each city
        graph = [[] for _ in range(n)]
        
        # Initial roads between consecutive cities
        for i in range(n - 1):
            graph[i].append(i + 1)
        
        # Process each query
        for u, v in queries:
            graph[u].append(v)
            if dist[u] + 1 < dist[v]:  # Update distance if new road is shorter
                dist[v] = dist[u] + 1
                self._bfs(graph, v, dist)  # Update all distances using BFS
            ans.append(dist[n - 1])  # Append shortest path from 0 to n-1
        
        return ans

    def _bfs(self, graph: list[list[int]], start: int, dist: list[int]) -> None:
        import collections
        q = collections.deque([start])
        while q:
            u = q.popleft()
            for v in graph[u]:
                if dist[u] + 1 < dist[v]:
                    dist[v] = dist[u] + 1
                    q.append(v)
```
<h2>Explanation</h2>
Initialization:<br>
Maintain a dist array where dist[i] represents the shortest path length from city 0 to city i.<br>
Build a graph to store roads between cities.<br>
Query Processing:<br>
For each query, add the new road to the graph.<br>
If the new road reduces the distance to a city, use BFS to propagate the updated distances.<br>
Answer Update:<br>
Append the shortest distance from 0 to n - 1 after processing each query.<br>
<h2>Time Complexity</h2>
Road Addition: O(queries.length)<br>
BFS Update: O(n + m) where n is the number of cities, and m is the number of edges.<br>
Total Complexity: O(queries.length * (n + m)).<br>
<h2>Space Complexity</h2>
Graph Storage: O(n + m).<br>
Distance Array: O(n).
