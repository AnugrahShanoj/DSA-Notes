# 🧭 Sliding Window Pattern — Quick Notes

---

## 📌 When to Use Sliding Window?

Use Sliding Window when:

* Problem involves **subarray / substring**.
* Elements are **continuous**.
* You need **max/min sum/length**.
* Window size is **fixed** or **dynamic**.
* You want to **avoid nested loops**.

Common clues in problem statements:

* "Subarray of size k"
* "Longest/Shortest substring"
* "Continuous segment"
* "Maximum/Minimum sum"

---

## 🧩 Example: Maximum Sum of Subarray of Size k

Given an array and integer k, find the maximum sum of any contiguous subarray of size k.

### 💻 Code

```js
function maxSubarraySum(arr, k) {
  let windowSum = 0;

  for (let i = 0; i < k; i++) {
    windowSum += arr[i];
  }

  let maxSum = windowSum;

  for (let i = k; i < arr.length; i++) {
    windowSum = windowSum - arr[i - k] + arr[i];
    if (windowSum > maxSum) {
      maxSum = windowSum;
    }
  }

  return maxSum;
}
```

### ⏱ Time Complexity

O(n)

### 📦 Space Complexity

O(1)

---

## 🗣 Interview Explanation

“I compute the first window sum and then slide the window by removing the outgoing element and adding the incoming element. This avoids recomputing sums and achieves linear time.”
