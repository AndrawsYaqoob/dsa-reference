# Recursion

A function that calls itself with a smaller input until it hits a stopping condition.

---

## Base Case & Recursive Case

- **Base case** — when to stop. Without it, infinite recursion → stack overflow.
- **Recursive case** — the smaller subproblem passed to the next call.

---

## Template

The product of all positive integers from 1 to n. (e.g. 5! = 5 × 4 × 3 × 2 × 1 = 120)
```
function solve(n):
    if n == base: return base_value   ← stop condition
    return f( solve(n - 1) )          ← call with smaller input
```

---

## Example — Factorial

```
factorial(n):
    if n == 0: return 1          ← base case
    return n * factorial(n - 1)  ← recursive case
```

---

## Call Stack

Each call is added to the stack and waits until the base case is hit, then resolves back up.

factorial(3)
  factorial(2)
    factorial(1)
      factorial(0)
        returns 1         ← base case hit
      returns 1 * 1 = 1
    returns 2 * 1 = 2
  returns 3 * 2 = 6

Stack depth = number of recursive calls = O(n) space.

---

## When to Use Recursion vs Iteration

| Use Recursion                          | Use Iteration                  |
|----------------------------------------|--------------------------------|
| Problem has natural substructure       | Simple loops suffice           |
| Tree / graph traversal                 | Performance is critical        |
| Backtracking / exploring all paths     | Stack overflow is a risk       |
| Divide and conquer                     | Language lacks tail-call opt.  |

---

## Where It Shows Up

| Area                | Why Recursion Fits                                          |
|---------------------|-------------------------------------------------------------|
| Trees               | Each node is a subproblem of the same structure             |
| Graphs (DFS)        | Explore a path, backtrack, explore next                     |
| Backtracking        | Build a solution, undo, try another path                    |
| Divide & Conquer    | Split input, solve halves, merge results                    |
| Dynamic Programming | Overlapping subproblems solved recursively + memoized       |