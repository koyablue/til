# Leet Code 1002 Find Common Characters

https://leetcode.com/problems/find-common-characters/description/
# References
https://www.youtube.com/watch?v=k1iowWJimbg
# Solution

```javascript
/**
 * @param {string[]} words
 * @return {string[]}
 */
const commonChars = function(words) {
  // Make an 26 length array filled with Infinity. This array is going to be used for tracking minimum frequency of each characters.
  const minFreq = new Array(26).fill(Infinity);
  // Get ascii code of 'a'
  const charCodeA = 'a'.charCodeAt(0);

  // loop words
  for (let word of words) {
    // init an array for tracking frequency of each characters in the item of words
    const wordCharFreq = new Array(26).fill(0);
    // loop word
    for (let c of word) {
      // increment the place of the char that appears in word
      wordCharFreq[c.charCodeAt(0) - charCodeA]++;
    }

    // loop 26 times
    for (let i = 0; i < 26; i++) {
      // set minFreq[i] = Min(minFreq[i], wordCharFreq[i])
      // char that doesn't appear in the word -> 0
      minFreq[i] = Math.min(minFreq[i], wordCharFreq[i])
    }
  }

  // init result array
  const res = [];
  // push the char for the number of times that appears
  for (let i = 0; i < 26; i++) {
    for (let j = 0; j < minFreq[i]; j++) {
      res.push(String.fromCharCode(i + charCodeA));
    }
  }

  return res;
};
```
