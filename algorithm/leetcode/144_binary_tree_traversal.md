# Leet Code 144  Binary Tree Preorder Traversal
https://leetcode.com/problems/binary-tree-preorder-traversal/description/
# References
https://www.youtube.com/watch?v=afTpieEZXck

- Preorder traversal is label -> left -> right
- Types of traversal
https://qiita.com/uniTM/items/324883808a62c6938ac0

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

Recursive solution
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
  const res = [];

  const traversal = (current, res) => {
    if (!current) return;

    res.push(current.val);
    traversal(current.left, res);
    traversal(current.right, res);
  };

  traversal(root, res);
  return res;
};
```
