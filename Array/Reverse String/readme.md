# 📘 Arrays – Question 3  
# 344. Reverse String

---

## 🧩 Problem Statement

Write a function that reverses a string.

The input string is given as an array of characters `s`.

You must do this by modifying the input array **in-place** with **O(1) extra memory**.

---

## Examples

Input:  
s = ["h","e","l","l","o"]  

Output:  
["o","l","l","e","h"]  

---

Input:  
s = ["H","a","n","n","a","h"]  

Output:  
["h","a","n","n","a","H"]  

---

# 🚀 Approach 1 — Brute Force (Using Extra Array)

## 💡 Idea

1. Create a temporary array.
2. Traverse the input array from end to start.
3. Copy elements back to original array.

---

## 💻 Code (Brute Force)

```js
function reverseString(s) {
    let temp = [];

    for (let i = s.length - 1; i >= 0; i--) {
        temp.push(s[i]);
    }

    for (let i = 0; i < temp.length; i++) {
        s[i] = temp[i];
    }
}
```

---

### ⏱ Time Complexity

**O(n)**  

Reason:  
Each element is visited once.

---

### 📦 Space Complexity

**O(n)**  

Reason:  
Extra array used.

---

⚠ Not optimal due to extra memory usage.

---

# 🚀 Approach 2 — Two Pointer (Optimized) ✅

## 💡 Idea

Use two pointers:

- `left` → starting index  
- `right` → ending index  

Swap:

```
s[left] ↔ s[right]
```

Move pointers inward until they meet.

---

## 💻 Code (Optimized)

```js
function reverseString(s) {
    let left = 0;
    let right = s.length - 1;

    while (left < right) {
        let temp = s[left];
        s[left] = s[right];
        s[right] = temp;

        left++;
        right--;
    }
}
```

---

### ⏱ Time Complexity

**O(n)**  

Reason:  
Each character is swapped once.

---

### 📦 Space Complexity

**O(1)**  

Reason:  
In-place swapping.  
No extra memory used.

---

# 🗣 Interview-Level Explanation

“I use a two-pointer approach where one pointer starts from the beginning and the other from the end. I swap characters and move pointers inward until they meet. This reverses the array in-place using O(n) time and O(1) space.”
