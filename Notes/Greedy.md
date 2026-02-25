# 🧭 Two Pointer Pattern — Quick Notes

---

## 📌 When to Use Two Pointers?

Use the Two Pointer approach when:

* You need to compare or operate on elements from **two positions** in an array/string.
* The problem asks for **in-place modification**.
* The array is **sorted** and involves removing duplicates or finding pairs.
* You need to **reverse** or **check symmetry** (like palindrome).
* You want to **avoid extra space** (O(1) space target).

Common clues in problem statements:

* "In-place"
* "Sorted array"
* "Reverse"
* "Remove duplicates"
* "Compare from both ends"

---

## 🧠 Types of Two Pointers

1. **Same Direction** (Fast & Slow)

   * Remove duplicates
   * Remove specific elements

2. **Opposite Direction** (Start & End)

   * Reverse string/array
   * Palindrome check

---

## 🧩 Example: Reverse String

Given an array of characters, reverse it in-place.

### 💻 Code

```js
function reverseString(s) {
  let left = 0;
  let right = s.length - 1;

  while (left < right) {
    [s[left], s[right]] = [s[right], s[left]];
    left++;
    right--;
  }
}
```

### ⏱ Time Complexity

O(n)

### 📦 Space Complexity

O(1)

---

## 🗣 Interview Explanation

“I use two pointers starting from both ends of the array and swap elements while moving inward. This reverses the array in-place using constant extra space.”
