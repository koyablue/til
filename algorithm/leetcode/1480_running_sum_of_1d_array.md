# Leet Code 1480 Running Sum of 1d Array

https://leetcode.com/problems/running-sum-of-1d-array/description/
# References

# Solution

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
const runningSum = (nums) => {
  const res = [];
  res.push(nums[0]);

  for (let i = 1; i < nums.length; i++) {
    res.push(res[i-1] + nums[i]);
  }

  return res;
};
```
