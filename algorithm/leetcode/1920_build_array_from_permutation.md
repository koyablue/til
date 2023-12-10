# Leet Code 1920 Build Array From Permutation

https://leetcode.com/problems/build-array-from-permutation/description/
# References

# Solution

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
const buildArray = (nums) => {
  const res = [];
  for (let i = 0; i < nums.length; i++) {
    res.push(nums[nums[i]]);
  }

  return res;
};
```
