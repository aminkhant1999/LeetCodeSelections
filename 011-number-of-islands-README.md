# 011. Number of Islands

Difficulty: Medium

LeetCode: https://leetcode.com/problems/number-of-islands/

---

## Question

Given an `m × n` 2D binary grid where `"1"` represents land and `"0"` represents water, return the number of islands.

An island is formed by horizontally or vertically connected land cells and is surrounded by water. The grid edges are also water.

---

## Examples

### Example 1

**Input**

```text
grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
```

**Output**

```text
1
```

---

### Example 2

**Input**

```text
grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
```

**Output**

```text
3
```

---

## Constraints

```text
m == grid.length
n == grid[i].length
1 <= m, n <= 300
`grid[i][j]` is `"0"` or `"1"`.
```

---

## Pattern

Graph DFS/BFS

---

## Key Idea

Scan every cell. When an unvisited land cell is found:

1. Increase the island count.
2. Run DFS from that cell.
3. Mark every horizontally or vertically connected land cell as visited by changing it to `"0"`.

Each DFS removes one complete island from future consideration.

---

## Iteration Trace

**Input**

```text
grid = [
  ["1","1","0"],
  ["1","0","0"],
  ["0","0","1"]
]
```

| Scan Position   | Value | Action                                      | Island Count |
| --------------- | ----- | ------------------------------------------- | ------------ |
| (0,0)           | 1     | Count island; DFS sinks (0,0), (0,1), (1,0) | 1            |
| Remaining water | 0     | Skip                                        | 1            |
| (2,2)           | 1     | Count island; DFS sinks (2,2)               | 2            |
| End             | —     | Return count                                | 2            |

---

## Code

```javascript
var numIslands = function(grid) {
    const rows = grid.length;
    const cols = grid[0].length;
    let islands = 0;

    const dfs = (row, col) => {
        if (
            row < 0 ||
            row >= rows ||
            col < 0 ||
            col >= cols ||
            grid[row][col] !== "1"
        ) {
            return;
        }

        grid[row][col] = "0";

        dfs(row + 1, col);
        dfs(row - 1, col);
        dfs(row, col + 1);
        dfs(row, col - 1);
    };

    for (let row = 0; row < rows; row++) {
        for (let col = 0; col < cols; col++) {
            if (grid[row][col] === "1") {
                islands++;
                dfs(row, col);
            }
        }
    }

    return islands;
};
```

---

## Complexity

**Time**

```text
O(m × n)
```

**Space**

```text
O(m × n)
```

in the worst case because of the DFS recursion stack.

---

## Notes

✔ Treat each land cell as a graph node.

✔ Only horizontal and vertical neighbours connect; diagonals do not.

✔ Changing visited land to `"0"` avoids needing a separate visited set.

---

## Recognition

Use this pattern when you need to:

- Count connected components
- Traverse a 2D grid
- Explore all neighbouring cells with DFS or BFS
