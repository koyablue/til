# Leet Code 82 Remove Duplicates from Sorted List II

https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/description/
# References
https://www.youtube.com/watch?v=R6-PnHODewY
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
const deleteDuplicates = function(head) {
  if (!head || !head.next) return head;

  const dummy = new ListNode(0, head);
  let curr = dummy;

  while (curr.next && curr.next.next) {
    if (curr.next.val === curr.next.next.val) {
      let dup = curr.next.next;
      while (dup.next && dup.val === dup.next.val) {
        dup = dup.next;
      }
      curr.next = dup.next;
    } else {
      curr = curr.next;
    }
  }

  return dummy.next;
};
```
