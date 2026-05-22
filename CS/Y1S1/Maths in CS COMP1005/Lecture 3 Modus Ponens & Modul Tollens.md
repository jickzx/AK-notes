---
notion-id: 283982ca-e761-80da-9192-cdffda5734e3
---
If a formula is satisfiable, then there is some assignment of values to
the atomic propositions which will make the formula true

---

**¬P∨Q ↔ (P → Q)**

![[lecture-3-modus-ponens-and-modul-tollens-01.png]]

---

# Equivalence: ≡

If two formulas have the same truth values for ALL rows, they are equivalent – the formulas will always have the same value

Difference between equivalence and iff?

> [!note] 🔥
> R ≡ S is a statement about two formulas, R and S, being equivalent
R **↔** S is a single formula, which, if a tautology, means R ≡ S

---

## De Morgan’s Law

> [!note] 🔥
> **¬(P∧Q)  ≡ ¬P ∨ ¬Q and vice versa**

---

# Entailment

## Modus Ponens

> [!note] 🔥
> A is true, A → B is true therefore we can conclude B is true

## Modus Tollens

> [!note] 🔥
> ¬B is true (B is false), A → B is true, therefore we can conclude that A is not true

![[lecture-3-modus-ponens-and-modul-tollens-02.png]]

![[lecture-3-modus-ponens-and-modul-tollens-03.png]]

## Entailment: ⊨

> [!note] 🔥
> Formalises relationships between formulae into logic. Eg: A, A**→**B ⊨ B
If P **∧** Q **∧** …  R is a tautology, then  P , Q , … ⊨ R

Implication is a single formula, entailment is a relationship between formulae

Examples of valid entailments: 

![[lecture-3-modus-ponens-and-modul-tollens-04.png]]

$$
\begin{array}{lll}P, Q \;\vDash\; P \land Q &\quad&P \land Q \;\vDash\; P \lor Q &\quad&\neg (P \lor Q) \;\vDash\; \neg (P \land Q) \\[1em]P \;\vDash\; P \lor Q\end{array}
$$

You can disprove logic using counterexamples

![[lecture-3-modus-ponens-and-modul-tollens-05.png]]

---

# Alternatives to checking truth tables

Checking truth tables for entailments is inefficient, there must be a better way

There are standard equivalencies that make logic easier. They are in [[Standard Equivalencies & Logical Symbols]].

---

# Practice Exercises

