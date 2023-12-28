# Leet Code 83 Remove Duplicates from Sorted List

https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/
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
const deleteDuplicates = function(head) {
  if (!head || !head.next) return head;

  let pointer = head;
  while (pointer && pointer.next) {
    if (pointer.val === pointer.next.val) {
      pointer.next = pointer.next.next;
    } else {
      pointer = pointer.next;
    }
  }

  return head;
};
```
