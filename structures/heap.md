# Heap

A complete binary tree where the parent is always greater (Max-Heap) or smaller (Min-Heap) than its children.

---

## Key Properties

- The top element is always the min or max
- Not fully sorted — only the parent/child relationship is guaranteed
- Usually implemented as an array under the hood
- Two types: Min-Heap (smallest at top), Max-Heap (largest at top)

---

## Operations & Complexity

| Operation   | Time     | Space | Notes                          |
|-------------|----------|-------|--------------------------------|
| Get top     | O(1)     | O(1)  | Min or max always at top       |
| Insert      | O(log n) | O(1)  | Bubble up to restore order     |
| Remove top  | O(log n) | O(1)  | Bubble down to restore order   |
| Build heap  | O(n)     | O(n)  | From an unsorted array         |
| Search      | O(n)     | O(1)  | No guaranteed order beyond top |

---

## Common Patterns

### Get Min / Max
Use when you repeatedly need the smallest or largest element from a changing collection.
```
heap = MinHeap()
heap.push(item)
top = heap.pop()   ← always returns the smallest
```

### Top K Smallest Elements
Use a Max-Heap of size K. Push each element and pop when size exceeds K.
The heap retains the K smallest seen so far.
```
heap = MaxHeap()
for each num in array:
    heap.push(num)
    if heap.size > K: heap.pop()
return heap
```

### Top K Largest Elements
Use a Min-Heap of size K. Push each element and pop when size exceeds K.
The heap retains the K largest seen so far.
```
heap = MinHeap()
for each num in array:
    heap.push(num)
    if heap.size > K: heap.pop()
return heap
```

### K Way Merge
Use when merging K sorted lists. Push the first element of each list into a Min-Heap, then pop and push the next element from the same list.
```
heap = MinHeap()
for each list: heap.push(list[0], list, index=0)
while heap not empty:
    val, list, i = heap.pop()
    result.add(val)
    if i + 1 < list.size: heap.push(list[i+1], list, index=i+1)
```

---

## When to Use

- Need repeated access to min or max
- Finding top K elements
- Merging K sorted lists
- Dijkstra's shortest path algorithm
- Scheduling by priority

---

## Classic Leetcode Problems

| Problem                          | Difficulty |
|----------------------------------|------------|
| Kth Largest Element in an Array  | Medium     |
| Top K Frequent Elements          | Medium     |
| Find Median from Data Stream     | Hard       |
| Merge K Sorted Lists             | Hard       |
| Task Scheduler                   | Medium     |