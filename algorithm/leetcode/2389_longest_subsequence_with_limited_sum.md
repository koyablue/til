# Leet Code 953 Verifying an Alien Dictionary

https://leetcode.com/problems/longest-subsequence-with-limited-sum/description/
# References
https://leetcode.com/problems/longest-subsequence-with-limited-sum/solutions/2776828/js-very-easy-and-fast-solution/
# Solution

```javascript
/**
 * @param {number[]} nums
 * @param {number[]} queries
 * @return {number[]}
 */
const answerQueries = function(nums, queries) {
  nums.sort((a, b) => a - b);
  const res = [];

  for (let i = 0; i < queries.length; i++) {
    let sum = 0;
    for (let j = 0; j < nums.length; j++) {
      sum += nums[j];
      if (sum > queries[i]) {
        res.push(j);
        break;
      }
    }
    if (res[i] === undefined) res.push(nums.length);
  }

  return res;
};
```
