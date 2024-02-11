# Leet Code 543 Diameter of Binary Tree
https://leetcode.com/problems/balanced-binary-tree/description/
# References
https://www.youtube.com/watch?v=QfJsau0ItOY

https://leetcode.com/problems/balanced-binary-tree/solutions/2428871/very-easy-100-fully-explained-c-java-python-javascript-python3/

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
 * @return {boolean}
 */
const isBalanced = function(root) {
  if (root === null) return true;

  const getHeight = (root) => {
    if (root === null) return 0;

    const leftHeight = getHeight(root.left);
    const rightHeight = getHeight(root.right);

    if (leftHeight === -1 || rightHeight === -1) return -1;
    if (Math.abs(leftHeight - rightHeight) > 1) return -1;

    return Math.max(leftHeight, rightHeight) + 1;
  };

  if (getHeight(root) === -1) return false;
  return true;
};
```
