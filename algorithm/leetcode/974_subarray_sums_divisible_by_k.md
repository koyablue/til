# Leet Code 974 Subarray Sums Divisible by K

https://leetcode.com/problems/subarray-sums-divisible-by-k/description/

# References
https://www.youtube.com/watch?v=3lUgA_QSwOw
# Solution

```javascript
  // count
  // sum
  // new Map(0, 1)
  // loop nums
  // mod
  // if mod < 0 mod = k + mod
  // if map.has(mod) count+=map.get(mod)
  // map.set(mod, (0||mod + 1))
  let count = 0;
  let accumSum = 0;

  // { mod: count }
  const modCountMap = new Map();
  modCountMap.set(0, 1);

  for (let i = 0; i < nums.length; i++) {
    accumSum += nums[i]
    let mod = accumSum % k;
    if (mod < 0) mod = k + mod;

    if (modCountMap.has(mod)) count += modCountMap.get(mod);

    modCountMap.set(mod, (modCountMap.get(mod) || 0) + 1);
  }

  return count;

```

Optimal solution
```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 */
function subarraysDivByK(nums, k) {
  let count = 0; // サブアレイの数を数えるための変数
  let sum = 0; // 累積和を計算するための変数
  const map = new Map(); // 各mod値の出現頻度を格納するためのMap
  map.set(0, 1); // 初期状態として、合計が0の場合の頻度を1に設定

  for (let i = 0; i < nums.length; i++) {
      sum += nums[i]; // 現在の要素を累積和に加える

      let mod = ((sum % k) + k) % k; // 累積和のmod k（負の数の対応を含む）

      if (map.has(mod)) {
          // このmod値が以前に見つかった場合、その頻度をカウントに追加
          count += map.get(mod);
      }

      // このmod値の頻度をMapに追加（または更新）
      map.set(mod, (map.get(mod) || 0) + 1);
  }

  return count; // サブアレイの合計数を返す
}

```
