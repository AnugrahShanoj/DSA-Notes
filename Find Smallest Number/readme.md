# 📘 Foundation – Question 6  
# Find Smallest Number in an Array

---

## 🧩 Problem Statement

Given an array of numbers, return the **smallest number** in the array.

Return `false` if:
- Input is not an array
- Array contains non-number values
- Array contains `NaN`, `Infinity`, or `-Infinity`

Return `null` if the array is empty.

⚠ You must NOT use `Math.min()`.

---

## Examples

Input: `[1, 5, -2, 10]`  
Output: `-2`

Input: `[0, 0, 0]`  
Output: `0`

Input: `[-1, -5, 0]`  
Output: `-5`

Input: `[]`  
Output: `null`

Input: `"hello"`  
Output: `false`

Input: `[1, 2, "3"]`  
Output: `false`

Input: `[Infinity, 2]`  
Output: `false`

---

# 🚀 Approach 1 — Basic Traversal (Without Validation)

## 💡 Idea

1. Assume first element is smallest.
2. Traverse the array.
3. Update smallest if smaller element found.
4. Return smallest.

---

## 💻 Code (Basic Version)

```js
function findSmallest(arr) {
    let min = arr[0];

    for (let num of arr) {
        if (num < min) {
            min = num;
        }
    }

    return min;
}
```

---

### ⏱ Time Complexity

**O(n)**  

Each element is visited once.

---

### 📦 Space Complexity

**O(1)**  

Only one variable (`min`) is used.

---

⚠ This version does NOT validate input and does not handle empty arrays.

---

# 🚀 Approach 2 — Validated Correct Solution ✅

## 💡 Idea

1. Check if input is an array.
2. If empty → return `null`.
3. Validate each element:
   - Must be of type `"number"`
   - Must be finite (`Number.isFinite`)
4. Track smallest value during traversal.
5. Return smallest value.

---

## 💻 Code (Validated Version)

```js
function findSmallest(arr) {
  if (!Array.isArray(arr)) {
    return false;
  }

  if (arr.length === 0) {
    return null;
  }

  let min = arr[0];

  for (let num of arr) {
    if (typeof num !== 'number' || !Number.isFinite(num)) {
      return false;
    }

    if (num < min) {
      min = num;
    }
  }

  return min;
}
```

---

### ⏱ Time Complexity

**O(n)**  

Reason:  
- Single traversal of array.
- Validation and comparison occur in the same loop.

---

### 📦 Space Complexity

**O(1)**  

Reason:  
- Only one tracking variable (`min`) used.
- No additional arrays created.

---

# 🗣 Interview-Level Explanation

“I first validate that the input is an array. If it is empty, I return null as specified. Then I ensure each element is a finite number. While traversing the array, I maintain a variable to track the smallest value. Since each element is visited once and no extra data structures are used, the solution runs in O(n) time and O(1) space.”
