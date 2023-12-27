# Leet Code 155 Min Stack
https://leetcode.com/problems/middle-of-the-linked-list/description/
# References
https://www.youtube.com/watch?v=A2_ldqM4QcY
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
 * @return {ListNode}
 */
const middleNode = function(head) {
  if (!head.next) return head;

  let slow = head;
  let fast = head;

  while (fast && fast.next) {
    slow = slow.next;
    fast = fast.next.next;
  }

  return slow;
};
```
