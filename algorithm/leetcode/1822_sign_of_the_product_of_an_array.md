# Leet Code 125 Valid Palindrome

https://leetcode.com/problems/sign-of-the-product-of-an-array/description/
# References
# Solution

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
const arraySign = (nums) => {
  let res = 1;

  for (let i = 0; i < nums.length; i++) {
    if (nums[i] === 0) return 0;
    if (nums[i] < 0) res = -res;
  }

  return res;
};
```
