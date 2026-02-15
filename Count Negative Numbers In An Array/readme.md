# 📘 Foundation – Question 5  
# Count Negative Numbers in an Array

---

## 🧩 Problem Statement

Given an array `arr` of numbers, return the **count of elements strictly less than 0**.

Return `false` if:
- Input is not an array
- Array contains non-number values
- Array contains `NaN`
- Array contains `Infinity` or `-Infinity`

---

## Examples

Input: `[-1, 0, 1]`  
Output: `1`

Input: `[-2, -5, -7]`  
Output: `3`

Input: `[0, 2, 3]`  
Output: `0`

Input: `[]`  
Output: `0`

Input: `"hello"`  
Output: `false`

Input: `[1, 2, NaN]`  
Output: `false`

---

# 🚀 Approach 1 — Basic Counting (Without Validation)

## 💡 Idea

1. Initialize a counter.
2. Loop through the array.
3. If element < 0 → increment counter.
4. Return counter.

---

## 💻 Code (Basic Version)

```js
function countNegative(arr) {
    let count = 0;

    for (let num of arr) {
        if (num < 0) {
            count++;
        }
    }

    return count;
}
```

---

### ⏱ Time Complexity

**O(n)**  

Where `n` = length of array.  
Each element is visited once.

---

### 📦 Space Complexity

**O(1)**  

Only one counter variable is used.

---

⚠ This version does NOT satisfy input validation requirements.

---

# 🚀 Approach 2 — Full Validation + Counting (Correct Solution) ✅

## 💡 Idea

1. Check if input is an array.
2. Traverse the array.
3. Validate each element:
   - Must be of type "number"
   - Must be finite (`Number.isFinite`)
4. If invalid element found → return false.
5. If element < 0 → increment counter.
6. Return counter.

---

## 💻 Code (Validated Version)

```js
function countNegative(arr) {
  let count = 0;

  if (!Array.isArray(arr)) {
    return false;
  }

  for (let num of arr) {
    if (typeof num !== 'number' || !Number.isFinite(num)) {
      return false;
    }

    if (num < 0) {
      count++;
    }
  }

  return count;
}
```

---

### ⏱ Time Complexity

**O(n)**  

Reason:  
- Single traversal of array.
- Validation and counting done in same loop.

---

### 📦 Space Complexity

**O(1)**  

Reason:  
- Only a counter variable used.
- No additional data structures created.

---

# 🗣 Interview-Level Explanation

“The solution first validates that the input is an array. Then, during a single traversal, each element is checked to ensure it is a finite number. If any invalid value is found, the function immediately returns false. Otherwise, it counts elements strictly less than zero. This approach runs in O(n) time and O(1) space.”
