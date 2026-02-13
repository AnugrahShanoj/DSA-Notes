# 📘 Foundation – Question 2  
# 1796. Second Largest Digit in a String

---

## 🧩 Problem Statement

Given a string `s`, return the **second largest numerical digit** that appears in `s`.

If no such digit exists, return `-1`.

---

### Examples

Input:  
s = "dfa12321afd"  

Output:  
2  

Explanation:  
Digits present = 1, 2, 3  
Largest = 3  
Second Largest = 2  

---

Input:  
s = "abc1111"  

Output:  
-1  

Explanation:  
Only one unique digit (1) → No second largest.

---

## 🚀 Approach 1 — Brute Force (Using Array + Set + Sorting)

### 💡 Idea

1. Traverse the string.
2. Extract digits.
3. Store digits in an array.
4. Remove duplicates using `Set`.
5. Sort in descending order.
6. Return second element if exists, otherwise return -1.

---

### 💻 Code (Brute Force)

```js
function secondHighest(s) {
    let digits = [];

    for (let char of s) {
        if (!isNaN(char) && char !== ' ') {
            digits.push(Number(char));
        }
    }

    let unique = [...new Set(digits)];

    if (unique.length < 2) return -1;

    unique.sort((a, b) => b - a);

    return unique[1];
}
```

---

### ⏱ Time Complexity (Brute Force)

**O(n log n)**  

Reason:
- Traversing string → O(n)
- Removing duplicates → O(n)
- Sorting → O(n log n)
- Sorting dominates → O(n log n)

---

### 📦 Space Complexity (Brute Force)

**O(n)**  

Reason:
- Array stores extracted digits.
- Set stores unique digits.
- Memory grows with number of digits in string.

---

## 🚀 Approach 2 — Optimized (Single Pass, No Sorting)

### 💡 Idea

Instead of storing and sorting, track:

- `max` → largest digit
- `secondMax` → second largest digit

Traverse string once:
- If digit > max → update both
- Else if digit < max AND digit > secondMax → update secondMax

This ensures:
- No duplicates
- No sorting
- Single traversal

---

### 💻 Code (Optimized)

```js
function secondHighest(s) {
    let max = -1;
    let secondMax = -1;

    for (let char of s) {
        if (!isNaN(char) && char !== ' ') {
            let digit = Number(char);

            if (digit > max) {
                secondMax = max;
                max = digit;
            } 
            else if (digit < max && digit > secondMax) {
                secondMax = digit;
            }
        }
    }

    return secondMax;
}
```

---

### ⏱ Time Complexity (Optimized)

**O(n)**  

Reason:
- Single traversal of string.
- No nested loops.
- No sorting.

---

### 📦 Space Complexity (Optimized)

**O(1)**  

Reason:
- Only two variables (`max`, `secondMax`).
- No additional data structures.
- Memory does not grow with input size.

---

## 🗣 Interview-Level Explanation (Optimized Approach)

“The straightforward approach is to extract digits, remove duplicates, and sort them to find the second largest. However, sorting is unnecessary because we only need the top two distinct digits.

Instead, I traverse the string once and maintain two variables: `max` and `secondMax`. Whenever I find a digit larger than the current `max`, I update both values accordingly. If a digit lies between `max` and `secondMax`, I update `secondMax`.

This approach avoids sorting and additional storage, achieving O(n) time complexity with O(1) space complexity.”
