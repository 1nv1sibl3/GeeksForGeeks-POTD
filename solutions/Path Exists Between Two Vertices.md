# Path Exists Between Two Vertices

**Difficulty:** Easy

## Approach - DFS

- Start traversing the graph from vertex `u` using iterative DFS.
- Maintain a `visited` set to avoid revisiting vertices.
- If vertex `v` is reached, return `True`.
- If traversal ends without reaching `v`, return `False`.

## Solution

```python
class Solution:
    def checkPath(self, adj: list[list[int]], u: int, v: int) -> bool:
        visited = {u}
        stack = [u]

        while stack:
            node = stack.pop()

            if node == v:
                return True

            for neighbor in adj[node]:
                if neighbor not in visited:
                    visited.add(neighbor)
                    stack.append(neighbor)

        return False
```

## Complexity Analysis

- **Time Complexity:** O(V + E)
- **Space Complexity:** O(V)

Where V is the number of vertices and E is the number of edges.
