# 📘 Foundation – Question 4  
# 7. Reverse Integer

---

## 🧩 Problem Statement

Given a signed 32-bit integer `x`, return `x` with its digits reversed.

If reversing `x` causes the value to go outside the signed 32-bit integer range  
[-2³¹, 2³¹ − 1], then return `0`.

---

### Examples

Input:  
x = 123  
Output:  
321  

Input:  
x = -123  
Output:  
-321  

Input:  
x = 120  
Output:  
21  

Input:  
x = 1534236469  
Output:  
0  

Explanation:  
Reversed value exceeds 32-bit signed integer range.

---

# 🚀 Approach 1 — Brute Force (Using String Conversion)

## 💡 Idea

1. Convert number to string.
2. Remove sign if negative.
3. Reverse string.
4. Convert back to number.
5. Restore sign.
6. Check 32-bit overflow.

---

## 💻 Code (Brute Force)

```js
function reverse(x) {
    let isNegative = x < 0;
    let str = Math.abs(x).toString();
    let reversedStr = str.split('').reverse().join('');
    let result = Number(reversedStr);

    if (isNegative) result = -result;

    if (result < -(2 ** 31) || result > 2 ** 31 - 1) {
        return 0;
    }

    return result;
}
```

---

### ⏱ Time Complexity

**O(n)**  

Where `n` = number of digits.  

Reason:  
- Convert to string → O(n)  
- Reverse → O(n)  
- Join → O(n)  

---

### 📦 Space Complexity

**O(n)**  

Reason:  
- Extra string and array created during reversal.  
- Memory grows with number of digits.  

---

# 🚀 Approach 2 — Optimized (Mathematical Reversal) ✅

## 💡 Idea

1. Store sign separately.
2. Work only with absolute value of number.
3. Extract last digit using `% 10`.
4. Build reversed number using multiplication and addition.
5. Restore sign.
6. Check overflow at the end.

---

## 💻 Code (Optimized – Your Version)

```js
function reverse(x) {
    let isNegative = x < 0;
    let reversed = 0;
    let num = Math.abs(x);

    while (num > 0) {
        let digit = num % 10;
        reversed = reversed * 10 + digit;
        num = Math.floor(num / 10);
    }

    if (isNegative) {
        reversed = -reversed;
    }

    if (reversed < -(2 ** 31) || reversed > 2 ** 31 - 1) {
        return 0;
    }

    return reversed;
}
```

---

### ⏱ Time Complexity

**O(n)**  

Where `n` = number of digits.  

Reason:  
- Each digit is processed exactly once.  
- No nested loops.  

---

### 📦 Space Complexity

**O(1)**  

Reason:  
- Only a few integer variables are used (`reversed`, `digit`, `num`).  
- No extra arrays or strings created.  

---

# 🗣 Interview-Level Explanation

“The brute force solution converts the number into a string and reverses it, but that requires extra space.

The optimized approach reverses the integer mathematically by extracting digits using modulus and division. I first separate the sign to simplify logic, reverse the magnitude, then restore the sign. Finally, I ensure the result stays within 32-bit integer range. This approach runs in O(n) time and O(1) space.”
