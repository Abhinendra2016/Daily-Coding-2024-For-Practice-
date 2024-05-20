# Closest Distance Pair

## Problem Statement
You are given an array containing 'N' points in the plane. The task is to find out the distance of the closest points.

**Note:**
The distance between two points (x1, y1) and (x2, y2) is calculated as:
\[ \text{distance} = (x1 - x2)^2 + (y1 - y2)^2 \]

## Solution
```python
from sys import stdin, setrecursionlimit
setrecursionlimit(10**7)

# Point class for 2-D points
class point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

def dist(p1, p2):
    return (p1.x - p2.x)**2 + (p1.y - p2.y)**2

def bruteForce(cordinates, start, end):
    min_dist = float('inf')
    for i in range(start, end):
        for j in range(i+1, end):
            min_dist = min(min_dist, dist(cordinates[i], cordinates[j]))
    return min_dist

def stripClosest(strip, size, d):
    min_dist = d
    for i in range(size):
        j = i + 1
        while j < size and (strip[j].y - strip[i].y) < min_dist:
            min_dist = min(min_dist, dist(strip[i], strip[j]))
            j += 1
    return min_dist

def closestPairUtil(cordinates, start, end):
    if end - start <= 3:
        return bruteForce(cordinates, start, end)

    mid = (start + end) // 2
    mid_point = cordinates[mid]

    dl = closestPairUtil(cordinates, start, mid)
    dr = closestPairUtil(cordinates, mid+1, end)
    d = min(dl, dr)

    strip = []
    for i in range(start, end):
        if abs(cordinates[i].x - mid_point.x) < d:
            strip.append(cordinates[i])

    strip.sort(key=lambda point: point.y)

    return min(d, stripClosest(strip, len(strip), d))

def closestPair(cordinates, n):
    cordinates.sort(key=lambda point: point.x)
    return closestPairUtil(cordinates, 0, n)

# Taking input using fast I/O
def takeInput():
    n = int(input().strip())
    if n == 0:
        return list(), n

    cordinates = [point(0,0) for i in range(n)]

    for i in range(n):
        arr = list(map(int, stdin.readline().strip().split(" ")))
        cordinates[i] = point(arr[0], arr[1])

    return cordinates, n

# Main
cordinates, n = takeInput()
print(closestPair(cordinates, n))
```
