# 📘 Foundation – Question 7  
# Find Largest Number in an Array

---

## 🧩 Problem Statement

Given an array of numbers, return the **largest number** in the array.

Return `false` if:
- Input is not an array
- Array contains non-number values
- Array contains `NaN`, `Infinity`, or `-Infinity`

Return `null` if the array is empty.

⚠ You must NOT use `Math.max()`.

---

## Examples

Input: `[1, 5, -2, 10]`  
Output: `10`

Input: `[0, 0, 0]`  
Output: `0`

Input: `[-1, -5, 0]`  
Output: `0`

Input: `[]`  
Output: `null`

Input: `"hello"`  
Output: `false`

Input: `[1, 2, "3"]`  
Output: `false`

Input: `[Infinity, 2]`  
Output: `false`

---

# 🚀 Approach — Single Traversal with Validation

## 💡 Idea

1. Check if input is an array.
2. If empty → return `null`.
3. Validate each element:
   - Must be of type `"number"`
   - Must be finite (`Number.isFinite`)
4. Track the maximum value while traversing.
5. Return the maximum value.

---

## 💻 Code

```js
function findLargest(arr) {
  if (!Array.isArray(arr)) {
    return false;
  }

  if (arr.length === 0) {
    return null;
  }

  let max = arr[0];

  for (let num of arr) {
    if (typeof num !== 'number' || !Number.isFinite(num)) {
      return false;
    }

    if (num > max) {
      max = num;
    }
  }

  return max;
}
```

---

### ⏱ Time Complexity

**O(n)**  

Reason:  
- Each element is visited exactly once.  
- Validation and comparison occur in the same traversal.

---

### 📦 Space Complexity

**O(1)**  

Reason:  
- Only one tracking variable (`max`) is used.  
- No additional data structures created.

---

# 🗣 Interview-Level Explanation

“I first validate that the input is an array. If it is empty, I return null as specified. Then I ensure each element is a finite number. During a single traversal, I maintain a variable to track the largest value. Since each element is processed once and no extra memory is used, the solution runs in O(n) time and O(1) space.”
