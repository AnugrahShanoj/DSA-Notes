# 📘 Foundation – Question 1: sum()

## 🧩 Problem
Design a function `sum` that can take any number of arguments and return their total.

### Examples
sum(1, 2, 3) → 6  
sum(10) → 10  
sum() → 0  
sum(5, -5, 10, 20) → 30  
sum(100, 200, 300, 400) → 1000  

---

## 🧠 Concept Used
- Rest Parameters (`...args`) in JavaScript
- Loop traversal
- Accumulation pattern

---

## 🚀 Approach

1. Use rest parameters to collect all inputs:
   `function sum(...args)`
2. Initialize `total = 0`
3. Loop through each element in `args`
4. Add each value to `total`
5. Return `total`

---

## 💻 Code

```js
function sum(...args) {
    let total = 0;

    for (let num of args) {
        total += num;
    }

    return total;
}
```

---

## ⏱ Time Complexity

**O(n)**  
Where `n` = number of arguments passed.

Reason:
- We iterate through each argument once.
- No nested loops.
- Linear growth with respect to input size.

---

## 📦 Space Complexity

**O(n)**  

Reason:
- Rest parameter `...args` stores arguments in an array.
- Memory usage grows proportionally with number of inputs.
- No additional significant memory used.

---

## 🗣 Interview Explanation

“The function needs to handle a dynamic number of arguments.  
Using rest parameters, I collect all inputs into an array and iterate once to accumulate the sum.  
This gives O(n) time and O(n) space complexity.”
