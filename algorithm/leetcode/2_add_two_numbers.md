# Leet Code 2 Add Two Numbers

https://leetcode.com/problems/add-two-numbers/description/
# References
https://www.youtube.com/watch?v=wgFPrzTjm7s
# Solution

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
const addTwoNumbers = function(l1, l2) {
  const dummy = new ListNode();
  let pointer = dummy;
  let carry = 0;

  while (l1 || l2 || carry) {
    let val = (l1?.val || 0) + (l2?.val || 0) + carry;
    carry = Math.floor(val / 10);
    val = val % 10;
    pointer.next = new ListNode(val);

    pointer = pointer.next;
    l1 = l1?.next || null;
    l2 = l2?.next || null;
  }

  return dummy.next;
};
```
