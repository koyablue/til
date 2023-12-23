# Leet Code 567 Permutation in String

https://leetcode.com/problems/permutation-in-string/description/
# References

# Solution

```javascript
/**
 * @param {string} s1
 * @param {string} s2
 * @return {boolean}
 */
const checkInclusion = function(s1, s2) {
  if (s1.length > s2.length) return false;

  const neededChar = {}; // char count in s1
  for (let i = 0; i < s1.length; i++) {
    neededChar[s1[i]] = (neededChar[s1[i]] || 0) + 1;
  }

  let left = 0;
  let right = 0;
  let requiredLength = s1.length;

  while (right < s2.length) {
    if (s2[right] in neededChar) {
      neededChar[s2[right]]--; // can be negative number

      // if neededChar[s2[right]] is negative it means too many chars in the window
      // s1 = abc
      // s2 = bbbca
      // right = 0, 2 more chars are needed
      // right = 1, too many "b" and neededChar[s2[right]] is negative, and still 2 more chars are needed.
      // if requiredLength-- occur in that case, 3 more chars are needed but that is not correct. So check if (neededChar[s2[right]] >= 0) to skip that case
      if (neededChar[s2[right]] >= 0) requiredLength--;
    }

    right++; // expand the window

    if (requiredLength === 0) return true;

    if (right - left === s1.length) {
      if (s2[left] in neededChar) {
        // if neededChar[s2[left]] is positive: less needed chars appeared in the window
        // if neededChar[s2[left]] is 0: correct count of needed chars appeared in the window
        // if neededChar[s2[left]] is negative: too many needed chars appeared, so requiredLength is not going to increment
        // because if s1 has 1 "b"and s2 has 2 "b"s, and neededChar[s2[left]] is "b", the value must be the negative number
        // still 1 b is needed, not 2 b, so not increment
        if (neededChar[s2[left]] >= 0) requiredLength++;
        neededChar[s2[left]]++;
      }
      left++; //shift the window to right
    }
  }


  return false;
};
```

It was too difficult for me to fully understand the solution.
