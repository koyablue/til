# Leet Code 953 Verifying an Alien Dictionary

https://leetcode.com/problems/verifying-an-alien-dictionary/description/

# References

https://www.youtube.com/watch?v=OVgPAJIyX6o

# Solution

```javascript
/**
 * @param {string[]} words
 * @param {string} order
 * @return {boolean}
 */
const isAlienSorted = function (words, order) {
  const orderCharIdx = {};
  for (let i = 0; i < order.length; i++) {
    orderCharIdx[order[i]] = i;
  }

  // words.length - 1
  // it uses 2 pointers and compare adjacent elements
  // if the condition is i < words.length, w2 would be undefined at some point
  // because words[i + 1] might not be in the array
  // that's why -1 is necessary
  for (let i = 0; i < words.length - 1; i++) {
    let w1 = words[i];
    let w2 = words[i + 1];

    for (let j = 0; j < w1.length; j++) {
      if (j === w2.length) return false;
      if (w1[j] !== w2[j]) {
        if (orderCharIdx[w2[j]] < orderCharIdx[w1[j]]) return false;
        break;
      }
    }
  }

  return true;
};
```
