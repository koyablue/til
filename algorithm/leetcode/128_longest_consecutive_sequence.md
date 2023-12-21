# Leet Code 128 Longest Consecutive Sequence

https://leetcode.com/problems/longest-consecutive-sequence/description/
# References
# Solution

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
const longestConsecutive = function(nums) {
  if (!nums.length) return 0;

  const map = {};
  for (let n of nums) {
    map[n] = 1;
  }

  let longest = 0;
  for (let k of Object.keys(map)) {
    // find the first element of the sequence
    let currentNum = Number(k);
    if ((currentNum - 1) in map) continue; // because this is not the first element

    let currentLongest = 1;
    while ((currentNum + 1) in map) {
      currentNum++;
      currentLongest++;
    }

    longest = Math.max(longest, currentLongest);
  }

  return longest;
};
```
