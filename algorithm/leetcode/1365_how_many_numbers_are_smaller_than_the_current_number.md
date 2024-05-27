# Leet Code 1365 How Many Numbers Are Smaller Than The Current Number

https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/description/

# References

https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/solutions/2837597/faster-than-100-simple-javascript-hashmap-solution/

# Solution

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
const smallerNumbersThanCurrent = function (nums) {
  // nums = [8,1,2,2,3]

  // Use slice() to avoid modifying the original array
  // sorted = [1, 2, 2, 3, 8]
  // Note:  [...arr].sort((a, b) => a - b); might be better
  const sorted = nums.slice().sort((a, b) => a - b);

  // {val: idx} of sorted
  // to count a number of smaller numbers
  // nums
  const map = {};
  for (let i = 0; i < sorted.length; i++) {
    // Skip if map has sorted[i] to avoid unnecessary update
    // ex) i = 2, sorted[2] = 2, map has {2: 1}
    // if map was updated, the value of map[2] would be 2, and that is not correct
    if (sorted[i] in map) continue;
    map[sorted[i]] = i;
  }
  // map = { 1: 0, 2: 1, 3: 3, 8: 4 }

  // Return new array
  // map is { valOfNums: countOfSmallerNumber } so just return map[n]
  return nums.map((n) => map[n]);
};
```
