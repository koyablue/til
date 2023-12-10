# Leet Code 242 Valid Anagram

https://leetcode.com/problems/valid-anagram/
# References

# Solution

```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
const isAnagram = (s, t) => {
  // isAnagram(s, t) is true
  // -> the same letters appear the same times in s and t
  // count which letter appears how many times

  // { char: count }
  const charCount =  {};

  for (let i = 0; i < s.length; i++) {
    if (!(s[i] in charCount)) {
      charCount[s[i]] = 1;
      continue;
    }

    charCount[s[i]] = charCount[s[i]] + 1;
  }

  for (let i = 0; i < t.length; i++) {
    if (t[i] in charCount) {
      charCount[t[i]] = charCount[t[i]] - 1;
      continue;
    }

    charCount[t[i]] = 1;
  }

  for (const[_, v] of Object.entries(charCount)) {
    if (v !== 0) return false;
  }

  return true;
};
```
