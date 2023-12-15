# Leet Code 125 Valid Palindrome

https://leetcode.com/problems/valid-palindrome/description/
# References
# Solution

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
const isPalindrome = (s) => {
   s = s.toLowerCase().replaceAll(/[^A-Za-z0-9]/g, "");
   let left = 0;
   let right = s.length - 1;

   while (left < right) {
     if (s[left] !== s[right]) return false;
     left++;
     right--;
   }

   return true;
};
```
