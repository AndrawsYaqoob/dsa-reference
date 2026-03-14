# Queue

A linear structure where elements are added at the back and removed from the front. First In, First Out (FIFO).

---

## Key Properties

- Only the front element is removable
- FIFO — the first element enqueued is the first dequeued
- Backed by an array or linked list under the hood

---

## Operations & Complexity

| Operation | Time | Space | Notes                      |
|-----------|------|-------|----------------------------|
| Enqueue   | O(1) | O(1)  | Add to back                |
| Dequeue   | O(1) | O(1)  | Remove from front          |
| Peek      | O(1) | O(1)  | View front without removing|
| Search    | O(n) | O(1)  | Must scan from front       |

---

## Common Patterns

### Basic Enqueue / Dequeue
Use when you need to process elements in the order they arrived.
```
queue = []
queue.enqueue(item)   ← add to back
queue.dequeue()       ← remove from front
queue.peek()          ← view front
```

### BFS Traversal
Use when exploring a graph or tree level by level, guaranteeing the shortest path in unweighted graphs.
```
queue = [start]
visited = {start}
while queue is not empty:
    node = queue.dequeue()
    for each neighbor of node:
        if neighbor not in visited:
            visited.add(neighbor)
            queue.enqueue(neighbor)
```

### Sliding Window Maximum
Use when you need to track the maximum element in a sliding window efficiently using a double-ended queue (deque).
```
deque = []
for each element at index i:
    remove indices outside window from front
    while deque not empty and arr[deque.back] < element:
        deque.pop_back()
    deque.push_back(i)
    if i >= window size: result.add(arr[deque.front])
```

---

## When to Use

- Processing elements in arrival order
- BFS traversal of graphs and trees
- Task scheduling or buffering
- Sliding window maximum (deque)

---

## Classic Leetcode Problems

| Problem                          | Difficulty |
|----------------------------------|------------|
| Number of Islands                | Medium     |
| Binary Tree Level Order Traversal| Medium     |
| Rotting Oranges                  | Medium     |
| Sliding Window Maximum           | Hard       |

---

## See Also

- [Stack](stack.md) — same idea but LIFO. Last element in is the first out.