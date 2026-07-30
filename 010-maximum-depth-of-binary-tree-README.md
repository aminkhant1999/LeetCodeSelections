# 010. Maximum Depth of Binary Tree

Difficulty: Easy

LeetCode: https://leetcode.com/problems/maximum-depth-of-binary-tree/

---

## Question

Given the `root` of a binary tree, return its maximum depth.

The maximum depth is the number of nodes along the longest path from the root down to the farthest leaf node.

---

## Examples

### Example 1

**Input**

```text
root = [3,9,20,null,null,15,7]
```

**Output**

```text
3
```

---

### Example 2

**Input**

```text
root = [1,null,2]
```

**Output**

```text
2
```

---

## Constraints

```text
The number of nodes is in the range `[0, 10⁴]`.
-100 <= Node.val <= 100
```

---

## Pattern

DFS

---

## Key Idea

Use recursive depth-first search.

- An empty tree has depth `0`.
- Find the depth of the left subtree.
- Find the depth of the right subtree.
- Return `1 +` the larger subtree depth.

---

## Iteration Trace

**Input**

```text
root = [3,9,20,null,null,15,7]
```

| Node | Left Depth | Right Depth | Returned Depth |
| ---- | ---------- | ----------- | -------------- |
| 9    | 0          | 0           | 1              |
| 15   | 0          | 0           | 1              |
| 7    | 0          | 0           | 1              |
| 20   | 1          | 1           | 2              |
| 3    | 1          | 2           | 3              |

---

## Code

```javascript
var maxDepth = function(root) {
    if (root === null) {
        return 0;
    }

    const leftDepth = maxDepth(root.left);
    const rightDepth = maxDepth(root.right);

    return 1 + Math.max(leftDepth, rightDepth);
};
```

---

## Complexity

**Time**

```text
O(n)
```

**Space**

```text
O(h)
```

for the recursion stack, where `h` is the tree height. It is `O(log n)` for a balanced tree and `O(n)` for a skewed tree.

---

## Notes

✔ The base case for a missing node is depth `0`.

✔ Each real node adds `1` to the deeper child path.

✔ DFS naturally solves problems defined using subtree results.

---

## Recognition

Use this pattern when you need to:

- Calculate a property from child subtrees
- Explore a tree down to its leaves
- Use recursion with a clear base case
