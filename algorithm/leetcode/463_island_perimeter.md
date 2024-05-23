# Leet Code 463 Island Perimeter

https://leetcode.com/problems/island-perimeter/description/

# References

https://leetcode.com/problems/island-perimeter/solutions/5039530/beated-island-perimeter/

# Solution

```javascript
/**
 * @param {number[][]} grid
 * @return {number}
 */
const islandPerimeter = (grid) => {
  const rows = grid.length; // number of vertical lines
  const cols = grid[0].length; // number of items inside a row
  let perimeter = 0; // value to return

  // iterate rows
  // iterate columns inside rows iteration
  for (let i = 0; i < rows; i++) {
    for (let j = 0; j < cols; j++) {
      // if the value is 0(no land. water) skip the calculation because it's 0
      if (grid[i][j] === 0) continue;

      // add 4 because a land has 4 sides initially
      perimeter += 4;

      // check if the cell above is land
      // if so substract a number of overlapped sides from perimeter
      if (i > 0 && grid[i - 1][j] === 1) {
        perimeter -= 2;
      }

      // check if the cell on the left is land
      // if so substract a number of overlapped sides from perimeter
      if (j > 0 && grid[i][j - 1] === 1) {
        perimeter -= 2;
      }
    }
  }

  return perimeter;
};
```
