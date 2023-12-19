# Leet Code 347 Top K Frequent Elements

https://leetcode.com/problems/top-k-frequent-elements/description/
# References
https://www.youtube.com/watch?v=YPTqKIgVk-k
# Solution

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
const topKFrequent = function(nums, k) {
  // nums = [1,1,1,2,2,2,3,4,4] k = 2

  // count = { 1: 3, 2: 3, 3: 1, 4: 2 }
  //         0    1     2     3     4   5   6   7   8   9   10 times
  // freq = [[], [3], [4], [1, 2], [], [], [], [], [], [], []]
  // res = []
  // iterate freq from right to left
  // iterate freq[i]
  // res.push(n)
  // if res.length === k return res;

  const count = {};
  for (let n of nums) {
    count[n] = (count[n] || 0) + 1;
  }

  const freq = Array.from({ length: nums.length + 1 }, () => []);
  for (const [k, v] of Object.entries(count)) {
    freq[v].push(k);
  }

  const res = [];
  for (let i = freq.length - 1; i >= 0; i--) {
    for (n of freq[i]) {
      res.push(n);
      if (res.length === k) return res;
    }
  }
};
```
