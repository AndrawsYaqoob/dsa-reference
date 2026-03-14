# Two Pointers

Using two variables to track two positions in a data structure simultaneously,
avoiding nested loops and reducing O(n²) to O(n).

---

## When to Use

- Sorted array and searching for a pair
- Comparing elements from both ends
- Detecting cycles in a linked list
- Removing duplicates in place
- Finding subarrays or subsequences

---

## Patterns

### Opposite Ends
Use when searching for a pair that satisfies a condition in a sorted array.
Start from both ends and move inward based on the result.
```
left = 0
right = n - 1
while left < right:
    if condition(arr[left], arr[right]):
        return [left, right]
    else if too small:
        left++
    else:
        right--
```

### Same Direction
Use when comparing adjacent elements or removing duplicates in place.
One pointer iterates, the other tracks the last valid position.
```
slow = 0
for fast from 0 to n - 1:
    if arr[fast] is valid:
        arr[slow] = arr[fast]
        slow++
```

### Fast & Slow Pointers (Floyd's)
Use when detecting cycles or finding the middle of a linked list.
Fast moves twice as fast as slow — when they meet, a cycle exists.
```
slow = head
fast = head
while fast and fast.next:
    slow = slow.next
    fast = fast.next.next
    if slow == fast: return true   ← cycle detected

# If no cycle, slow is at the midpoint when fast reaches the end
```

---

## When Each Variant Fits

| Variant         | Use When                                        |
|-----------------|-------------------------------------------------|
| Opposite Ends   | Sorted array, searching for a pair              |
| Same Direction  | Duplicates, partitioning, comparing neighbors   |
| Fast & Slow     | Linked list cycle, finding midpoint             |

---

## Classic Leetcode Problems

| Problem                              | Difficulty | Variant        |
|--------------------------------------|------------|----------------|
| Valid Palindrome                     | Easy       | Opposite Ends  |
| Two Sum II (sorted)                  | Medium     | Opposite Ends  |
| Remove Duplicates from Sorted Array  | Easy       | Same Direction |
| Container With Most Water            | Medium     | Opposite Ends  |
| 3Sum                                 | Medium     | Opposite Ends  |
| Linked List Cycle                    | Easy       | Fast & Slow    |
| Find the Duplicate Number            | Medium     | Fast & Slow    |