# Leet Code 49 Group Anagrams

https://leetcode.com/problems/group-anagrams/

# References
https://www.youtube.com/watch?v=vzdNOK2oB2E

# Solution

```javascript
/**
 * @param {string[]} strs
 * @return {string[][]}
 */
const groupAnagrams = (strs) => {
  // this obj will look like this:
  // {'1#0#0#...': ['abc', 'bca'...],}
  const anagrams = {};

  for (let str of strs) {
    // Alphabet has 26 characters so create a 26 length empty array
    const countList = Array(26).fill(0);

    for (let char of str) {
      // char.charCodeAt(0) - 'a'.charCodeAt(0) determine the place of character
      countList[char.charCodeAt(0) - 'a'.charCodeAt(0)]++;
    }

    // use # for delimiter because if you use ',' it creates ambiguous string
    // if you use comma [11,1] and [1,11] become the same string '1,1,1'
    const key = countList.join('#');
    if (!(key in anagrams)) {
      anagrams[key] = [];
    }

    anagrams[key].push(str);
  }

  // don't need to return with key so return the array of values
  return Object.values(anagrams);
};
```