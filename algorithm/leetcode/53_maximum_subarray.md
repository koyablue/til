# Leet Code 53 Maximum Subarray

https://leetcode.com/problems/maximum-subarray/description/

# References
https://www.youtube.com/watch?v=5WZl3MMT0Eg&t=277s

# Solution

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
const maxSubArray = (nums) => {
  let maxSub = nums[0];
  let currSub = 0;

  for (let i = 0; i < nums.length; i++) {
    // Negative value doesn't contribute so it currSub is negative, reset to 0
    if (currSub < 0) currSub = 0;

    currSub += nums[i];

    maxSub = Math.max(currSub, maxSub);
  }

  return maxSub;
}
```
