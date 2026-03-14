# Graph

A collection of nodes (vertices) connected by edges. Used to represent relationships and networks.

---

## Key Properties

- **Directed** — edges have a direction (A → B)
- **Undirected** — edges go both ways (A ↔ B)
- **Weighted** — edges have a cost or distance
- **Cyclic** — contains at least one cycle
- **Acyclic** — no cycles (e.g. trees are acyclic graphs)
- **Connected** — every node is reachable from any other node

---

## Representations

### Adjacency List
Use for sparse graphs (few edges). Most common in interview problems.
```
graph = {
    A: [B, C],
    B: [D],
    C: [D],
    D: []
}
```
Space: O(V + E)

### Adjacency Matrix
Use for dense graphs (many edges) or when you need O(1) edge lookup.
```
     A  B  C  D
A  [ 0, 1, 1, 0 ]
B  [ 0, 0, 0, 1 ]
C  [ 0, 0, 0, 1 ]
D  [ 0, 0, 0, 0 ]
```
Space: O(V²)

`V` = vertices, `E` = edges

---

## Operations & Complexity

| Operation     | Adjacency List | Adjacency Matrix |
|---------------|----------------|------------------|
| Add vertex    | O(1)           | O(V²)            |
| Add edge      | O(1)           | O(1)             |
| Remove edge   | O(E)           | O(1)             |
| Check edge    | O(V)           | O(1)             |
| Get neighbors | O(V)           | O(V)             |
| Space         | O(V + E)       | O(V²)            |

---

## Common Patterns

### DFS (Depth First Search)
Use when exploring all paths, detecting cycles, or going as deep as possible before backtracking.
```
visited = {}
dfs(node):
    if node in visited: return
    visited.add(node)
    process(node)
    for each neighbor of node:
        dfs(neighbor)
```

### BFS (Breadth First Search)
Use when finding the shortest path in an unweighted graph or exploring level by level.
```
queue = [start]
visited = {start}
while queue is not empty:
    node = queue.dequeue()
    process(node)
    for each neighbor of node:
        if neighbor not in visited:
            visited.add(neighbor)
            queue.enqueue(neighbor)
```

### Topological Sort
Use when ordering tasks with dependencies (e.g. course prerequisites). Only works on Directed Acyclic Graphs (DAG).
```
visited = {}
result = []
dfs(node):
    if node in visited: return
    visited.add(node)
    for each neighbor of node:
        dfs(neighbor)
    result.prepend(node)   ← add after all dependencies are processed

for each node in graph:
    dfs(node)
```

### Union Find (Disjoint Set)
Use when grouping nodes into connected components or detecting cycles in undirected graphs.
```
parent = {node: node for each node}

find(node):
    if parent[node] != node:
        parent[node] = find(parent[node])   ← path compression
    return parent[node]

union(a, b):
    rootA = find(a)
    rootB = find(b)
    if rootA == rootB: return false   ← cycle detected
    parent[rootA] = rootB
    return true
```

### Shortest Path — Dijkstra
Use when finding the shortest path in a weighted graph with non-negative edges.
```
dist = {node: infinity for each node}
dist[start] = 0
heap = [(0, start)]   ← (cost, node)

while heap is not empty:
    cost, node = heap.pop_min()
    if cost > dist[node]: continue
    for each neighbor, weight of node:
        new_cost = cost + weight
        if new_cost < dist[neighbor]:
            dist[neighbor] = new_cost
            heap.push((new_cost, neighbor))
```

---

## When to Use

- Modeling relationships or networks
- Finding shortest path (BFS unweighted, Dijkstra weighted)
- Detecting cycles (Union Find, DFS)
- Ordering dependencies (Topological Sort)
- Exploring all paths or connected components (DFS)

---

## Classic Leetcode Problems

| Problem                              | Difficulty |
|--------------------------------------|------------|
| Number of Islands                    | Medium     |
| Clone Graph                          | Medium     |
| Course Schedule                      | Medium     |
| Pacific Atlantic Water Flow          | Medium     |
| Number of Connected Components       | Medium     |
| Cheapest Flights Within K Stops      | Medium     |
| Word Ladder                          | Hard       |
| Network Delay Time (Dijkstra)        | Medium     |