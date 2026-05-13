# 📘 Linked List Fundamentals — Day 1

---

# 🧠 Why Linked List Was Introduced?

Arrays store elements in **continuous memory locations**.

Example:

```text
[10, 20, 30, 40]
```

Memory representation:

```text
Address   Value
100       10
104       20
108       30
112       40
```

Because arrays are continuous in memory:

```js
arr[2]
```

can be directly accessed.

This gives:

### ⏱ Array Access Time Complexity

```text
O(1)
```

---

# 🚨 Problem With Arrays

Suppose array is:

```text
[10,20,30,40]
```

Now insert:

```text
25 at index 2
```

Need shifting:

```text
[10,20,30,40]
↓
[10,20,25,30,40]
```

Elements must move.

So insertion becomes costly.

### ⏱ Insertion Complexity

```text
O(n)
```

---

# 🧠 What Is a Linked List?

Linked List stores elements as separate nodes connected using references/pointers.

Each node contains:

```text
[data | next]
```

Example:

```text
[10 | • ] → [20 | • ] → [30 | null]
```

Meaning:

- Node containing 10 points to node containing 20
- Node containing 20 points to node containing 30
- Last node points to null

---

# 🚂 Real-Life Analogy

Think of train compartments:

```text
[10] → [20] → [30]
```

Each compartment knows where the next compartment is.

---

# 🧠 Important Terms

---

# 1️⃣ Node

A node is the basic unit of a linked list.

Each node contains:

- Data
- Reference to next node

Structure:

```text
[data | next]
```

---

# 2️⃣ Head

Head is the starting node of the linked list.

Example:

```text
head
 ↓
[10] → [20] → [30]
```

Without head:

❌ Entire linked list is lost.

---

# 3️⃣ Next Pointer

Each node stores reference/address of the next node.

Important:

```text
next does NOT store next value
```

It stores:

```text
reference/address of next node
```

---

# 4️⃣ Null

Last node points to:

```text
null
```

Meaning:

```text
End of linked list
```

---

# 🧠 Array vs Linked List

| Array | Linked List |
|---|---|
Continuous memory | Random memory locations |
Fast indexing | Slow traversal |
O(1) access | O(n) access |
Insertion costly | Insertion easier |
Uses indexes | Uses references |

---

# 🧠 Linked List In JavaScript

---

# Creating Node Structure

```js
class ListNode {
    constructor(val) {
        this.val = val;
        this.next = null;
    }
}
```

Each node contains:

```js
value
next pointer
```

---

# Creating Nodes

```js
let node1 = new ListNode(10);
let node2 = new ListNode(20);
let node3 = new ListNode(30);
```

---

# Connecting Nodes

```js
node1.next = node2;
node2.next = node3;
```

Structure becomes:

```text
10 → 20 → 30 → null
```

---

# Defining Head

```js
let head = node1;
```

---

# 🧠 Most Important Conceptual Shift

## Arrays

Move using:

```text
indexes
```

Example:

```js
arr[2]
```

---

## Linked Lists

Move using:

```text
references/pointers
```

Example:

```js
current = current.next
```

This is the biggest mental shift in linked lists.

---

# 🚀 Traversal In Linked List

Traversal means visiting every node one by one.

---

# 💻 Traversal Code

```js
let current = head;

while (current !== null) {
    console.log(current.val);
    current = current.next;
}
```

---

# 🧠 Dry Run

Initial:

```text
current = 10
```

Print:

```text
10
```

Move:

```js
current = current.next
```

Now:

```text
current = 20
```

Again move:

```text
20 → 30 → null
```

Loop stops when current becomes null.

---

# ⏱ Time Complexities

| Operation | Array | Linked List |
|---|---|---|
Access by index | O(1) | O(n) |
Insert at beginning | O(n) | O(1) |
Delete at beginning | O(n) | O(1) |

---

# 🧠 Why Linked List Is Important?

Linked Lists build foundation for:

- Stack
- Queue
- Trees
- Graphs

Understanding linked lists properly makes future DSA topics easier.

---

# 🚨 Common Beginner Mistake

Wrong Thinking:

```text
next stores next value
```

Correct Thinking:

```text
next stores reference/address of next node
```

---

# 🧠 Important Visualization

```text
head
 ↓
[10 | • ] → [20 | • ] → [30 | null]
```

This structure should stay permanently in mind.

---

# 🗣 Interview-Level Explanation

“A linked list is a linear data structure where each node stores data and a reference to the next node. Unlike arrays, linked lists are not stored continuously in memory, so traversal happens using references instead of indexing.”