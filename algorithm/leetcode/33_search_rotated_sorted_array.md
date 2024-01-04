# Leet Code 153 Find Minimum in Rotated Sorted Array
https://leetcode.com/problems/search-in-rotated-sorted-array/description/
# References
https://www.youtube.com/watch?v=U8XENwh8Oy8
# Solution

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
const search = (nums, target) => {
  let leftI = 0;
  let rightI = nums.length - 1;

  while (leftI <= rightI) {
    const midI = Math.floor((leftI + rightI) / 2);
    if (nums[midI] === target) return midI;

    if (nums[leftI] <= nums[midI]) {
      if (target < nums[leftI] || nums[midI] < target) {
        leftI = midI + 1;
      } else {
        rightI = midI - 1;
      }
    } else {
      if (nums[rightI] < target || target < nums[midI]) {
        rightI = midI - 1;
      } else {
        leftI = midI + 1;
      }
    }
  }

  return - 1;
};
```
