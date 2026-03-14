# Sliding Window

A technique where a window (subarray or substring) expands and shrinks over a sequence
to avoid recomputing results from scratch, reducing O(n²) to O(n).

---

## When to Use

- Finding a subarray or substring that satisfies a condition
- Maximum or minimum sum of a subarray of size K
- Longest or shortest subarray/substring with a constraint
- Problem involves contiguous elements

---

## Patterns

### Fixed Size Window
Use when the window size K is given. Slide the window one step at a time,
adding the new element and removing the element that falls out.
```
window_sum = sum of first K elements
result = window_sum

for i from K to n - 1:
    window_sum += arr[i]           ← add new element
    window_sum -= arr[i - K]       ← remove element that fell out
    result = max(result, window_sum)
```

### Variable Size Window
Use when the window size is not fixed and must grow or shrink based on a condition.
Expand from the right, shrink from the left when the window becomes invalid.
```
start = 0
result = 0
for end from 0 to n - 1:
    add arr[end] to window
    while window is invalid:
        remove arr[start] from window
        start++
    result = max(result, end - start + 1)
```

### Sliding Window + Hashmap
Use when tracking character or element frequencies inside the window.
Common in substring problems.
```
start = 0
freq = {}
result = 0
for end from 0 to n - 1:
    freq[arr[end]]++
    while window is invalid:
        freq[arr[start]]--
        if freq[arr[start]] == 0: remove arr[start] from freq
        start++
    result = max(result, end - start + 1)
```

---

## When Each Variant Fits

| Variant                  | Use When                                          |
|--------------------------|---------------------------------------------------|
| Fixed Size Window        | Window size K is given                            |
| Variable Size Window     | Find longest/shortest subarray with a constraint  |
| Sliding Window + Hashmap | Tracking frequencies inside the window            |

---

## Classic Leetcode Problems

| Problem                                         | Difficulty | Variant                  |
|-------------------------------------------------|------------|--------------------------|
| Maximum Average Subarray I                      | Easy       | Fixed Size               |
| Longest Substring Without Repeating Characters  | Medium     | Variable Size + Hashmap  |
| Minimum Size Subarray Sum                       | Medium     | Variable Size            |
| Permutation in String                           | Medium     | Fixed Size + Hashmap     |
| Longest Repeating Character Replacement         | Medium     | Variable Size + Hashmap  |
| Minimum Window Substring                        | Hard       | Variable Size + Hashmap  |