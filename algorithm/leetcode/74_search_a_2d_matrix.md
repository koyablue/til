# Leet Code 74 Search a 2D Matrix

https://leetcode.com/problems/search-a-2d-matrix/description/
# References
https://www.youtube.com/watch?v=Ber2pi2C0j0
# Solution

```javascript
/**
 * @param {number[][]} matrix
 * @param {number} target
 * @return {boolean}
 */
const searchMatrix = function(matrix, target) {
  const rowLen = matrix.length - 1;
  const colLen = matrix[0].length - 1;

  let top = 0;
  let bottom = rowLen;
  while (top <= bottom) {
    const mid = Math.floor((top + bottom) / 2);
    if (target < matrix[mid][0]) {
      bottom = mid - 1;
    } else if (target > matrix[mid][colLen]) {
      top = mid + 1;
    } else {
      break;
    }
  }

  if (!(top <= bottom)) return false;

  let l = 0;
  let r = colLen;
  const rowIdx = Math.floor((top + bottom) / 2);
  while (l <= r) {
    const m = Math.floor((l + r) / 2);
    if (target < matrix[rowIdx][m]) {
      r = m - 1;
    } else if (target > matrix[rowIdx][m]) {
      l = m + 1;
    } else {
      return true;
    }
  }

  return false;
};
```
