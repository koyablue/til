# Leet Code 217 Contains Duplicate

https://leetcode.com/problems/contains-duplicate/description/

# References

# Solution

```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
const containsDuplicate = (nums) => {
  const map = {};

  for (let n of nums) {
    if (n in map) return true;

    map[n] = 1;
  }

  return false;
};
```
