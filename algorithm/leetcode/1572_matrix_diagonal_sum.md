# Leet Code 1920 Build Array From Permutation

https://leetcode.com/problems/matrix-diagonal-sum/description/
# References
https://www.youtube.com/watch?v=WliTu6gIK7o
# Solution

```javascript
/**
 * @param {number[][]} mat
 * @return {number}
 */
const diagonalSum = (mat) => {
  let res = 0;
  const midVal = Math.floor(mat.length / 2)

  for (let i = 0; i < mat.length; i++) {
    res += mat[i][i]; // first diagonal
    res += mat[i][mat.length - 1 - i]; //second diagonal
  }

  return mat.length % 2 === 0
    ? res
    : res - mat[midVal][midVal]
};
```
