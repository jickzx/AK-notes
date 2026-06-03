---
notion-id: 292982ca-e761-8013-91de-ca85207c2cda
---
# Universal Quantifier and the Empty Set

> [!note] 🔥
> Vacuous Truth: A statement which is true because you are working over the empty set.

$\forall x \in \empty P(x)$ always holds as it is a vacuous truth.

Inversely, $\exists x \in \empty,P(x) \equiv \bot$

This is because $\forall x \in \empty P(x)$ is true iff there is no counterexample to the predicate. Since $\empty$ has no elements, there can be no counterexample, therefore it must be true. 

Formally:

$$
\forall x \in S,P(x)
$$

is equivalent to

$$
¬\exists x \in S : ¬P(x)
$$

For $S = \empty:$

$$
¬\exists x \in \empty : ¬P(x)
$$

Which becomes:

$$
\forall x \in \empty, P(x)
$$

Analogy: 

Saying “all unicorns have wings” is logically true because there are no unicorns to contradict it.

Another way of thinking abt this is you can flip

$$
\exists x \in \empty, P(x) \equiv \bot
$$

Flipping this gives

$$
\forall x \in \empty, P(x) \equiv \top
$$

---

# “There is exactly one in the set”

$\exists^1 a \in A,P(a)$ informally, don’t use

$$
\lnot ( \forall_{x \in C}( \exists_{y \in C} (y \in A) \Rightarrow \lnot (x \in B)) )
$$

$$
\exists_{x \in C}\lnot( \exists_{y \in C} (y \in A) \Rightarrow \lnot (x \in B))
$$

$$
\exists_{x \in C}( \lnot\exists_{y \in C} (y \in A) \Rightarrow \lnot (x \in B))
$$

$$
\exists_{x \in C}( \exists_{y \in C} \lnot((y \in A) \Rightarrow \lnot (x \in B)))
$$

$$
\exists_{x \in C}( \exists_{y \in C} \lnot((y \in A) \Rightarrow \lnot (x \in B)))
$$

$$
\exists_{x \in C}( \exists_{y \in C} (y \in A) \land (x \in B))
$$

there must exist some x in c, some y in c s.t y is in A and x is in B