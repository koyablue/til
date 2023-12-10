# Leet Code 929 Unique Email Addresses

https://leetcode.com/problems/unique-email-addresses/description/

# References

# Solution

```javascript
/**
 * @param {string[]} emails
 * @return {number}
 */
const numUniqueEmails = (emails) => {
  // alice.z@leetcode.com = alicez@leetcode.com
  // m.y+name@email.com = my@email.com
  // split @ => local,domain
  // local local.split('+')[0].replace('.', '')
  // local + @ + domain
  // add to Set

  const unique = new Set();

  for (let email of emails) {
    let [local, domain] = email.split('@');
    local = local.split('+')[0].replaceAll('.', '');

    unique.add(`${local}@${domain}`);
  }

  return unique.size;
};
```
