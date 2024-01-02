# Leet Code 875 Koko Eating Bananas

https://leetcode.com/problems/koko-eating-bananas/description/
# References
https://www.youtube.com/watch?v=U2SozAs9RzA
# Solution

```javascript
/**
 * @param {number[]} piles
 * @param {number} h
 * @return {number}
 */
const minEatingSpeed = function(piles, h) {
  let l = 1;
  let r = Math.max(...piles);
  let res = r;

  while (l <= r) {
    const k = Math.floor((l + r) /2 );
    let hours = 0;

    for (let p of piles) {
      hours += Math.ceil(p / k);
    }

    if (hours <= h) {
      res = Math.min(res, k);
      r = k - 1;
    } else {
      l = k + 1;
    }
  }

  return res;
};
```
