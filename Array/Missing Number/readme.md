# 📘 Arrays – Question  
# 268. Missing Number

---

## 🧩 Problem Statement

Given an array `nums` containing `n` distinct numbers in the range:

```
[0, n]
```

Return the only number in the range that is missing from the array.

---

## Examples

Input:  
nums = [3,0,1]

Output:  
2

---

Input:  
nums = [0,1]

Output:  
2

---

# 🚀 Approach 1 — Brute Force

## 💡 Idea

For every number from `0` to `n`:

1. Search whether it exists in the array.
2. If not found, return that number.

---

## 💻 Code (Brute Force)

```js
function missingNumber(nums) {
    let n = nums.length;

    for (let i = 0; i <= n; i++) {
        let found = false;

        for (let j = 0; j < n; j++) {
            if (nums[j] === i) {
                found = true;
                break;
            }
        }

        if (!found) {
            return i;
        }
    }
}
```

---

### ⏱ Time Complexity

**O(n²)**

Reason:  
Nested loops used.

---

### 📦 Space Complexity

**O(1)**

Reason:  
No extra memory used.

---

⚠ Not optimal.

---

# 🚀 Approach 2 — Sorting

## 💡 Idea

1. Sort the array.
2. Each index should contain the same number.
3. First mismatch gives the missing number.

Example:

```
[3,0,1]
→ [0,1,3]
```

Index `2` should contain `2`.

So answer = `2`.

---

## 💻 Code (Sorting)

```js
function missingNumber(nums) {
    nums.sort((a, b) => a - b);

    for (let i = 0; i < nums.length; i++) {
        if (nums[i] !== i) {
            return i;
        }
    }

    return nums.length;
}
```

---

### ⏱ Time Complexity

**O(n log n)**

Reason:  
Sorting dominates complexity.

---

### 📦 Space Complexity

**O(1)**

Ignoring internal sorting memory.

---

# 🚀 Approach 3 — Mathematical Formula (Optimal) ✅

## 💡 Idea

Numbers are from:

```
0 → n
```

Expected sum:

```
n * (n + 1) / 2
```

Actual sum:

```
sum of all array elements
```

Difference between them gives the missing number.

---

## 💻 Code (Optimal)

```js
function missingNumber(nums) {
    let n = nums.length;

    let expectedSum = (n * (n + 1)) / 2;

    let actualSum = 0;

    for (let num of nums) {
        actualSum += num;
    }

    return expectedSum - actualSum;
}
```

---

### ⏱ Time Complexity

**O(n)**

Reason:  
Single traversal of array.

---

### 📦 Space Complexity

**O(1)**

Reason:  
Only variables used.

---

# 🗣 Interview-Level Explanation

“I calculate the expected sum of numbers from 0 to n using the arithmetic formula and subtract the actual sum of array elements. The difference gives the missing number in O(n) time and O(1) space.”