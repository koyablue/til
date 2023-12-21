# Leet Code 167 Two Sum II - Input Array Is Sorted

https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/
# References
https://www.youtube.com/watch?v=cQ1Oz4ckceM
# Solution

```javascript
/**
 * @param {number[]} numbers
 * @param {number} target
 * @return {number[]}
 */
const twoSum = function(numbers, target) {
  // l = 0, r = numbers.length - 1
  // numbers[l] + numbers[r] === target: return [l+1, r+1]
  // sum target then l++ else r--

  let l = 0;
  let r = numbers.length - 1;

  while (l < r) {
    const currentSum = numbers[l] + numbers[r];
    if (currentSum === target) return [l + 1, r + 1];

    currentSum < target ? l++ : r--;
  }
};
```
