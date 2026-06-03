---
notion-id: 2b7982ca-e761-80f8-ba71-d99aecc7173c
---
We’ll do a **top-down merge sort** on the doubly linked list:

> 5 ⇄ 4 ⇄ 1 ⇄ 6 ⇄ 3 ⇄ 2 ⇄ 8 ⇄ 7

I’ll show:

1. how it **splits** using slow/fast pointers
2. how each half is **recursively sorted**
3. how the **merge** uses only the list heads (and what happens to `prev` / `next`)

---

## 1. First split (full list → two halves)

Use slow/fast pointers:

- Start: `slow = 5`, `fast = 5`
- Step 1: `slow = 4`, `fast = 1`
- Step 2: `slow = 1`, `fast = 3`
- Step 3: `slow = 6`, `fast = 8`
- Step 4: `slow = 3`, `fast = null` (end)

So `slow` ends around the middle. We split **after** `3`:

Left half:

`5 ⇄ 4 ⇄ 1 ⇄ 6 ⇄ 3`

Right half:

`2 ⇄ 8 ⇄ 7`

But a common split point is actually when slow is at `6` or `3` depending on implementation. Let’s choose a clean, balanced split:

We’ll instead assume the midpoint gives:

- Left: `5 ⇄ 4 ⇄ 1 ⇄ 6`
- Right: `3 ⇄ 2 ⇄ 8 ⇄ 7`

We then:

- set `6.next = null`
- set `3.prev = null`

Now we sort each half separately.

---

## 2. Sort the left half: `5, 4, 1, 6`

### 2.1 Split `5 ⇄ 4 ⇄ 1 ⇄ 6`

Slow/fast on this sublist:

- `slow = 5`, `fast = 5`
- `slow = 4`, `fast = 1`
- `slow = 1`, `fast = null` (depending on implementation)

We split into:

- Left-left: `5 ⇄ 4`
- Left-right: `1 ⇄ 6`

Again, adjust pointers:

- `4.next = null`, `1.prev = null`

### 2.1.1 Sort `5 ⇄ 4`

Split:

- `slow = 5`, `fast = 5`
- `slow = 4`, `fast = null`

So:

- `5` and `4` as two 1-node lists
- `5.next = null`, `4.prev = null`

Now merge `5` and `4`:

- Compare heads: `5` vs `4` → take `4`
    - result: `4`
- Compare next head: `5` (only one left) → append `5`
    - result: `4 ⇄ 5`

While merging we also do:

- when `4` is first: `4.prev = null`
- when linking `5` after `4`: `4.next = 5` and `5.prev = 4`

So sorted result of this sublist:

`4 ⇄ 5`

### 2.1.2 Sort `1 ⇄ 6`

Split into `1` and `6`:

- `1.next = null`, `6.prev = null`

Merge:

- Compare `1` vs `6` → take `1`, then `6`
- Result: `1 ⇄ 6` (already in order)

### 2.1.3 Merge `4 ⇄ 5` and `1 ⇄ 6`

We now merge:

- A: `4 ⇄ 5`
- B: `1 ⇄ 6`

Step-by-step:

4. Compare `4` vs `1` → take `1`
    - result: `1`
5. Compare `4` vs `6` → take `4`
    - result: `1 ⇄ 4`
    - set `1.next = 4`, `4.prev = 1`
6. Compare `5` vs `6` → take `5`
    - result: `1 ⇄ 4 ⇄ 5`
    - set `4.next = 5`, `5.prev = 4`
7. Remaining: `6`
    - append: `1 ⇄ 4 ⇄ 5 ⇄ 6`
    - set `5.next = 6`, `6.prev = 5`

Left half sorted:

`1 ⇄ 4 ⇄ 5 ⇄ 6`

---

## 3. Sort the right half: `3, 2, 8, 7`

Right half:

`3 ⇄ 2 ⇄ 8 ⇄ 7`

### 3.1 Split `3 ⇄ 2 ⇄ 8 ⇄ 7`

