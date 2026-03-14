# Dynamic Programming

Break a problem into overlapping subproblems, solve each once, and store the result.
Avoids redundant computation by trading space for time.

---

## When to Use

- Problem has overlapping subproblems (same subproblem solved multiple times)
- Problem has optimal substructure (optimal solution built from optimal subproblems)
- Keywords: "min/max", "how many ways", "is it possible", "longest/shortest"

---

## Two Approaches

| Approach                  | How                              | When                                      |
|---------------------------|----------------------------------|-------------------------------------------|
| Top-Down (Memoization)    | Recursion + cache                | Natural recursive structure is clear      |
| Bottom-Up (Tabulation)    | Iterative, fill table from base  | Want to avoid recursion overhead          |

---

## Templates

### Top-Down (Memoization)
Start from the original problem, recurse down, cache results to avoid recomputation.
```
memo = {}

solve(n):
    if n in memo: return memo[n]        ← return cached result
    if base case: return base_value
    memo[n] = combine(solve(subproblem1), solve(subproblem2))
    return memo[n]
```

### Bottom-Up (Tabulation)
Start from the base case, iteratively build up to the original problem.
```
dp = array of size n + 1
dp[0] = base case
dp[1] = base case

for i from 2 to n:
    dp[i] = combine(dp[i - 1], dp[i - 2])

return dp[n]
```

---

## Patterns

### 1D DP
Use when the current state depends only on a fixed number of previous states.
```
# Climbing Stairs — how many ways to reach step n using 1 or 2 steps
dp[0] = 1   ← one way to stay at ground
dp[1] = 1   ← one way to reach step 1
for i from 2 to n:
    dp[i] = dp[i - 1] + dp[i - 2]
return dp[n]
```

### 2D DP — Grid
Use when moving through a grid and the current cell depends on adjacent cells.
```
# Unique Paths — how many ways to reach bottom-right of an m x n grid
dp = grid of size m x n filled with 1s   ← base case: one way along edges
for i from 1 to m - 1:
    for j from 1 to n - 1:
        dp[i][j] = dp[i - 1][j] + dp[i][j - 1]
return dp[m - 1][n - 1]
```

### 2D DP — Strings
Use when comparing two strings and the current state depends on previous characters.
```
# Longest Common Subsequence
dp = grid of size (m + 1) x (n + 1) filled with 0s
for i from 1 to m:
    for j from 1 to n:
        if s1[i - 1] == s2[j - 1]:
            dp[i][j] = dp[i - 1][j - 1] + 1   ← characters match
        else:
            dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
return dp[m][n]
```

### Knapsack
Use when selecting items with weights and values to maximize value within a capacity.
Each item can be included or excluded.
```
# 0/1 Knapsack
dp = grid of size (n + 1) x (capacity + 1) filled with 0s
for i from 1 to n:
    for w from 0 to capacity:
        if weight[i] <= w:
            dp[i][w] = max(dp[i - 1][w], value[i] + dp[i - 1][w - weight[i]])
        else:
            dp[i][w] = dp[i - 1][w]   ← item too heavy, skip
return dp[n][capacity]
```

---

## When Each Variant Fits

| Variant          | Use When                                              |
|------------------|-------------------------------------------------------|
| 1D DP            | Current state depends on previous 1 or 2 states      |
| 2D DP — Grid     | Navigating a grid, path counting                      |
| 2D DP — Strings  | Comparing or aligning two sequences                   |
| Knapsack         | Selecting items under a constraint to optimize value  |

---

## Classic Leetcode Problems

| Problem                            | Difficulty | Variant         |
|------------------------------------|------------|-----------------|
| Climbing Stairs                    | Easy       | 1D DP           |
| House Robber                       | Medium     | 1D DP           |
| Coin Change                        | Medium     | 1D DP           |
| Longest Increasing Subsequence     | Medium     | 1D DP           |
| Unique Paths                       | Medium     | 2D DP — Grid    |
| Minimum Path Sum                   | Medium     | 2D DP — Grid    |
| Longest Common Subsequence         | Medium     | 2D DP — Strings |
| Edit Distance                      | Medium     | 2D DP — Strings |
| Partition Equal Subset Sum         | Medium     | Knapsack        |
| Target Sum                         | Medium     | Knapsack        |