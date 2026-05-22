---
notion-id: 27f982ca-e761-8081-89be-de0cad2f8e7c
---
We did A implies B before. [[Lecture 1 Proposition and Logic]] 

The truth table for A implies B (or “if A then B”) is:

This is because A being false does not imply anything so A → B holds, whereas when A is true, A has to imply B and a true statement cannot imply a false statement.

| A | B | A **→** B |
| --- | --- | --- |
| 0 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

# “Only if A” then B

A **←** B means A only if B, meaning if B is true, A must be true. 

> [!note] 🔥
> A **←** B = B **→** A

| A | B | A **←** B |
| --- | --- | --- |
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

# “If and only if” (Iff)

B is true if and only if A is True (Combines A **→** B &  A **←** B)

> [!note] 🔥
> A iff B is true when A and B are the same value, think of as a logical “=”
> Iff is commutative, so A ↔ B = B ↔ A 

| A | B | A ↔ B |
| --- | --- | --- |
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

# Tautologies

Tautologies are logical statements that are always true, Eg. A ∪ 1

## (**¬**A **∪** B) ↔ (A **→ **B) Tautology

This truth table shows the above always holds

| A | B | (**¬**A ∪ B) | (A **→ **B) | (**¬**A ∪ B) ↔ (A **→ **B) |
| --- | --- | --- | --- | --- |
| 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

## (A **∩** B) ∪ **¬A** **→** (B ↔ True) Not a tautology 

This truth table shows the above does not hold, this simplifies to A ∪ B.

Some combination of A and B’s values satisfies the logic therefore it is known as satisfiable. 

| A | B | (A **∩** B) ∪ **¬A** | (B ↔ True) | (A **∩** B) ∪ **¬A** **→** (B ↔ True) |
| --- | --- | --- | --- | --- |
| 0 | 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

## (A **∩ **B) **→** C ↔ A **→** (B **→** C) Tautology

| A | B | C | (B **→** C) |  A **→** (B **→** C) | (A **∩ **B) **→** C | (A **∩ **B) **→** C ↔ A **→** (B **→** C) |
| --- | --- | --- | --- | --- | --- | --- |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 |
| 0 | 1 | 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 1 | 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 1 | 1 | 1 | 1 |
| 1 | 0 | 1 | 1 | 1 | 1 | 1 |
| 1 | 1 | 0 | 0 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 | 1 | 1 |

# Contradictions & Law of Excluded Middle 

> [!note] 🔥
> A ∪ **¬**A is a tautology but A **∩ ¬**A is always false so it is a contradiction

| A | **¬A** | A ∪ **¬**A | A **∩ ¬**A |
| --- | --- | --- | --- |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |

# Useful logic table

![[lecture-2-tautologies.png]]