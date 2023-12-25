# Leet Code 71 Simplify Path

https://leetcode.com/problems/simplify-path/description/
# References
https://www.youtube.com/watch?v=qYlHrAKJfyA
# Solution

```javascript
/**
 * @param {string} path
 * @return {string}
 */
const simplifyPath = function(path) {
  const stack = [];
  let curr = '';

  for (let c of path + '/') {
    if (c === '/') {
      if (curr === '..') {
        stack.length && stack.pop();
      } else if (curr !== '' && curr !== '.') {
        stack.push(curr);
      }
      curr = '';
    } else {
      curr += c;
    }
  }

  return '/' + stack.join('/');
};
```
