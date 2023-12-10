# Leet Code 1512 Number of Good Pairs

https://leetcode.com/problems/number-of-good-pairs/description/
# References

https://www.youtube.com/watch?v=BqhDFUo1rjs

# Solution

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
const numIdenticalPairs = (nums) => {
  // nums = [1,2,3,1,1,3]
  // numCount = {} n -> c
  // res = 0

  // nums[0] {1: 1}
  // ...
  // nums[3] => (nums[0], nums[3]) => 1 pair(res += numCount[nums[3]])

  const numCount = {};
  let res = 0;

  for (let i = 0; i < nums.length; i++) {
    if (nums[i] in numCount) {
      res += numCount[nums[i]];
      numCount[nums[i]] += 1;
      continue;
    }

    numCount[nums[i]] = 1;
  }

  return res;
};
```
