# Leet Code 2 Reorder List

https://leetcode.com/problems/reorder-list/description/
# References
https://www.youtube.com/watch?v=S5bfdUTrKLM
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
 * @return {void} Do not return anything, modify head in-place instead.
 */
const reorderList = function(head) {
  // split
  let slow = head;
  let fast = head.next;
  while (fast && fast.next) {
    slow = slow.next;
    fast = fast.next.next;
  }

  let second = slow.next;
  slow.next = null;

  //reverse second
  let prev = null;
  while (second) {
    const tmpNext = second.next;
    second.next = prev;
    prev = second;
    second = tmpNext;
  }

  // merge
  let first = head;
  second = prev;

  // the second half could be shorter than the first half when the number of list is odd
  // 1,2,3,4,5 -> 1,2,3 / 4,5 (second half starts with slow.next)
  while (second) {
    const tmp1 = first.next;
    const tmp2 = second.next;
    first.next = second;
    second.next = tmp1
    first = tmp1;
    second = tmp2;
  }
};
```
