# Leet Code 121 Best Time ti¥o Buy and Sell Stock

https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/
# References
https://www.youtube.com/watch?v=1pkOgXD63yU
# Solution

```javascript
/**
 * @param {number[]} prices
 * @return {number}
 */
const maxProfit = function(prices) {
  // 2 pointers
  // i = 0, runner = 1

  // while runner < prices.length
  // if prices[i] < prices[runner] maxProfit = Math.max(prices[i] - prices[runner], maxProfit)
  // else i = runner

  let i = 0;
  let runner = 1;

  let maxProfit = 0;

  while (runner < prices.length) {
    if (prices[i] < prices[runner]) {
      maxProfit = Math.max(prices[runner] - prices[i], maxProfit);
    } else {
      i = runner;
    }
    runner++
  }

  return maxProfit;
};
```
