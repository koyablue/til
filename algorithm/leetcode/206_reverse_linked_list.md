# Leet Code 206 Reverse Linked List

https://leetcode.com/problems/reverse-linked-list/description/
# References

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
var reverseList = function(head) {
  if (!head || !head.next) return head;

  let prev = null;
  let current = head;

  while (current) {
    const currentNext = current.next;
    current.next = prev;
    prev = current;
    current = currentNext;
  }

  return prev;
};
```
