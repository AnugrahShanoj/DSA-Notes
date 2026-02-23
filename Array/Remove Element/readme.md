# 📘 Arrays – Question 2  
# 27. Remove Element

---

## 🧩 Problem Statement

Given an integer array `nums` and an integer `val`,  
remove all occurrences of `val` **in-place**.

Return the number of elements `k` which are **not equal to val**.

Modify the array such that:

```
nums[0] to nums[k-1]
```

contain elements **not equal to val**.

Order of elements may change.

---

## Examples

Input:  
nums = [3,2,2,3], val = 3  

Output:  
k = 2  
nums = [2,2,_,_]  

---

Input:  
nums = [0,1,2,2,3,0,4,2], val = 2  

Output:  
k = 5  
nums = [0,1,3,0,4,_,_,_]  

---

# 🚀 Approach 1 — Brute Force (Using Extra Array)

## 💡 Idea

1. Create a temporary array.
2. Add all elements not equal to `val`.
3. Copy elements back to original array.
4. Return the length of temporary array.

---

## 💻 Code (Brute Force)

```js
function removeElement(nums, val) {
    let temp = [];

    for (let num of nums) {
        if (num !== val) {
            temp.push(num);
        }
    }

    for (let i = 0; i < temp.length; i++) {
        nums[i] = temp[i];
    }

    return temp.length;
}
```

---

### ⏱ Time Complexity

**O(n)**  

Reason:  
- Traversing array once.  
- Copying elements back.

---

### 📦 Space Complexity

**O(n)**  

Reason:  
- Extra array used.

---

⚠ Not optimal due to extra memory usage.

---

# 🚀 Approach 2 — Two Pointer (Optimized) ✅

## 💡 Idea

Use:

- `i` → scan pointer  
- `k` → position to place valid elements  

If:

```
nums[i] !== val
```

Then:

```
nums[k] = nums[i]
k++
```

---

## 💻 Code (Optimized)

```js
function removeElement(nums, val) {
    let k = 0;

    for (let i = 0; i < nums.length; i++) {
        if (nums[i] !== val) {
            nums[k] = nums[i];
            k++;
        }
    }

    return k;
}
```

---

### ⏱ Time Complexity

**O(n)**  

Reason:  
- Each element visited once.

---

### 📦 Space Complexity

**O(1)**  

Reason:  
- In-place modification.
- No extra memory used.

---

# 🗣 Interview-Level Explanation

“I use a two-pointer approach where one pointer scans the array and the other tracks the position to place elements not equal to val. Valid elements are copied forward, modifying the array in-place with O(n) time and O(1) space.”