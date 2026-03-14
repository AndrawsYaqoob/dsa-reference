# Big O Notation

Measures how time or space scales as input size `n` grows.
Ignore constants, keep the dominant term.

---

## Complexity Order (fast → slow)

O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ) < O(n!)

---

## Complexities

| Notation   | Name         | Reason                                          |
|------------|--------------|-------------------------------------------------|
| O(1)       | Constant     | Direct access, no traversal                     |
| O(log n)   | Logarithmic  | Input is halved each step                       |
| O(n)       | Linear       | Each element visited once                       |
| O(n log n) | Linearithmic | Input divided, then each element processed      |
| O(n²)      | Quadratic    | For each element, all others are visited        |
| O(2ⁿ)      | Exponential  | Each step doubles the number of calls           |
| O(n!)      | Factorial    | Every possible ordering is explored             |

---

## Simplification Rules

- Drop constants → O(3n) = O(n)
- Drop lower terms → O(n² + n) = O(n²)
- Different inputs, different variables → O(a + b), not O(n)
- Nested loops over same input → multiply → O(n²)
- Sequential loops over same input → add → O(n + n) = O(n)

---

## Space Complexity

Same notation, but measures memory instead of time.
- Storing n items → O(n)
- Recursive call stack of depth n → O(n)
- Constant extra variables → O(1)

---

## Complexity Reference

### Structures

| Structure          | Access         | Search         | Insert         | Delete         |
|--------------------|----------------|----------------|----------------|----------------|
| Array              | O(1)           | O(n)           | O(n)           | O(n)           |
| Hashmap            | O(1) / O(n)*   | O(1) / O(n)*   | O(1) / O(n)*   | O(1) / O(n)*   |
| Stack / Queue      | O(1)           | O(n)           | O(1)           | O(1)           |
| Singly Linked List | O(n)           | O(n)           | O(1) head      | O(1) head      |
| Binary Search Tree | O(log n) / O(n)* | O(log n) / O(n)* | O(log n) / O(n)* | O(log n) / O(n)* |
| Heap               | O(1) top only  | O(n)           | O(log n)       | O(log n)       |
| Graph (adj. list)  | O(1)           | O(V + E)       | O(1)           | O(V + E)       |

`*` avg / worst

### Algorithms

| Algorithm      | Best       | Average    | Worst      | Space    |
|----------------|------------|------------|------------|----------|
| Binary Search  | O(1)       | O(log n)   | O(log n)   | O(1)     |
| Bubble Sort    | O(n)       | O(n²)      | O(n²)      | O(1)     |
| Insertion Sort | O(n)       | O(n²)      | O(n²)      | O(1)     |
| Merge Sort     | O(n log n) | O(n log n) | O(n log n) | O(n)     |
| Quick Sort     | O(n log n) | O(n log n) | O(n²)      | O(log n) |
| Heap Sort      | O(n log n) | O(n log n) | O(n log n) | O(1)     |
| DFS / BFS      | O(V + E)   | O(V + E)   | O(V + E)   | O(V)     |

`V` = vertices, `E` = edges