# Leet Code 145  Binary Tree Postorder Traversal
https://leetcode.com/problems/invert-binary-tree/description/
# References
https://www.youtube.com/watch?v=OnSn2XEQ4MY

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
 * @return {TreeNode}
 */
const invertTree = function(root) {
  if (!root) return null;

  const tmp = root.left;
  root.left = root.right;
  root.right = tmp;

  invertTree(root.left);
  invertTree(root.right);
  return root;
};
```
