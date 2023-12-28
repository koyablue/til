# Leet Code 19 Remove Nth Node From End of List

https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/
# References
https://www.youtube.com/watch?v=XVuQxVej6y8
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
 * @param {ListNode} head
 * @param {number} n
 * @return {ListNode}
 */
const removeNthFromEnd = function(head, n) {
  const dummy = new ListNode(0, head);
  let left = dummy;

  let right = head;
  while (n !== 0) {
    right = right.next;
    n--;
  }

  while (right) {
    left = left.next;
    right = right.next;
  }

  left.next = left.next.next;

  return dummy.next;
};
```
