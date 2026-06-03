# Null Space

## Definition

If $A$ is an $m \times n$ matrix, the null space of $A$ is the set of all solutions of the homogeneous equation $A\mathbf{x}=0$.

$$
\operatorname{Nul}(A)=\{\mathbf{x}\in\mathbb{R}^n \mid A\mathbf{x}=0\}.
$$

## Example

If

$$
A=
\begin{pmatrix}
1 & 1\\
1 & 1\\
1 & 1
\end{pmatrix},
$$

then row reducing gives

$$
\begin{pmatrix}
1 & 1\\
1 & 1\\
1 & 1
\end{pmatrix}
\xrightarrow{\text{RREF}}
\begin{pmatrix}
1 & 1\\
0 & 0\\
0 & 0
\end{pmatrix}.
$$

So the equation $A\mathbf{x}=0$ becomes

$$
x+y=0,
$$

which means

$$
\begin{pmatrix}
x\\
y
\end{pmatrix}
=
y
\begin{pmatrix}
-1\\
1
\end{pmatrix}.
$$

Therefore,

$$
\operatorname{Nul}(A)=
\operatorname{Span}
\left\{
\begin{pmatrix}
-1\\
1
\end{pmatrix}
\right\}.
$$

This is a line in $\mathbb{R}^2$.

## Why It Matters

The null space is a [[Subspace|subspace]] and describes all homogeneous solutions of a matrix equation.

In the example above, the null space is a line in $\mathbb{R}^2$. So:

- if
  $$
  \mathbf{x}=
  \begin{pmatrix}
  -2\\
  2
  \end{pmatrix},
  $$
  then $\mathbf{x}$ lies on that line, so $A\mathbf{x}=0$
- if
  $$
  \mathbf{x}=
  \begin{pmatrix}
  1\\
  0
  \end{pmatrix},
  $$
  then $\mathbf{x}$ does not lie on that line, so $A\mathbf{x}\neq 0$

So the null space answers the question: which vectors $\mathbf{x}$ get sent to zero by the matrix $A$?

## Appears In

- [[3.1 Solution Sets and Subspaces]]
- [[3.3 Subspaces]]

## Related

- [[Homogeneous System]]
- [[Solution Set]]
- [[Column Space]]
