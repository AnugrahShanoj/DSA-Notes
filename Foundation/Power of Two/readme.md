# 📘 Foundation – Question 10  
# 231. Power of Two

---

## 🧩 Problem Statement

Given an integer `n`, return **true** if it is a power of two.

Otherwise, return **false**.

A number is a power of two if:

```
n = 2^x   where x ≥ 0
```

---

## Examples

Input:  
n = 1  
Output:  
true  

Input:  
n = 16  
Output:  
true  

Input:  
n = 3  
Output:  
false  

Input:  
n = 0  
Output:  
false  

---

# 🚀 Approach 1 — Repeated Division

## 💡 Idea

1. If n ≤ 0 → return false.
2. Keep dividing n by 2 while it is even.
3. If n becomes 1 → return true.
4. Otherwise → return false.

---

## 💻 Code

```js
function isPowerOfTwo(n) {
    if (n <= 0) return false;

    while (n % 2 === 0) {
        n = n / 2;
    }

    return n === 1;
}
```

---

### ⏱ Time Complexity

**O(log n)**  

Reason:  
n is repeatedly divided by 2.

---

### 📦 Space Complexity

**O(1)**  

Reason:  
No extra memory used.

---

# 🚀 Approach 2 — Bit Manipulation (Optimized) ✅

## 💡 Idea

Power of two in binary form contains only one set bit.

Example:

| Number | Binary |
|--------|--------|
1 | 0001  
2 | 0010  
4 | 0100  
8 | 1000  
16 | 10000  

Subtracting 1 flips all bits after the set bit.

Performing:

```
n & (n - 1)
```

results in:

```
0   → for powers of two
```

Check also:

```
n > 0
```

to avoid 0 case.

---

## 💻 Code

```js
function isPowerOfTwo(n) {
    if (n <= 0) return false;
    return (n & (n - 1)) === 0;
}
```

---

### ⏱ Time Complexity

**O(1)**  

Reason:  
Single bitwise operation.

---

### 📦 Space Complexity

**O(1)**  

Reason:  
No additional memory used.

---

# 🗣 Interview-Level Explanation

“A power of two has only one bit set in its binary representation. Subtracting one flips all bits after that position. Therefore, performing n & (n - 1) results in zero only for powers of two. We also check that n is positive to avoid zero.”
