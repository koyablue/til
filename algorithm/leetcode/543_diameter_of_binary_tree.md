# Leet Code 543 Diameter of Binary Tree
https://leetcode.com/problems/diameter-of-binary-tree/description/
# References
https://leetcode.com/problems/diameter-of-binary-tree/solutions/101148/intuitive-javascript-solution/

https://www.youtube.com/watch?v=bkxqA8Rfv04

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
const diameterOfBinaryTree = function(root) {
  // dfs(node)
  // until node ends
  // go left sub tree
  // go right sub tree
  // update diameter
  // return height of the sub tree rooted at the current node

  let diameter = 0;

  const dfs = (node) => {
    if (!node) return 0;

    const left = dfs(node.left);
    const right = dfs(node.right);

    diameter = Math.max(diameter, (left + right));
    return 1 + Math.max(left, right);
  };

  // initi diameter
  // dfs: update diameter inside
  // return updated deameter
  dfs(root);

  return diameter;
};
```

too difficult for me
