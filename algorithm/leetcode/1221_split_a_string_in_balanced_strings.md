# Leet Code 1221 Split a String in Balanced Strings

https://leetcode.com/problems/split-a-string-in-balanced-strings/description/

# References

https://www.youtube.com/watch?v=-buRS1f7C8E

# Solution

```javascript
/**
 * @param {string} s
 * @return {number}
 */
const balancedStringSplit = (s) => {
  let balance = 0;
  let result = 0;

  for (let i = 0; i < s.length; i++) {
    s[i] === "R" ? balance-- : balance++;
    if (balance === 0) result++;
  }

  return result;
};
```
