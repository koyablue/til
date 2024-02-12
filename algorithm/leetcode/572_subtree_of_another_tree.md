# Leet Code 572 Subtree of Another Tree
https://leetcode.com/problems/subtree-of-another-tree/description/

# References
https://www.youtube.com/watch?v=E36O5SWp-LE

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
 * @param {TreeNode} subRoot
 * @return {boolean}
 */
const isSubtree = (root, subRoot) => {
  const isSameTree = (root, subRoot) => {
    if (root === null && subRoot === null) return true;
    if (root === null || subRoot === null) return false;
    if (root.val !== subRoot.val) return false;

    return isSameTree(root.left, subRoot.left) && isSameTree(root.right, subRoot.right);
  };

  if (subRoot === null) return true;
  if (root === null) return false;
  if (isSameTree(root, subRoot)) return true;

  return isSubtree(root.left, subRoot) || isSubtree(root.right, subRoot);
};
```
