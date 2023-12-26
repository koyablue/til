# Leet Code 141 Linked List Cycle

https://leetcode.com/problems/linked-list-cycle/description/
# References
https://www.youtube.com/watch?v=gBTe7lFR3vc
# Solution

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */

/**
 * @param {ListNode} head
 * @return {boolean}
 */
const hasCycle = function(head) {
  // slow = head, fast = head
  // loop while head.next
  // slow = slow.next, fast = fast.next.next
  // if slow and fast meet, return true

  if (!head || !head.next) return false;

  let slow = head;
  let fast = head;

  while (fast && fast.next) {
    slow = slow.next;
    fast = fast.next.next;

    if (slow === fast) return true;
  }

  return false;
};
```
