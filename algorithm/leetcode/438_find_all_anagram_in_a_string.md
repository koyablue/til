# Leet Code 438 Find All Anagram In a String

https://leetcode.com/problems/find-all-anagrams-in-a-string/description/

# References
https://www.youtube.com/watch?v=G8xtZy0fDKg

https://leetcode.com/problems/find-all-anagrams-in-a-string/solutions/1025753/simplest-sliding-window-solution-o-n-heavily-commented-javascript/

# Solution

```javascript
const findAnagrams = (s, p) => {
  if (p.length > s.length) return [];

  // if p = a,b,c => {a:1, b:1, c:1}
  // shows how many of the chars are needed in the sliding window
  // a:2 means 2 'a's are needed
  // a:0 means correct amount of a exists in the window
  // a:-2 means 2 extra 'a's are in the window 
  const neededChars = {};
  const res = [];

  // build hashmap
  for (let char of p) {
    if (!neededChars[char]) {
      neededChars[char] = 1;
      continue;
    }
    neededChars[char]++;
  }

  // window (of sliding window = range of left ~ right)
  let left = 0;
  let right = 0;

  // how many more chars are needed for the letters in the window
  // to become an anagram of p
  // ex) s = "cbaebabacd", p = "abc", left = 1, right = 3
  // window is "bae" and count = 1
  // means 1 more char is needed to be the anagram
  // so when count=0, means that window is anagram of p,
  // so push the first index of the window to res[]. 
  let count = p.length;

  while (right < s.length) {
    if (neededChars[s[right]] !== undefined) {
      if (neededChars[s[right]] > 0) {
        count--;
      }
      // if the char appears in s more often than it exists in p,
      // value of neededChars will be negative
      neededChars[s[right]]--;
    }
    right++; // change window size

    // count === 0 means the set of chars in the window is anagram 
    if (count === 0) {
      res.push(left);
    }

    // adjust the window size
    if (right - left === p.length) {
      // if neededChars[s[left]] is needed but going to be out of the window
      // means that char is needed in the next window, so increase count
      if (neededChars[s[left]] !== undefined) {
        if (neededChars[s[left]] >= 0) {
          count++;
        }
        neededChars[s[left]]++;
      }
      left++; // move left when the window size reaches p.length
    }
  }

  return res;
};
```