[moodle.nottingham.ac.uk](https://moodle.nottingham.ac.uk/pluginfile.php/11824674/mod_resource/content/5/E1A-propositions%20practice%20exercises%202023.pdf)

1a.  Prove P ∨¬Q ≡ Q → P using a truth table. 

As P ∨¬Q ↔ Q → P is a tautology, P ∨¬Q ≡ Q → P holds

| P | Q | P ∨¬Q | Q → P | P ∨¬Q ↔ Q → P |
| --- | --- | --- | --- | --- |
| 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 1 | 1 |
| 1 | 1 | 1 | 1 | 1 |

1b: Prove (P ⇒Q)∨(P ⇒R) ≡ P ⇒(Q∨R) using a truth table.

As (P ⇒Q)∨(P ⇒R) ↔ P ⇒(Q∨R) is a tautology, (P ⇒Q)∨(P ⇒R) ≡ P ⇒(Q∨R) holds

| P | Q | R | (P ⇒Q) | (P ⇒R) | (P ⇒Q)∨(P ⇒R) | (Q∨R) | P ⇒(Q∨R) | (P ⇒Q)∨(P ⇒R) ↔ P ⇒(Q∨R) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 1 |
| 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 |
| 1 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 |
| 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |

1c: Prove ¬(P ∧¬Q)∨(R⇒ False ) ≡ (P ∧R)⇒Q using a truth table.

As  ¬(P ∧¬Q)∨(R ⇒ False ) ↔ (P ∧ R) ⇒ Q is a tautology, ¬(P ∧¬Q)∨(R⇒ False ) ≡ (P ∧R)⇒Q holds

| P | Q | R | ¬(P ∧¬Q) | R ⇒ False | ¬(P ∧¬Q) ∨<br>(R ⇒ False ) | P ∧ R | (P ∧ R) ⇒ Q |  ¬(P ∧¬Q)∨(R ⇒ False ) ↔ (P ∧ R) ⇒ Q  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 1 |
| 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | 1 |
| 0 | 1 | 1 | 1 | 0 | 1 | 0 | 1 | 1 |
| 1 | 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 |
| 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | 1 |
| 1 | 1 | 1 | 1 | 0 | 1 | 1 | 1 | 1 |

2a: Find the relation between P ∧(Q∨R) and (P ∧Q)∨P using a truth table.

Let A be  P∧(Q∨R), B be (P∧Q)∨P

Since A → B is a tautology, A ⊨ B. Another way this is proven is that B is true when A is true so the last column is unnecessary.

| P | Q | R | Q∨R | P∧Q |  P∧(Q∨R) | (P∧Q)∨P |  P∧(Q∨R) → (P ∧Q)∨P  |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 |
| 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 |
| 0 | 1 | 1 | 1 | 1 | 0 | 1 | 1 |
| 1 | 0 | 0 | 0 | 0 | 0 | 1 | 1 |
| 1 | 0 | 1 | 1 | 1 | 1 | 1 | 1 |
| 1 | 1 | 0 | 1 | 0 | 1 | 1 | 1 |
| 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |

2b: Find the relation between P ∨(Q∧R) and (P ∨ Q)∧(P ∨ R) using a truth table.

Let A be (P ∨ Q)∧(P ∨ R) and B be P ∨(Q∧R)

As A↔B is a tautology, A ≡ B. This is self evident through distributive law

| P | Q | R | P ∨ Q | P ∨ R | (P ∨ Q)∧(P ∨ R) | P ∨(Q∧R)  | P ∨(Q∧R) ↔ (P ∨ Q)∧(P ∨ R) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 |
| 0 | 1 | 0 | 1 | 0 | 0 | 0 | 1 |
| 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 1 | 1 | 1 | 1 | 1 |
| 1 | 0 | 1 | 1 | 1 | 1 | 1 | 1 |
| 1 | 1 | 0 | 1 | 1 | 1 | 1 | 1 |
| 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |

2c: Find the relation between P ⇒(Q⇒R) and (P ⇒Q)⇒R using a truth table.

Let A be P ⇒(Q⇒R), B be (P ⇒Q)⇒R. 

As B → A is a tautology, B ⊨ A

| P | Q | R | P ⇒Q | Q⇒R | (P ⇒Q)⇒R | P ⇒(Q⇒R) | P ⇒(Q⇒R) **← **(P ⇒Q)⇒R |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 |
| 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 |
| 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 | 1 | 1 | 1 | 1 |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 |
| 1 | 1 | 0 | 1 | 0 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |

3a: Find all truth assignments that satisfy (P ⇔Q)∧(¬P ⇒Q):

| P | Q | P ⇔ Q | ¬P ⇒Q | (P ⇔Q)∧(¬P ⇒Q) |
| --- | --- | --- | --- | --- |
| 0 | 0 | 1 | 0 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 1 | 1 | 1 | 1 |

3b: Find all truth assignments that satisfy (P ∨¬Q∨R)∧(P ∨Q)∧(¬P ∨¬R).

| P | Q | R | P ∨¬Q∨R | P ∨ Q | (P ∨¬Q∨R)∧(P ∨Q) | ¬P ∨¬R | (P ∨¬Q∨R)∧(P ∨Q)∧(¬P ∨¬R) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 |
| 0 | 0 | 1 | 1 | 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 1 | 1 | 1 | 1 | 1 |
| 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 |
| 1 | 1 | 0 | 1 | 1 | 1 | 1 | 1 |
| 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 |

4: 

Translate the following natural language statements into appropriate propositional formulas (regardless of their truth values, i.e., some of them may not be true):

a:  If the earth is flat, then it is not a globe, and if the earth is not a globe, then global warming is a hoax.

Let A be “the earth is flat”, B be “the earth is a globe”, C be “global warming is a hoax”

(A → ¬B) ∧ (¬B → C), This simplifies to A → C

b: 

You attended the lectures, you did your homework, and you studied for the exam, therefore you passed Mathematics.

Let A be “You attended lectures”, B be “You did your homework”, C be “You studied for your exam”, D be “You passed Mathematics”

(A ∧ B ∧ C) → D 

c:  Saying that if you smell essential oils then you will be cured is the same as saying modern medicine does not work.

Let A be “you smell essential oils””, B be “you will be cured”, C be “, B be “, B be “youY, B be “”

Let B be “you will be cured”

Let C be “modern medicine works”

(A → B) ↔ C

5: 

Consider the following lines of reasoning. What are the premisses? What are the conclusions? Demonstrate that
these lines of reasoning are valid.

a:

A number is either even or odd. Therefore, if a number is not even, it must be odd.

Propositions: A = Number is even, B = Number is odd

Premises: A ∨ B = Either number is even or odd. 

Conclusion: ¬A → B, If a number is not even then it is odd

This is true as A∨B≡¬A→B

b: 

If Arsenal is better than Bayern, and Bayern is better than Chelsea, then Arsenal is better than Chelsea. Arsenal is not better than Chelsea. Therefore, Bayern is not better than Chelsea, or Arsenal is not better than Bayern.

Propositions: 

A = Arsenal is better than Bayern, 

B = Bayern is better than Chelsea, 

C = Arsenal is better than Chelsea. 

Premises: (A ∧ B) → C, ¬C ⊨¬B∨¬A

Why this is valid: By modus tollens, as ¬C is true, ¬(A ∧ B) is true, so ¬B∨¬A is true by De Morgan’s law 

c: 

| P | Q | R | **(P ⇒ Q)** | **(¬P ⇒ R)** | **¬(Q ∧ R)** |
| --- | --- | --- | --- | --- | --- |
| 0 | 0 | 0 | 1 | 0 | 1 |
| 0 | 0 | 1 | 1 | 1 | 1 |
| 0 | 1 | 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 1 | 1 | 0 |
| 1 | 0 | 0 | 0 | 1 | 1 |
| 1 | 0 | 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 1 | 1 | 1 |
| 1 | 1 | 1 | 1 | 1 | 0 |