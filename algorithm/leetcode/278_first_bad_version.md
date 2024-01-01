# Leet Code 278 First Bad Version

https://leetcode.com/problems/first-bad-version/description/
# References

# Solution

```javascript
/**
 * Definition for isBadVersion()
 *
 * @param {integer} version number
 * @return {boolean} whether the version is bad
 * isBadVersion = function(version) {
 *     ...
 * };
 */

/**
 * @param {function} isBadVersion()
 * @return {function}
 */
const solution = function(isBadVersion) {
    // n: number
    // return number
    return function(n) {
      let left = 1;
      let right = n;

      while (left <= right) {
        const mid = Math.floor((left + right) / 2);
        if (isBadVersion(mid)) {
          right = mid - 1;
        } else {
          left = mid + 1;
        }
      }

      return left;
    };
};
```
