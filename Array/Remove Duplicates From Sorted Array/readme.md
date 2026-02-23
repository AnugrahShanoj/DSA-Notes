# 📘 Arrays – Question 1  
# 26. Remove Duplicates from Sorted Array

---

## 🧩 Problem Statement

Given a **sorted array** `nums`, remove the duplicates **in-place** such that each element appears only once.

Return the number of unique elements `k`.

Modify the array such that:

```
nums[0] to nums[k-1]
```

contain the unique elements.

---

## Examples

Input:  
nums = [1,1,2]  

Output:  
k = 2  
nums = [1,2,_]  

---

Input:  
nums = [0,0,1,1,1,2,2,3,3,4]  

Output:  
k = 5  
nums = [0,1,2,3,4,_,_,_,_,_]  

---

# 🚀 Approach 1 — Brute Force (Using Set)

## 💡 Idea

1. Use Set to remove duplicates.
2. Convert Set back to array.
3. Copy unique values into original array.
4. Return length of unique array.

---

## 💻 Code (Brute Force)

```js
function removeDuplicates(nums) {
    let unique = [...new Set(nums)];

    for (let i = 0; i < unique.length; i++) {
        nums[i] = unique[i];
    }

    return unique.length;
}
```

---

### ⏱ Time Complexity

**O(n)**  

Reason:  
- Creating Set takes O(n).  
- Copying values takes O(n).

---

### 📦 Space Complexity

**O(n)**  

Reason:  
- Extra memory used by Set.

---

⚠ This does not satisfy in-place constraint optimally.

---

# 🚀 Approach 2 — Two Pointer (Optimized) ✅

## 💡 Idea

Since the array is sorted, duplicate elements are adjacent.

Use:

- `i` → scans the array  
- `k` → tracks position of next unique element  

Compare:

```
nums[i] with nums[k-1]
```

If different:

```
nums[k] = nums[i]
k++
```

---

## 💻 Code (Optimized)

```js
function removeDuplicates(nums) {
    if (nums.length === 0) return 0;

    let k = 1;

    for (let i = 1; i < nums.length; i++) {
        if (nums[i] !== nums[k - 1]) {
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
- No extra memory used.  
- In-place modification.

---

# 🗣 Interview-Level Explanation

“Since the array is sorted, duplicates appear adjacent. I use a second pointer to track the position for unique elements. When a new unique element is found, I place it at the tracked position and increment the pointer. This modifies the array in-place with O(n) time and O(1) space.”