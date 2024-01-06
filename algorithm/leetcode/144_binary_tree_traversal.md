# Leet Code 144  Binary Tree Preorder Traversal
https://leetcode.com/problems/binary-tree-preorder-traversal/description/
# References
https://www.youtube.com/watch?v=afTpieEZXck
# Solution

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[]}
 */
const preorderTraversal = function(root) {
  let current = root;
  const rightStack = [];
  const res = [];

  while (current || rightStack.length) {
    if (current) {
      rightStack.push(current.right);
      res.push(current.val);
      current = current.left;
    } else {
      current = rightStack.pop();
    }
  }

  return res;
};
```