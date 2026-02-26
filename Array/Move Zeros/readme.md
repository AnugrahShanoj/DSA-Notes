# 📘 Arrays – Question 6  
# 283. Move Zeroes

---

## 🧩 Problem Statement

Given an integer array `nums`, move all `0`s to the end of it  
while maintaining the **relative order of non-zero elements**.

Modify the array **in-place**.

---

## Examples

Input:  
nums = [0,1,0,3,12]  

Output:  
[1,3,12,0,0]  

---

# 🚀 Approach 1 — Brute Force

## 💡 Idea

1. Create a temporary array.
2. Add all non-zero elements to it.
3. Fill remaining positions with zero.
4. Copy back to original array.

---

## 💻 Code (Brute Force)

```js
function moveZeroes(nums) {
    let temp = [];

    for (let num of nums) {
        if (num !== 0) {
            temp.push(num);
        }
    }

    while (temp.length < nums.length) {
        temp.push(0);
    }

    for (let i = 0; i < nums.length; i++) {
        nums[i] = temp[i];
    }
}
```

---

### ⏱ Time Complexity

**O(n)**  

Reason:  
Traversing array once and copying elements back.

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

Use:

- `i` → scans array  
- `k` → position for next non-zero element  

If:

```
nums[i] !== 0
```

Swap:

```
nums[i] and nums[k]
```

Increment `k`.

---

## 💻 Code (Optimized)

```js
function moveZeroes(nums) {
    let k=0;
    for(let i=0; i<nums.length; i++){
        if(nums[i]!==0){
            let temp=nums[i];
            nums[i]=nums[k];
            nums[k]=temp;
            k++;
        }
    }
}
```

---

### ⏱ Time Complexity

**O(n)**  

Reason:  
Each element visited once.

---

### 📦 Space Complexity

**O(1)**  

Reason:  
In-place modification.

---

# 🗣 Interview-Level Explanation

“I use a two-pointer approach where one pointer scans the array and the other tracks the position for the next non-zero element. When a non-zero element is found, I swap it with the element at the tracked position and increment the pointer. This moves all non-zero elements forward while pushing zeros to the end in-place.”