# 📘 Reverse Linked List Fundamentals

---

# 🧠 Problem Statement

Current Linked List:

```text
10 → 20 → 30 → null
```

After reversal:

```text
30 → 20 → 10 → null
```

Goal:

Reverse all links in the linked list.

---

# 🚨 Important Understanding

We are NOT reversing values.

❌ Wrong Thinking:

```text
10 becomes 30
```

✅ Correct Thinking:

```text
Direction of links changes
```

---

# 🧠 Original Structure

```text
10.next = 20
20.next = 30
30.next = null
```

After reversal:

```text
30.next = 20
20.next = 10
10.next = null
```

Only links change.

---

# 🚨 Biggest Beginner Mistake

Suppose:

```text
10 → 20 → 30
```

If we directly do:

```js
current.next = prev;
```

without saving next node,

we lose access to remaining nodes.

---

# 🧠 Golden Rule

Before changing any link:

```text
Save next node first
```

This prevents losing the remaining list.

---

# 🚀 Core Idea

Use 3 pointers:

| Pointer | Purpose |
|---|---|
prev | Previous node |
current | Current node |
nextNode | Saves next node |

---

# 🚀 Initial Setup

```js
let prev = null;
let current = head;
```

Visualization:

```text
null ← 10 → 20 → 30
       ↑
    current
```

---

# 🚀 Step-by-Step Process

---

## Step 1 — Save Next Node

```js
let nextNode = current.next;
```

Save future reference.

---

## Step 2 — Reverse Link

```js
current.next = prev;
```

Direction changes.

---

## Step 3 — Move prev

```js
prev = current;
```

prev moves forward.

---

## Step 4 — Move current

```js
current = nextNode;
```

Move to next node.

---

# 🧠 Core Mental Model

At every step:

```text
Save future
Reverse current link
Move forward
```

This sequence is the heart of linked list reversal.

---

# 💻 Final Code

```js
function reverseList(head) {
    let prev = null;
    let current = head;

    while (current !== null) {
        let nextNode = current.next;

        current.next = prev;

        prev = current;

        current = nextNode;
    }

    return prev;
}
```

---

# ⏱ Time Complexity

```text
O(n)
```

Each node visited once.

---

# 📦 Space Complexity

```text
O(1)
```

Only pointers used.

---

# 🚨 Common Beginner Mistakes

## Mistake 1

Changing pointer before saving next node.

Causes node loss.

---

## Mistake 2

Thinking values are reversed.

No.

Links are reversed.

---

## Mistake 3

Returning current instead of prev.

At end:

```text
current = null
```

New head becomes:

```text
prev
```

---

# 🧠 Most Important Understanding

Arrays:

```text
Move using indexes
```

Linked Lists:

```text
Move using references
```

---

# 🗣 Interview-Level Explanation

“I use three pointers: prev, current, and nextNode. Before reversing a link, I store the next node to avoid losing access to the remaining list. Then I reverse the current node’s pointer and move all pointers forward iteratively.”