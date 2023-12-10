# Leet Code 1 Two Sum

https://leetcode.com/problems/two-sum/

# References

# Solution

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
const twoSum = (nums, target) => {
  // nums = [2,7,11,15], target = 9
  // return [0,1]

  // i=0 2, 9 - 2 = 7

  // { 2: 0 }
  const valIdx = {};

  for (let i = 0; i < nums.length; i++) {
    const diff = target - nums[i];
    if (diff in valIdx) return [valIdx[diff], i];

    valIdx[nums[i]] = i;
  }

  return [];
};
```
