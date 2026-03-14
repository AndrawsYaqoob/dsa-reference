# Tree

A hierarchical structure where each node has a parent (except the root) and zero or more children.

---

## Key Properties

- Root — top node with no parent
- Leaf — node with no children
- Height — longest path from root to a leaf
- Depth — distance from root to a node
- Binary Tree — each node has at most 2 children (left, right)
- Binary Search Tree (BST) — left < node < right at every node

---

## Operations & Complexity

| Operation | Binary Tree | BST avg  | BST worst | Space |
|-----------|-------------|----------|-----------|-------|
| Search    | O(n)        | O(log n) | O(n)      | O(h)  |
| Insert    | O(n)        | O(log n) | O(n)      | O(h)  |
| Delete    | O(n)        | O(log n) | O(n)      | O(h)  |

`h` = height of tree. BST worst case occurs when tree is unbalanced (like a linked list).

---

## DFS Traversals

All three traversals visit every node once — O(n) time, O(h) space for the call stack.

### Inorder (Left → Node → Right)
Use when you need elements in sorted order from a BST.
```
inorder(node):
    if node is null: return
    inorder(node.left)
    process(node)
    inorder(node.right)
```

### Preorder (Node → Left → Right)
Use when you need to serialize or copy a tree.
```
preorder(node):
    if node is null: return
    process(node)
    preorder(node.left)
    preorder(node.right)
```

### Postorder (Left → Right → Node)
Use when you need to process children before the parent (e.g. deleting a tree, evaluating expressions).
```
postorder(node):
    if node is null: return
    postorder(node.left)
    postorder(node.right)
    process(node)
```

---

## BFS / Level Order Traversal

Use when you need to process nodes level by level, or find the shortest path in an unweighted tree.
```
queue = [root]
while queue is not empty:
    node = queue.dequeue()
    process(node)
    if node.left: queue.enqueue(node.left)
    if node.right: queue.enqueue(node.right)
```

---

## Common Patterns

### Path Sum
Use when checking if a root-to-leaf path exists that sums to a target value.
```
hasPathSum(node, target):
    if node is null: return false
    if node is leaf: return node.val == target
    return hasPathSum(node.left, target - node.val) or
           hasPathSum(node.right, target - node.val)
```

### Lowest Common Ancestor (LCA)
Use when finding the deepest node that is an ancestor of two given nodes.
```
lca(node, p, q):
    if node is null: return null
    if node == p or node == q: return node
    left = lca(node.left, p, q)
    right = lca(node.right, p, q)
    if left and right: return node   ← p and q are on different sides
    return left or right
```

### Validate BST
Use when checking if a binary tree is a valid BST.
```
validate(node, min, max):
    if node is null: return true
    if node.val <= min or node.val >= max: return false
    return validate(node.left, min, node.val) and
           validate(node.right, node.val, max)
```

---

## Trie

A tree where each node represents a character. Used for prefix-based search.

### Key Properties
- Root is empty
- Each path from root to a leaf represents a word
- O(m) search and insert where m = length of word

### Common Pattern — Insert & Search
```
# Node structure
TrieNode:
    children = {}
    is_end = false

# Insert
insert(word):
    node = root
    for each char in word:
        if char not in node.children:
            node.children[char] = TrieNode()
        node = node.children[char]
    node.is_end = true

# Search
search(word):
    node = root
    for each char in word:
        if char not in node.children: return false
        node = node.children[char]
    return node.is_end
```

---

## When to Use

- Hierarchical data (file system, org chart)
- BST for sorted dynamic data with fast lookup
- DFS/BFS for traversal and path problems
- Trie for autocomplete, spell check, prefix search

---

## Classic Leetcode Problems

| Problem                              | Difficulty |
|--------------------------------------|------------|
| Invert Binary Tree                   | Easy       |
| Maximum Depth of Binary Tree         | Easy       |
| Same Tree                            | Easy       |
| Lowest Common Ancestor of a BST      | Medium     |
| Binary Tree Level Order Traversal    | Medium     |
| Validate Binary Search Tree          | Medium     |
| Construct Binary Tree from Preorder and Inorder | Medium |
| Word Search II (Trie)                | Hard       |
| Serialize and Deserialize Binary Tree| Hard       |