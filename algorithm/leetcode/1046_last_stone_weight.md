# Leet Code 1046 Last Stone Weight

https://leetcode.com/problems/last-stone-weight/description/

# References

https://www.youtube.com/watch?v=B-QCq79-Vfw

# Solution

```javascript
/**
 * @param {number[]} stones
 * @return {number}
 */
const lastStoneWeight = function (stones) {
  while (stones.length > 1) {
    stones.sort((a, b) => b - a);
    stones[1] = stones[0] - stones[1];
    stones.shift();
  }

  return stones[0] || 0;
};
```
