# Leet Code 704 Binary Search

https://leetcode.com/problems/binary-search/description/
# References

# Solution

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
const search = function(nums, target) {
  let left = 0;
  let right = nums.length - 1;

  // use <= for nums.length = 1
  while (left <= right) {
    const midIdx = Math.floor((left + right) / 2);
    if (nums[midIdx] < target) {
      left = midIdx + 1;
    } else if (target < nums[midIdx]) {
      right = midIdx - 1;
    } else {
      return midIdx;
    }
  }

  return -1;
};
```

Recursive version
```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
const search = function(nums, target) {
  const _search = (left, right) => {
    if (left > right) return -1;

    const midIdx = Math.floor((left + right) / 2);
    if (nums[midIdx] < target) {
      return _search(midIdx + 1, right);
    } else if (target < nums[midIdx]) {
      return _search(left, midIdx - 1);
    } else {
      return midIdx;
    }
  };

  return _search(0, nums.length - 1);
};

```
