# Leet Code 200 Number of Islands

https://leetcode.com/problems/number-of-islands/description/

# References

# Solution

```javascript
/**
 * @param {character[][]} grid
 * @return {number}
 */
const numIslands = (grid) => {
  if (!grid || !grid.length) return 0;

  const rows = grid.length;
  const cols = grid[0].length;
  let islandCount = 0;

  const dfs = (i, j) => {
    if (i < 0 || i >= rows || j < 0 || j >= cols || grid[i][j] === "0") return;
    grid[i][j] = "0";

    dfs(i - 1, j);
    dfs(i + 1, j);
    dfs(i, j - 1);
    dfs(i, j + 1);
  };

  for (let i = 0; i < rows; i++) {
    for (let j = 0; j < cols; j++) {
      if (grid[i][j] === "1") {
        islandCount++;
        dfs(i, j);
      }
    }
  }

  return islandCount;
};
```
