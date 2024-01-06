# Leet Code 145  Binary Tree Postorder Traversal
https://leetcode.com/problems/binary-tree-postorder-traversal/description/
# References
https://www.youtube.com/watch?v=QhszUQhGGlA
https://leetcode.com/problems/binary-tree-postorder-traversal/solutions/880981/iterative-recursive-js-solutions/

- Preorder traversal is left -> right -> label
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
const postorderTraversal = function(root) {
  if (!root) return [];

  const res = [];
  const stack = [];
  stack.push(root);

  while (stack.length) {
    let node = stack[stack.length - 1];
    if (node.left) {
      stack.push(node.left);
      node.left = null;
    } else if (node.right) {
      stack.push(node.right);
      node.right = null;
    } else {
      node = stack.pop();
      res.push(node.val);
    }
  };

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
const postorderTraversal = function(root) {
  const res = [];

  const postOrder = (node) => {
    if (!node) return;

    postOrder(node.left);
    postOrder(node.right);
    res.push(node.val);
  };

  postOrder(root);
  return res;
};
```
