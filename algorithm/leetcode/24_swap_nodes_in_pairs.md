# Leet Code 24 Swap Nodes in Pairs

https://leetcode.com/problems/swap-nodes-in-pairs/description/
# References
https://www.youtube.com/watch?v=o811TZLAWOo
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
const swapPairs = function(head) {
  const dummy = new ListNode(0, head);
  let prev = dummy;
  let curr = head; //1

  // d,1,2,3,4
  while (curr && curr.next) {
    let second = curr.next; // 2
    let nextPair = curr.next.next; // 3

    prev.next = second;
    second.next = curr;
    curr.next = nextPair;
    // d,2,1,3,4

    prev = curr; // 1
    curr = curr.next; // 3(nextPair)
  }

  return dummy.next;
};
```
