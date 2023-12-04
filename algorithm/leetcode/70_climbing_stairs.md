# Leet Code 70 Climbing Stairs

https://leetcode.com/problems/climbing-stairs/description/

# References
https://www.youtube.com/watch?v=Y0lT9Fck7qI

# Solution

```javascript
/**
 * @param {number} n
 * @return {number}
 */
const climbStairs = (n) => {
  let one = 1;
  let two = 1;

  for (let i = 0; i < n - 1; i++) {
    let prevOne = one;
    one = one + two;
    two = prevOne;
  }

  return one;
};
```
