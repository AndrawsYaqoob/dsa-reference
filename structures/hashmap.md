# Hashmap

A key-value store that maps keys to values using a hash function for direct access.

---

## Key Properties

- Keys are unique
- Values are accessible by key, not by index
- Unordered (insertion order not guaranteed in all languages)
- Hash collisions can degrade performance to O(n) in worst case

---

## Operations & Complexity

| Operation | Time          | Space | Notes                        |
|-----------|---------------|-------|------------------------------|
| Access    | O(1) / O(n)*  | O(1)  | Direct key lookup            |
| Search    | O(1) / O(n)*  | O(1)  | Check if key exists          |
| Insert    | O(1) / O(n)*  | O(1)  | Add or update key-value pair |
| Delete    | O(1) / O(n)*  | O(1)  | Remove by key                |

`*` avg / worst — worst case due to hash collisions

---

## Common Patterns

### Frequency Count
Use when you need to track how many times each element appears.
```
map = {}
for each item in collection:
    if item in map: map[item]++
    else: map[item] = 1
```

### Seen Before (Duplicate Detection)
Use when you need to know if an element has already been encountered.
```
seen = {}
for each item:
    if item in seen: return true   ← duplicate found
    seen[item] = true
return false
```

### Two Sum Pattern
Use when you need to find two elements that satisfy a condition (e.g. sum to target).
Instead of a nested loop O(n²), store complements as you go for O(n).
```
map = {}
for each num at index i:
    complement = target - num
    if complement in map: return [map[complement], i]
    map[num] = i
```

---

## When to Use

- Need O(1) lookup, insert, or delete
- Counting frequencies
- Detecting duplicates
- Storing seen values to avoid revisiting
- Pairing values (e.g. Two Sum, anagram detection)

---

## Classic Leetcode Problems

| Problem                              | Difficulty |
|--------------------------------------|------------|
| Two Sum                              | Easy       |
| Valid Anagram                        | Easy       |
| Contains Duplicate                   | Easy       |
| Group Anagrams                       | Medium     |
| Top K Frequent Elements              | Medium     |
| Longest Consecutive Sequence         | Medium     |