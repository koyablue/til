# Leet Code 3 Longest Substring Without Repeating Characters

https://leetcode.com/problems/longest-substring-without-repeating-characters/description/
# References
https://www.youtube.com/watch?v=wiGpQwVHdE0
# Solution

```javascript
/**
 * @param {string} s
 * @return {number}
 */
const lengthOfLongestSubstring = function(s) {
  let charSet = new Set();
  let left = 0;
  let res = 0;

  for (let i = 0; i < s.length; i++) {
    while (charSet.has(s[i])) {
      charSet.delete(s[left]);
      left++;
    }

    charSet.add(s[i]);
    res = Math.max(res, i - left + 1);
  }

  return res;
}

```
