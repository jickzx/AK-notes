---
notion-id: 29b982ca-e761-800b-9b3f-e1a60d4b3db1
---
# Proof Rules

Proofs follow logical reasoning steps, which are outlined below:

Here is a clear reference table of the **standard natural deduction reasoning rules** used in propositional logic.

## **Table of Natural Deduction Rules**

### **Conjunction ( ∧ )**

| **Rule Name** | **Form** | **Explanation** |
| --- | --- | --- |
| ∧-Introduction | from (P) and (Q) infer (P ∧ Q) | Combine two statements |
| ∧-Elimination | from (P ∧ Q) infer (P) or infer (Q) | Extract either part of a conjunction |

### **Disjunction ( ∨ )**

| **Rule Name** | **Form** | **Explanation** |
| --- | --- | --- |
| ∨-Introduction | from (P) infer (P ∨ Q); from (P) infer (Q ∨ P) | Add a disjunct |
| ∨-Elimination (Proof by Cases) | from (P ∨ Q), and from (P) derive (R), and from (Q) derive (R), infer (R) | Conclude something from all cases |

### **Implication ( ⇒ )**

| **Rule Name** | **Form** | **Explanation** |
| --- | --- | --- |
| ⇒-Introduction | from assumption (P) derive (Q), infer (P ⇒ Q) | Discharge assumption to form an implication |
| ⇒-Elimination (*Modus Ponens*) | from (P ⇒ Q) and (P), infer (Q) | Apply an implication |

### **Negation ( ¬ )**

| **Rule Name** | **Form** | **Explanation** |
| --- | --- | --- |
| ¬-Introduction | assume (P), derive (⊥), infer (¬P) | Proof by contradiction (constructive) |
| ¬-Elimination | from (¬P) and (P), infer (⊥) | Detect contradiction |
| Explosion (**ex falso**) | from (⊥) infer any (Q) | Anything follows from contradiction |

### **Biconditional ( ↔ )**

| **Rule Name** | **Form** | **Explanation** |
| --- | --- | --- |
| ↔-Introduction | from (P ⇒ Q) and (Q ⇒ P), infer (P ↔ Q) | Show equivalence |
| ↔-Elimination | from (P ↔ Q) infer (P ⇒ Q) and infer (Q ⇒ P) | Unpack equivalence |

### **Double Negation**

| **Rule Name** | **Form** | **Explanation** |
| --- | --- | --- |
| Double Negation | from (P) infer (¬¬P), and from (¬¬P) infer (P) | Removes or adds two negations (classical logic) |

### **Law of Excluded Middle (classical only)**

| **Rule Name** | **Form** | **Explanation** |
| --- | --- | --- |
| LEM | (P ∨ ¬P) | Every proposition is either true or false |

# Forming implications

<!-- Column 1 -->
Form implications with assumption flags. You can form an implication from the proposition in the assumption flag and the proposition at the end of it

Eg:

<!-- Column 2 -->
![[how-to-write-proofs-01.png]]

# Propositional Proofs

![[how-to-write-proofs-02.png]]

![[how-to-write-proofs-03.png]]

![[how-to-write-proofs-04.png]]