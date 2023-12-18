# Leet Code 20 Valid Parentheses

https://leetcode.com/problems/valid-parentheses/description/
# References
https://www.youtube.com/watch?v=WTzjTskDFMg
# Solution

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
  const map = {
    ')': '(',
    '}': '{',
    ']': '[',
  };

  const stack = [];

  for (let i = 0; i < s.length; i++) {
    if (s[i] in map) {
      if (stack.length && stack[stack.length - 1] === map[s[i]]) {
        stack.pop();
        continue;
      }
    }

    stack.push(s[i]);
  }

  return stack.length === 0;
};
```
