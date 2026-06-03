---
notion-id: 27d982ca-e761-8021-90dd-e0c40bf59085
---
Proposition is an expression that is either True or False, depending on nothing outside it.

Eg: 3<6: True

A predicate is a parameterised proposition. 

Eg: x>6: Depends on x.

Propositions can be combined with logic to make larger ones. 

A proposition that cannot be subdivided is atomic. One that can is a compound proposition.

Basic Logical Operators:

- **Conjunction (AND, ∧, ∩):** P ∧ Q is True if and only if both P and Q are True
- **Disjunction (OR, ∨, ∪):** P ∨ Q is True if and only if at least one of P or Q is True
- **Negation (NOT, ¬, overline):** $\overline{P}$ is True if and only if P is False
- **Implication (→, ⊆):** P → Q is True if P is False or Q is True. It's only False when P is True and Q is False

Truth tables for these operators help visualise all possible combinations:

| P | Q | P ∧ Q | P ∨ Q | ¬P | P → Q |
| --- | --- | --- | --- | --- | --- |
| T | T | T | T | F | T |
| T | F | F | T | F | F |
| F | T | F | T | T | T |
| F | F | F | F | T | T |

| P | Q | P-Q | Q-P |
| --- | --- | --- | --- |
| 1 | 1 | 0 | 0 |
| 1 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 |
| 0 | 0 | 0 | 0 |

This table is **¬**(P **→ Q)**