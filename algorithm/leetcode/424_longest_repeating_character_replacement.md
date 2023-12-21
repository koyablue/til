# Leet Code 424 Longest Repeating Character Replacement

https://leetcode.com/problems/longest-repeating-character-replacement/description/
# References
https://www.youtube.com/watch?v=gqXU1UyA8pk
# Solution

```javascript
/**
 * @param {string} s
 * @param {number} k
 * @return {number}
 */
const characterReplacement = function(s, k) {
  const count = {};
  let left = 0;
  let res = 0;

  for (let i = 0; i < s.length; i++) {
    count[s[i]] = (count[s[i]] || 0) + 1;

    while (i - left + 1 - Math.max(...Object.values(count)) > k) {
      count[s[left]]--;
      left++;
    }

    res = Math.max(res, i - left + 1);
  }

  return res;
};

```
