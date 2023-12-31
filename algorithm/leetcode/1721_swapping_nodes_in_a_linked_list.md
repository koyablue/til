# Leet Code 1721 Swapping Nodes in a Linked List

https://leetcode.com/problems/swapping-nodes-in-a-linked-list/description/
# References
https://www.youtube.com/watch?v=4LsrgMyQIjQ
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
 * @param {number} k
 * @return {ListNode}
 */
const swapNodes = function(head, k) {
  let curr = head;
  for (let i = 0; i < k - 1; i++) {
    curr = curr.next;
  }

  slow = head;
  fast = curr;
  while (fast.next) {
    slow = slow.next;
    fast = fast.next;
  }

  const tmpCurrVal = curr.val
  curr.val = slow.val;
  slow.val = tmpCurrVal;

  return head;
};
```
