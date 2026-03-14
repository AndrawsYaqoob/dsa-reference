# Array

A ordered collection of elements stored in contiguous memory, accessible by index.

---

## Key Properties

- Zero-indexed
- Fixed size in most languages (dynamic in Python/JS)
- Elements are the same type (in typed languages)
- Fast access by index, slow insert/delete in the middle

---

## Operations & Complexity

| Operation          | Time | Space | Notes                        |
|--------------------|------|-------|------------------------------|
| Access by index    | O(1) | O(1)  | Direct memory lookup         |
| Search             | O(n) | O(1)  | Must scan each element       |
| Insert at end      | O(1) | O(1)  | Append                       |
| Insert at middle   | O(n) | O(1)  | Shift elements right         |
| Delete at end      | O(1) | O(1)  | Remove last                  |
| Delete at middle   | O(n) | O(1)  | Shift elements left          |

---

## Common Patterns

### Traversal
Visit every element in order, one at a time.
```
for i from 0 to n - 1:
    process(arr[i])
```

### Two Pointers
Use when searching for a pair that satisfies a condition. Start from both ends and move inward, avoiding a nested loop O(n²).
```
left = 0
right = n - 1
while left < right:
    process(arr[left], arr[right])
    move left or right based on condition
```

### Sliding Window
Use when working with a contiguous subarray of variable size. Expand from the right, shrink from the left when the window becomes invalid.
```
start = 0
for end from 0 to n - 1:
    expand window with arr[end]
    while window is invalid:
        shrink from start
        start++
    update result
```

### Prefix Sum
Use when you need the sum of a subarray range repeatedly. Precompute cumulative sums once O(n), then answer each range query in O(1).
```
prefix[0] = arr[0]
for i from 1 to n - 1:
    prefix[i] = prefix[i - 1] + arr[i]

# Sum of range [l, r]
sum = prefix[r] - prefix[l - 1]
```

---

## When to Use

- Need fast index access
- Data is ordered and fixed size
- Applying two pointer or sliding window patterns
- Storing intermediate results (prefix sums, dp tables)

---

## Classic Leetcode Problems

| Problem                              | Difficulty |
|--------------------------------------|------------|
| Two Sum                              | Easy       |
| Best Time to Buy and Sell Stock      | Easy       |
| Contains Duplicate                   | Easy       |
| Product of Array Except Self         | Medium     |
| Maximum Subarray                     | Medium     |
| Sliding Window Maximum               | Hard       |