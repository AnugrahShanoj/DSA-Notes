# 📘 Arrays – Question 4  
# 121. Best Time to Buy and Sell Stock

---

## 🧩 Problem Statement

You are given an array `prices` where:

```
prices[i]
```

is the price of a stock on day `i`.

You want to:

- Buy one day
- Sell on a later day

Return the **maximum profit** you can achieve.

If no profit possible, return 0.

---

## Examples

Input:  
prices = [7,1,5,3,6,4]  

Output:  
5  

Explanation:  
Buy at 1  
Sell at 6  
Profit = 5  

---

Input:  
prices = [7,6,4,3,1]  

Output:  
0  

No profit possible.

---

# 🚀 Approach 1 — Brute Force

## 💡 Idea

Check:

Every possible buy day  
with every possible sell day after it.

---

## 💻 Code (Brute Force)

```js
function maxProfit(prices) {
    let maxProfit = 0;

    for (let i = 0; i < prices.length; i++) {
        for (let j = i + 1; j < prices.length; j++) {
            let profit = prices[j] - prices[i];
            maxProfit = Math.max(maxProfit, profit);
        }
    }

    return maxProfit;
}
```

---

### ⏱ Time Complexity

**O(n²)**  

Nested loops used.

---

### 📦 Space Complexity

**O(1)**  

No extra memory used.

---

⚠ Not optimal.

---

# 🚀 Approach 2 — Greedy (Optimized) ✅

## 💡 Idea

Maintain:

- Minimum price seen so far  
- Maximum profit possible  

At each day:

1. Calculate profit if sold today.
2. Update maximum profit.
3. Update minimum price if current price is lower.

---

## 💻 Code (Optimized)

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

---

### ⏱ Time Complexity

**O(n)**  

Single pass through the array.

---

### 📦 Space Complexity

**O(1)**  

Only variables used.

---

# 🗣 Interview-Level Explanation

“I maintain the minimum price seen so far while traversing the array. For each day, I calculate the profit if sold today and update the maximum profit accordingly. This greedy strategy ensures O(n) time and O(1) space.”
