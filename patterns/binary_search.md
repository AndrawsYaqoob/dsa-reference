# Binary Search

Repeatedly halving the search space to find a target, reducing O(n) to O(log n).
Only works on sorted data or a monotonic search space.

---

## When to Use

- Array is sorted
- Finding a specific value or boundary
- Problem asks for min/max of something and the answer space is monotonic
- "Search in rotated sorted array" problems
- Phrase "find the smallest/largest that satisfies condition"

---

## Patterns

### Standard Binary Search
Use when searching for an exact value in a sorted array.
```
low = 0
high = n - 1
while low <= high:
    mid = (low + high) / 2
    if arr[mid] == target: return mid   ← found
    if arr[mid] < target: low = mid + 1 ← search right
    else: high = mid - 1                ← search left
return -1   ← not found
```

### Find Leftmost Position
Use when you need the first occurrence of a target or the leftmost valid position.
```
low = 0
high = n - 1
result = -1
while low <= high:
    mid = (low + high) / 2
    if arr[mid] == target:
        result = mid       ← save and keep searching left
        high = mid - 1
    else if arr[mid] < target: low = mid + 1
    else: high = mid - 1
return result
```

### Find Rightmost Position
Use when you need the last occurrence of a target or the rightmost valid position.
```
low = 0
high = n - 1
result = -1
while low <= high:
    mid = (low + high) / 2
    if arr[mid] == target:
        result = mid       ← save and keep searching right
        low = mid + 1
    else if arr[mid] < target: low = mid + 1
    else: high = mid - 1
return result
```

### Search in Rotated Sorted Array
Use when the sorted array has been rotated at an unknown pivot.
One half is always sorted — determine which half and search accordingly.
```
low = 0
high = n - 1
while low <= high:
    mid = (low + high) / 2
    if arr[mid] == target: return mid
    if arr[low] <= arr[mid]:              ← left half is sorted
        if arr[low] <= target < arr[mid]:
            high = mid - 1               ← target in left half
        else:
            low = mid + 1                ← target in right half
    else:                                 ← right half is sorted
        if arr[mid] < target <= arr[high]:
            low = mid + 1                ← target in right half
        else:
            high = mid - 1               ← target in left half
return -1
```

### Binary Search on Answer (Search Space)
Use when the answer is a value in a range and you can check if a value is valid.
Instead of searching an array, you search the answer space itself.
```
low = minimum possible answer
high = maximum possible answer
result = -1
while low <= high:
    mid = (low + high) / 2
    if isValid(mid):
        result = mid       ← save and search for better answer
        high = mid - 1     ← or low = mid + 1 depending on min/max
    else:
        low = mid + 1      ← or high = mid - 1
return result
```

---

## When Each Variant Fits

| Variant                      | Use When                                              |
|------------------------------|-------------------------------------------------------|
| Standard                     | Find exact value in sorted array                      |
| Leftmost / Rightmost         | First or last occurrence, boundary finding            |
| Rotated Sorted Array         | Sorted array rotated at unknown pivot                 |
| Binary Search on Answer      | Min/max of a value that satisfies a condition         |

---

## Classic Leetcode Problems

| Problem                                  | Difficulty | Variant                  |
|------------------------------------------|------------|--------------------------|
| Binary Search                            | Easy       | Standard                 |
| First Bad Version                        | Easy       | Leftmost                 |
| Search in Rotated Sorted Array           | Medium     | Rotated                  |
| Find Minimum in Rotated Sorted Array     | Medium     | Rotated                  |
| Find First and Last Position of Element  | Medium     | Leftmost / Rightmost     |
| Koko Eating Bananas                      | Medium     | Search on Answer         |
| Median of Two Sorted Arrays              | Hard       | Standard                 |