# 📘 Arrays – Question  
# 136. Single Number

---

## 🧩 Problem Statement

Given a non-empty array of integers `nums`,

Every element appears twice except for one.

Find that single element.

You must solve it using:

- Linear runtime
- Constant extra space

---

## Examples

Input:  
nums = [2,2,1]

Output:  
1

---

Input:  
nums = [4,1,2,1,2]

Output:  
4

---

# 🚀 Approach 1 — Brute Force

## 💡 Idea

For every element:

1. Count its frequency in the array.
2. The element with frequency `1` is the answer.

---

## 💻 Code (Brute Force)

```js
function singleNumber(nums) {
    for (let i = 0; i < nums.length; i++) {
        let count = 0;

        for (let j = 0; j < nums.length; j++) {
            if (nums[i] === nums[j]) {
                count++;
            }
        }

        if (count === 1) {
            return nums[i];
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

# 🚀 Approach 2 — Hash Map

## 💡 Idea

Store frequency of each element.

Element with frequency `1` is the answer.

---

## 💻 Code (Hash Map)

```js
function singleNumber(nums) {
    let map = {};

    for (let num of nums) {
        map[num] = (map[num] || 0) + 1;
    }

    for (let key in map) {
        if (map[key] === 1) {
            return Number(key);
        }
    }
}
```

---

### ⏱ Time Complexity

**O(n)**

Reason:  
Single traversal for storing and checking frequencies.

---

### 📦 Space Complexity

**O(n)**

Reason:  
Extra hash map used.

---

# 🚀 Approach 3 — XOR (Optimal) ✅

## 💡 Idea

XOR properties:

```
a ^ a = 0
a ^ 0 = a
```

Duplicate numbers cancel each other.

Only the unique number remains.

---

## 💻 Code (Optimal XOR)

```js
function singleNumber(nums) {
    let result = 0;

    for (let num of nums) {
        result ^= num;
    }

    return result;
}
```

---

### ⏱ Time Complexity

**O(n)**

Reason:  
Single traversal.

---

### 📦 Space Complexity

**O(1)**

Reason:  
No extra memory used.

---

# 🗣 Interview-Level Explanation

“I use XOR because identical numbers cancel each other out due to the property a ^ a = 0. After XORing all elements, only the unique element remains.”