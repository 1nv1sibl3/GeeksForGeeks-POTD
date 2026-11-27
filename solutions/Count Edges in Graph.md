# Count Edges in Graph

## Approach
In an undirected graph, every edge appears twice in the adjacency list. Therefore, we simply sum the lengths of all adjacency lists and divide the result by 2 to get the total number of edges.

## Solution
```python
class Solution:
    def countEdges(self, adj: list[list[int]]) -> int:
        return sum(len(i) for i in adj) // 2
```

## Complexity
- **Time Complexity:** O(V), where V is the number of vertices.
- **Space Complexity:** O(1), as no extra space is required.
