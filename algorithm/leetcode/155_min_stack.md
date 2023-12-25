# Leet Code 155 Min Stack

https://leetcode.com/problems/min-stack/description/
# References

# Solution

```javascript
class MinStack {
  constructor() {
    this.stack = [];
    this.minStack = [];
  }

  /**
   * @param {number} val
   * @return {void}
   */
  push(val) {
    this.stack.push(val);

    if (!this.minStack.length || val <= this.minStack[this.minStack.length - 1]) {
      this.minStack.push(val);
    }
  }

  /**
   * @return {void}
   */
  pop() {
    if (!this.stack.length) return;
    const removed = this.stack.pop();

    if (this.minStack.length && removed === this.minStack[this.minStack.length - 1]) {
      this.minStack.pop();
    }
  }

  /**
   * @return {number}
   */
  top() {
    return this.stack.length
      ? this.stack[this.stack.length  - 1]
      : undefined;
  }

  /**
   * @return {number}
   */
  getMin() {
    return this.minStack.length
      ? this.minStack[this.minStack.length  - 1]
      : undefined;
  }
}
```
