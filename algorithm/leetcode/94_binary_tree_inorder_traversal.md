# Leet Code 94  Binary Tree Inorder Traversal
https://leetcode.com/problems/binary-tree-inorder-traversal/description/
# References
https://www.youtube.com/watch?v=g_S5WuasWUE

- Inorder traversal is left -> label -> right
- Types of traversal
https://qiita.com/uniTM/items/324883808a62c6938ac0

# Solution

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
const inorderTraversal = function(root) {
  const res = [];

  const inOrder = (node) => {
    if (!node) return;

    inOrder(node.left);
    res.push(node.val);
    inOrder(node.right);
  };

  inOrder(root);
  return res;
};
```

Iterative solution
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
const inorderTraversal = function(root) {
  const res = [];
  const stack = [];
  let cur = root;

  while (cur || stack.length) {
    while (cur) {
      stack.push(cur);
      cur = cur.left;
    }

    cur = stack.pop();
    res.push(cur.val);
    cur = cur.right;
  }

  return res;
};
```