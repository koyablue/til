# Leet Code 153 Find Minimum in Rotated Sorted Array
https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/
# References
https://www.youtube.com/watch?v=nIVW4P8b1VA
# Solution

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
const findMin = function(nums) {
  let res = nums[0];

  let left = 0;
  let right = nums.length - 1;

  while (left <= right) {
    if (nums[left] < nums[right]) {
      res = Math.min(res, nums[left]);
      break;
    }

    const mid = Math.floor((left + right) / 2);
    res = Math.min(res, nums[mid]);
    if (nums[left] <= nums[mid]) {
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }

  return res;
};
```
