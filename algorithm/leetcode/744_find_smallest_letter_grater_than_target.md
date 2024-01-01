# Leet Code 278 First Bad Version

https://leetcode.com/problems/find-smallest-letter-greater-than-target/description/
# References

# Solution

```javascript
/**
 * @param {character[]} letters
 * @param {character} target
 * @return {character}
 */
const nextGreatestLetter = function(letters, target) {
  if (target < letters[0] || letters[letters.length - 1] <= target) return letters[0];

  let left = 0;
  let right = letters.length - 1;

  while (left <= right) {
    const mid = Math.floor((left + right) / 2);
    if (target < letters[mid]) {
      right = mid - 1;
    } else {
      left = mid + 1;
    }
  }

  return letters[left];
};
```
