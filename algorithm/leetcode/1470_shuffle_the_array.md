# Leet Code 1470 Shuffle the Array

https://leetcode.com/problems/shuffle-the-array/description/

# References

# Solution

```javascript
/**
 * @param {number[]} nums
 * @param {number} n
 * @return {number[]}
 */
const shuffle = (nums, n) => {
  // nums = [2,5,1,3,4,7], n = 3
  // x1=2, x2=5, x3=1 | y1=3, y2=4, y3=7
  // res = [0,3,2,4,3,5]
  const res = [];
  for (let i = 0; i < n; i++) {
    res.push(nums[i], nums[i+n]);
  }

  return res;
};
```