Use slow/fast:

- `slow = 3`, `fast = 3`
- `slow = 2`, `fast = 8`
- `slow = 8`, `fast = null`

Split roughly in the middle:

- Right-left: `3 ⇄ 2`
- Right-right: `8 ⇄ 7`

Again:

- `2.next = null`, `8.prev = null`

### 3.1.1 Sort `3 ⇄ 2`

Split into `3` and `2`:

- `3.next = null`, `2.prev = null`

Merge:

8. Compare `3` vs `2` → take `2`
    - result: `2`
9. Remaining: `3`
    - result: `2 ⇄ 3`
    - set `2.next = 3`, `3.prev = 2`

So we get:

`2 ⇄ 3`

### 3.1.2 Sort `8 ⇄ 7`

Split into `8` and `7`:

- `8.next = null`, `7.prev = null`

Merge:

10. Compare `8` vs `7` → take `7`
    - result: `7`
11. Remaining: `8`
    - result: `7 ⇄ 8`

So we get:

`7 ⇄ 8`

### 3.1.3 Merge `2 ⇄ 3` and `7 ⇄ 8`

Merge:

- A: `2 ⇄ 3`
- B: `7 ⇄ 8`
12. Compare `2` vs `7` → take `2`
    - result: `2`
13. Compare `3` vs `7` → take `3`
    - result: `2 ⇄ 3`
14. Remaining from B: `7 ⇄ 8`
    - append them in order:
    - `2 ⇄ 3 ⇄ 7 ⇄ 8`

Pointers for each link:

- `2.prev = null`
- `2.next = 3`, `3.prev = 2`
- `3.next = 7`, `7.prev = 3`
- `7.next = 8`, `8.prev = 7`

Right half sorted:

`2 ⇄ 3 ⇄ 7 ⇄ 8`

---

## 4. Final merge: `[1,4,5,6]` with `[2,3,7,8]`

Now merge:

- Left sorted: `1 ⇄ 4 ⇄ 5 ⇄ 6`
- Right sorted: `2 ⇄ 3 ⇄ 7 ⇄ 8`

Step-by-step:

15. Compare `1` vs `2` → take `1`
    - result: `1`
16. Compare `4` vs `2` → take `2`
    - result: `1 ⇄ 2`
17. Compare `4` vs `3` → take `3`
    - result: `1 ⇄ 2 ⇄ 3`
18. Compare `4` vs `7` → take `4`
    - result: `1 ⇄ 2 ⇄ 3 ⇄ 4`
19. Compare `5` vs `7` → take `5`
    - result: `1 ⇄ 2 ⇄ 3 ⇄ 4 ⇄ 5`
20. Compare `6` vs `7` → take `6`
    - result: `1 ⇄ 2 ⇄ 3 ⇄ 4 ⇄ 5 ⇄ 6`
21. Remaining from right: `7 ⇄ 8`
    - append: `1 ⇄ 2 ⇄ 3 ⇄ 4 ⇄ 5 ⇄ 6 ⇄ 7 ⇄ 8`

Throughout, for each chosen node `x`, you:

- set `tail.next = x` (where `tail` is last node in the result)
- set `x.prev = tail`
- update `tail = x`
- ensure the final head’s `prev = null`

Final sorted doubly linked list:

> 1 ⇄ 2 ⇄ 3 ⇄ 4 ⇄ 5 ⇄ 6 ⇄ 7 ⇄ 8

---

### Key conceptual points from this walk-through

- You *never* compare entire lists, only **current heads**.
- The list is repeatedly **halved** until you reach length 1.
- Merging is just **pointer rewiring**:
    - advance the head of whichever list has the smaller front value
    - fix both `next` and `prev` as you build the new list
- Doubly linked specifics: every time you attach a node, you also ensure its `prev` is correct; the algorithmic structure is the same as for a singly linked list.

If you want, next step could be to translate this exact example into pseudocode with calls like `merge(head1, head2)` and explicit `prev/next` updates.