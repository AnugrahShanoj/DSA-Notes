# 📘 Arrays – Question 5  
# 88. Merge Sorted Array

---

## 🧩 Problem Statement

You are given two sorted arrays:

- `nums1` of size `m + n`
- `nums2` of size `n`

Where:

- First `m` elements in `nums1` are valid
- Last `n` elements in `nums1` are 0 (placeholders)

Merge `nums2` into `nums1` such that:

- Final array is sorted
- Modify `nums1` **in-place**

---

## Examples

Input:  
nums1 = [1,2,3,0,0,0]  
m = 3  
nums2 = [2,5,6]  
n = 3  

Output:  
[1,2,2,3,5,6]  

---

# 🚀 Approach 1 — Brute Force

## 💡 Idea

1. Copy all elements of `nums2` into `nums1`.
2. Sort the final array.

---

## 💻 Code (Brute Force)

```js
function merge(nums1, m, nums2, n) {
    for (let i = 0; i < n; i++) {
        nums1[m + i] = nums2[i];
    }

    nums1.sort((a, b) => a - b);
}
```

---

### ⏱ Time Complexity

**O((m + n) log(m + n))**  

Reason:  
Sorting required after merging.

---

### 📦 Space Complexity

**O(1)**  

Ignoring internal sort memory.

---

⚠ Not optimal due to sorting.

---

# 🚀 Approach 2 — Two Pointer (Optimized) ✅

## 💡 Idea

Use three pointers:

- `i` → last valid element in nums1 (m - 1)  
- `j` → last element in nums2 (n - 1)  
- `k` → last index in nums1 (m + n - 1)  

Compare:

```
nums1[i] and nums2[j]
```

Place the larger element at:

```
nums1[k]
```

Move the pointers accordingly.

---

## 💻 Code (Optimized)

```js
function merge(nums1, m, nums2, n) {
    let i = m - 1;
    let j = n - 1;
    let k = m + n - 1;

    while (i >= 0 && j >= 0) {
        if (nums1[i] > nums2[j]) {
            nums1[k] = nums1[i];
            i--;
        } else {
            nums1[k] = nums2[j];
            j--;
        }
        k--;
    }

    while (j >= 0) {
        nums1[k] = nums2[j];
        j--;
        k--;
    }
}
```

---

### ⏱ Time Complexity

**O(m + n)**  

Reason:  
Each element is placed once.

---

### 📦 Space Complexity

**O(1)**  

Reason:  
In-place merging.
No extra memory used.

---

# 🗣 Interview-Level Explanation

“I use three pointers starting from the end of both arrays. I compare the largest elements and place them at the end of nums1, ensuring in-place merging without overwriting valid data.”