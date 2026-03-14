# Backtracking

Build a solution incrementally, one step at a time, and undo (backtrack) a step
when it leads to an invalid or complete state. A structured form of brute force.

---

## When to Use

- Exploring all possible combinations, subsets, or permutations
- Problem asks for all valid solutions, not just one
- Constraints eliminate large portions of the search space early
- Keywords: "all possible", "generate all", "find all combinations"

---

## General Template

Every backtracking problem follows the same skeleton.
Build → recurse → undo.
```
result = []

backtrack(current, choices):
    if base case:
        result.add(copy of current)   ← save valid solution
        return
    for each choice in choices:
        if choice is valid:
            current.add(choice)       ← make a choice
            backtrack(current, updated choices)
            current.remove(choice)    ← undo the choice
```

---

## Patterns

### Subsets
Use when you need all possible subsets of a set (including empty set).
At each step, choose to include or exclude the current element.
```
result = []

backtrack(start, current):
    result.add(copy of current)   ← every state is a valid subset
    for i from start to n - 1:
        current.add(arr[i])
        backtrack(i + 1, current)
        current.remove(arr[i])

backtrack(0, [])
```

### Combinations
Use when you need all combinations of K elements from a set.
Similar to subsets but only save when current size equals K.
```
result = []

backtrack(start, current):
    if len(current) == K:
        result.add(copy of current)
        return
    for i from start to n - 1:
        current.add(arr[i])
        backtrack(i + 1, current)
        current.remove(arr[i])

backtrack(0, [])
```

### Permutations
Use when you need all possible orderings of a set.
Unlike subsets/combinations, order matters and each element is used once.
```
result = []
used = {}

backtrack(current):
    if len(current) == n:
        result.add(copy of current)
        return
    for each num in arr:
        if num not in used:
            used.add(num)
            current.add(num)
            backtrack(current)
            current.remove(num)
            used.remove(num)

backtrack([])
```

---

## When Each Variant Fits

| Variant      | Use When                                      | Order Matters | Size Fixed |
|--------------|-----------------------------------------------|---------------|------------|
| Subsets      | All possible subsets                          | No            | No         |
| Combinations | All groups of exactly K elements              | No            | Yes        |
| Permutations | All possible orderings                        | Yes           | Yes        |

---

## Classic Leetcode Problems

| Problem                   | Difficulty | Variant      |
|---------------------------|------------|--------------|
| Subsets                   | Medium     | Subsets      |
| Subsets II (duplicates)   | Medium     | Subsets      |
| Combination Sum           | Medium     | Combinations |
| Combination Sum II        | Medium     | Combinations |
| Permutations              | Medium     | Permutations |
| Permutations II           | Medium     | Permutations |
| Word Search               | Medium     | General      |
| N-Queens                  | Hard       | General      |
| Palindrome Partitioning   | Medium     | General      |