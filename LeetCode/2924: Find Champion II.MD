# Problem 2924: Find Champion II

There are `n` teams numbered from `0` to `n - 1` in a tournament; each team is also a node in a Directed Acyclic Graph (DAG).

## Problem Description

You are given the integer `n` and a 0-indexed 2D integer array `edges` of length `m` representing the DAG, where `edges[i] = [u_i, v_i]` indicates that there is a directed edge from team `u_i` to team `v_i` in the graph.

A directed edge from team `a` to team `b` in the graph means:
- Team `a` is stronger than team `b`.
- Team `b` is weaker than team `a`.

Team `a` will be the **champion** of the tournament if there is no team `b` that is stronger than team `a`.

You need to return the team that will be the champion of the tournament if there is a unique champion. If no such unique champion exists, return `-1`.

### Notes
- A cycle is a series of nodes `a1, a2, ..., an, an+1` such that node `a1` is the same as node `an+1`. The nodes `a1, a2, ..., an` are distinct, and there is a directed edge from node `ai` to node `ai+1` for every `i` in the range `[1, n]`.
- A DAG (Directed Acyclic Graph) is a directed graph that does not have any cycle.

## Examples

### Example 1
**Input**:
n = 3 edges = [[0,1], [1,2]]
**Output**:
0
**Explanation**:
- Team 1 is weaker than team 0.
- Team 2 is weaker than team 1.
- Therefore, team 0 is the champion.

### Example 2
**Input**:
n = 4 edges = [[0,2], [1,3], [1,2]]
**Output**:
-1
**Explanation**:
- Team 2 is weaker than both team 0 and team 1.
- Team 3 is weaker than team 1.
- Both team 0 and team 1 are not weaker than any other teams.
- Therefore, there is no unique champion, so the output is `-1`.

## Constraints
- `1 <= n <= 100`
- `m == edges.length`
- `0 <= m <= n * (n - 1) / 2`
- `edges[i].length == 2`
- `0 <= edges[i][j] <= n - 1`
- `edges[i][0] != edges[i][1]`
- The input is generated such that:
  - If team `a` is stronger than team `b`, team `b` is not stronger than team `a`.
  - If team `a` is stronger than team `b` and team `b` is stronger than team `c`, then team `a` is stronger than team `c`.

## Solution

### Python Code
```python
class Solution:
    def findChampion(self, n: int, edges: list[list[int]]) -> int:
        inDegrees = [0] * n

        for _, v in edges:
            inDegrees[v] += 1

        return (-1 if inDegrees.count(0) > 1
                else inDegrees.index(0))
```


### Example 1
**Input**:
n = 3 edges = [[0,1], [1,2]]

**Output**:
0

<h2>Explanation</h2>
Initialize an array inDegrees of size n to count the number of incoming edges for each team.<br>
Iterate through each edge, increasing the count of incoming edges for the target node.<br>
A team can only be the champion if it has no incoming edges (i.e., inDegrees[team] == 0).<br>
If there is exactly one team with inDegrees == 0, it is the unique champion.<br>
If more than one team has inDegrees == 0, return -1 since there is no unique champion.<br>
<h2>Time Complexity</h2>
O(n + m): We iterate over the list of edges once and check the inDegrees list.<br>
n is the number of teams.<br>
m is the number of edges.<br>
<h2>Space Complexity</h2>
O(n): The inDegrees list is of size n.<br>
