# Stack

A linear structure where elements are added and removed from the same end. Last In, First Out (LIFO).

---

## Key Properties

- Only the top element is accessible
- LIFO — the last element pushed is the first popped
- Backed by an array or linked list under the hood

---

## Operations & Complexity

| Operation | Time | Space | Notes                     |
|-----------|------|-------|---------------------------|
| Push      | O(1) | O(1)  | Add to top                |
| Pop       | O(1) | O(1)  | Remove from top           |
| Peek      | O(1) | O(1)  | View top without removing |
| Search    | O(n) | O(1)  | Must scan from top        |

---

## Common Patterns

### Basic Push / Pop
Use when you need to process elements in reverse order or undo a previous step.
```
stack = []
stack.push(item)   ← add to top
stack.pop()        ← remove from top
stack.peek()       ← view top
```

### Balanced Parentheses
Use when validating that every opening symbol has a matching closing symbol.
```
stack = []
for each char in string:
    if char is opening: stack.push(char)
    if char is closing:
        if stack is empty or top doesn't match: return false
        stack.pop()
return stack is empty
```

### Monotonic Stack
Use when you need to track the next greater or smaller element for each item in an array.
```
stack = []
for each element in array:
    while stack not empty and top < element:
        process(stack.pop())
    stack.push(element)
```

---

## When to Use

- Need to reverse order of elements
- Tracking previous state (undo, backtracking)
- Validating nested structures (parentheses, brackets)
- Iterative DFS traversal
- Finding next greater / smaller element

---

## Classic Leetcode Problems

| Problem                          | Difficulty |
|----------------------------------|------------|
| Valid Parentheses                | Easy       |
| Min Stack                        | Medium     |
| Evaluate Reverse Polish Notation | Medium     |
| Daily Temperatures               | Medium     |
| Largest Rectangle in Histogram   | Hard       |

---

## See Also

- [Queue](queue.md) — same idea but FIFO. First element in is the first out.