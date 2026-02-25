# 🧭 Greedy Pattern — Quick Notes

---

## 📌 What Is Greedy?

A Greedy algorithm makes the **best local decision at each step** hoping it leads to the **global optimal solution**.

Key idea:

* Never revisit past choices.
* Decide optimally at the current step based on available information.

Common clues in problem statements:

* "Maximize" / "Minimize"
* "Choose best at each step"
* "Buy before sell"
* "Earliest finish time"
* "Minimum number of operations"

---

## 🧩 Example: Best Time to Buy and Sell Stock

Maintain:

* Minimum price seen so far
* Maximum profit possible

### 💻 Code

```js
function maxProfit(prices) {
  let minPrice = prices[0];
  let maxProfit = 0;

  for (let i = 1; i < prices.length; i++) {
    let profit = prices[i] - minPrice;

    if (profit > maxProfit) {
      maxProfit = profit;
    }

    if (prices[i] < minPrice) {
      minPrice = prices[i];
    }
  }

  return maxProfit;
}
```

### ⏱ Time Complexity

O(n)

### 📦 Space Complexity

O(1)

---

## 🗣 Interview Explanation

“I maintain the minimum value seen so far and compute the best possible gain at each step. This greedy choice ensures the optimal profit in a single pass.”
