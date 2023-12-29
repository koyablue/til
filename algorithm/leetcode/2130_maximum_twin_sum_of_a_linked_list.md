# Leet Code 2130 Maximum Twin Sum of a Linked List

https://leetcode.com/problems/maximum-twin-sum-of-a-linked-list/description/
# References
https://www.youtube.com/watch?v=doj95MelfSA
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
 * @return {number}
 */
const pairSum = function(head) {
  // slow, fast
  let slow = head;
  let fast = head;

  let prev = null;
  // loop
  while (fast && fast.next) {
    // split the list
    fast = fast.next.next;

    // reverse left list
    const tmpSlowNext = slow.next;
    slow.next = prev;
    prev = slow;
    slow = tmpSlowNext;
  }

  let res = 0
  // while slow(first node of right list, prev is the last node in left list)
  while (slow) {
    res = Math.max(res, prev.val + slow.val);
    prev = prev.next;
    slow = slow.next;
  }

  return res;
};
```
