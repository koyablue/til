# Leet Code 78 Subsets

https://leetcode.com/problems/subsets/description/

# References

https://leetcode.com/problems/subsets/solutions/940599/3-approaches-for-your-interview-dry-run-iterative-recursive-bitmasking/

# Solution

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
const subsets = (nums) => {
  const res = [[]];

  for (let n of nums) {
    const appendarr = [];
    for (let subset of res) {
      appendarr.push([...subset, n]);
    }
    res.push(...appendarr);
  }

  return res;
};
```
