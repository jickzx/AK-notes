---
notion-id: 28e982ca-e761-8080-9fe1-c69136bc0d4a
---
Predicates are paramaterised propositions that act across sets

## Universal Quantifier: ∀ means true for all the set

E.g.: for all students in this class, the student is paying attention
• ∀ x∈X ( P(x) )   : for all elements x in some set X, predicate P(x) holds (is true)
• x is a student, X is set of all students in the class, P(x) means x is paying
attention
• Need to check P(x) for every x, to ensure that this statement is true
• If any fail then we have a counter-example
• Counterexample: a value x for which P(x) is false

## There exists in a set: ∃ true for at least one in the set

E.g., there exists some student in this class who is paying attention
•  xX ( P(x) )   : for at least one element x in some set X,
predicate P(x) holds
• where x is a student, X is set of all students in the class, P(x) means x is
paying attentio

# Bound, Free and Fresh Variables

Consider F(v) : ∃ x ∈ X (x = v)

x is a bound variable because it is defined and ‘bound’ within the scop of the operator ∃. It has no meaning outside of the ∃, it is only used by the ∃.

v is a free variable because it is not tied to any operators, so it is used but not bound to anything, it is considered a parameter or an input that can be used anywhere in the formula.

A variable is fresh in scope if it is neither free nor bound within that scope. If the variable isn’t being used in the scope then it is considered fresh. For instance, a is a fresh variable in the predicate because we didn’t use it.

![[lecture-6-predicates.png]]

# Practice question

Assume A $\subseteq$ B . Does $∀ x ∈ A (P(x))  ⊨  ∀ x ∈ B (P(x))$?

We can rename the bound variable $x$ to a fresh variable like $a$ and $b$ for clarity, yielding $∀ a ∈ A  (P(a)) ⊨ ∀ b ∈ B  (P(b))$

This entailment does **not** hold. The reason is that $A \subseteq B$ means there are elements in $B$ that are not in $A$. While $∀ x ∈ A ( P(x))$ asserts that every element of $A$  satisfies $P(x)$, there’s no information about the elements of

$B \setminus A$. These extra elements in $B$ could fail to satisfy $P(x)$, so we cannot conclude that $∀ x ∈ B , P(x)$ must hold. Therefore, the entailment is false.

However, since A $\subseteq$ B, it must hold that for all elements of $B$ that satisfy $P(x)$, those elements in $A$ also satisfy $P(x)$.

 $\therefore ∀ x ∈ B (P(x))  ⊨  ∀ x ∈ A (P(x))$ 

## More

Assume A $\subseteq$ B. Does $∃ x ∈ B (P(x))  ⊨  ∃ x ∈ A (P(x))$?

This statement means that if there exists some x in B that satisfies P(x), there must exist some x in A that satisfies P(x). 

This is clearly false as$A \subseteq B$, the counterexample is if x is in  $B \setminus A$, then the RHS doesn’t hold as $x$ isnt in $A$.

However, the entailment does hold the other way round as all $A$ is in $B$, so if there exists some $x$ in $A$ that satisfies $P(x)$, that $x$ is also in $B$ and satisfies $P(x)$.

$\therefore ∃ x ∈ A (P(x))  ⊨  ∃ x ∈ B (P(x))$

# Another Practice Question

$∀ x ∈ S (W(x))$ where $S$ is the set of all swans and $W(x)$ is true if $x$ is white

This formula tells us that for all $x$ in $S$, $x$ satisfies $W(x)$, meaning all swans are white.

We can fix this by considering swans in the UK alone. 

Let $UK(x)$ be true if $x$ was in the UK.

Now we can saw that for all swans, if the swan is in the UK it’s white

$$
∀ x ∈ S (UK(x)\implies W(x))
$$

This means that for all x in S, if x is in the UK, it is white

You could also just change the set being checked so it is only UK swans

$$
UKS \subseteq S, ∀ x ∈ UKS (W(x))
$$

# Comparing ∃ and ∀

You can use ¬ to switch between ∃ and ∀. 

For instance, $¬∃ x ∈ C (V(x)) ≡ ∀ x ∈ C ( ¬V(x) )$ because if for all $x$ in $C$ there doesnt exist an $x$ that satisfies $V(x)$ then for all $x$ in $C$, $x$ does not satisfy $V(x)$.

## Considering finite sets - De Morgan’s Law

De Morgan’s Law allows us to convert between ∃ and ∀.

For instance:

$$
∀x ∈ \{1,2,3,..,n\} (¬P(x)) ≡ ¬P(1) ∧¬P(2)∧¬P(3)∧...∧¬P(n)
$$

Equivalently:

$$
¬∃x ∈ \{1,2,3,..,n\} (P(x)) ≡ ¬(P(1) ∨P(2)∨P(3)∨...∨P(n))
$$
