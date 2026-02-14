# 📘 Foundation – Question 3  
# 9. Palindrome Number

---

## 🧩 Problem Statement

Given an integer `x`, return **true** if `x` is a palindrome, otherwise return **false**.

A palindrome number reads the same backward as forward.

---

### Examples

Input:  
x = 121  

Output:  
true  

---

Input:  
x = -121  

Output:  
false  

---

Input:  
x = 10  

Output:  
false  

---

## 🚀 Approach 1 — Brute Force (Using String Conversion)

### 💡 Idea

1. Convert number to string.
2. Reverse the string.
3. Compare with original string.

---

### 💻 Code

```js
function isPalindrome(x) {
    let str = x.toString();
    let reversed = str.split('').reverse().join('');
    return str === reversed;
}
```

---

### ⏱ Time Complexity

**O(n)**  

Where `n` = number of digits.

Reason:
- Converting to string → O(n)
- Splitting → O(n)
- Reversing → O(n)
- Joining → O(n)

---

### 📦 Space Complexity

**O(n)**  

Reason:
- Extra string and array created.
- Memory grows with number of digits.

---

## 🚀 Approach 2 — Optimized (Mathematical Reversal)

### 💡 Idea

1. Negative numbers are not palindrome.
2. If number ends with 0 (and is not 0), it cannot be palindrome.
3. Reverse the number mathematically:
   - Extract last digit using `% 10`
   - Remove last digit using `Math.floor(x / 10)`
4. Compare reversed number with original.

---

### 💻 Code

```js
function isPalindrome(x) {
    if (x < 0) return false;
    if (x !== 0 && x % 10 === 0) return false;

    let original = x;
    let reversed = 0;

    while (x > 0) {
        let digit = x % 10;
        reversed = reversed * 10 + digit;
        x = Math.floor(x / 10);
    }

    return original === reversed;
}
```

---

### ⏱ Time Complexity

**O(n)**  

Where `n` = number of digits.

Reason:
- Each digit is processed once.

---

### 📦 Space Complexity

**O(1)**  

Reason:
- Only a few integer variables used.
- No extra arrays or strings created.

---

## 🗣 Interview-Level Explanation

“The brute force approach converts the number to a string and checks if it reads the same backward. However, that requires extra space.

A better approach reverses the number mathematically by extracting digits using modulus and division. If the reversed number equals the original number, it is a palindrome. This solution runs in O(n) time and O(1) space.”
