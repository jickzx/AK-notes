---
notion-id: 28b982ca-e761-80b3-9089-f60f968fa2a8
---
# ++a and a++

There is a difference. 

The difference lies in **when** the increment happens relative to evaluation:

- `++a` → **Pre-increment**
    - Increments `a` first, then returns the **new** value
    - Example:
```c
int a = 5;
int b = ++a; // a = 6, b = 6
```
- `a++` → **Post-increment**
    - Returns the **current** value first, then increments `a`
    - Example:
```c
int a = 5;
int b = a++; // b = 5, then a = 6
```

# Evaluation order

There is an order of precedence for operations in C

![[week-2-learning-more-c.png]]

## Short Circuit order

Logical expressions are evaluated as soon as the result is determined, skipping unnecessary expressions. 

For example, OR skips the RHS if the LHS is true.

AND is evaluated left to right and if the LHS is false, the RHS isn’t evaluated.

**Example:**

```c
if (x == 3 && ++x == 4)
```

If `x == 3` is false, `++x == 4` is skipped so x is never incremented