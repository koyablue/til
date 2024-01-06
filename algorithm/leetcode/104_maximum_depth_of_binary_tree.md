# Leet Code 145  Binary Tree Postorder Traversal
https://leetcode.com/problems/maximum-depth-of-binary-tree/description/
# References
https://www.youtube.com/watch?v=hTM3phVI6YQ&t=274s

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
 * @return {number}
 */
const maxDepth = function(root) {
  const dfs = (node, count) => {
    if (!node) return count;
    count++;

    return Math.max(dfs(node.left, count), dfs(node.right, count));
  };

  return dfs(root, 0);
};
```
