# Universal Recurrence Relations for Weighted Power Sums

Throughout this document, let x, y, z be distinct non-zero real numbers.

Our goal is to understand how expressions built from powers of these numbers behave, and to show that they satisfy universal recurrence rules that apply across a wide range of situations.

---
## 1. Definition of Weighted Power Sum Functions
For coefficients k, l, m, define the weighted power sum as follows. We explicitly allow n to be any integer, including negative values.

- **f_n(k,l,m) = kx^n + ly^n + mz^n**
- **g_n(k,l,m) = k/x^{n} + l/y^{n} + m/z^{n}**

The two functions are related by:

- **f_{-n}(k,l,m) = g_n(k,l,m)**
- **g_{-n}(k,l,m) = f_n(k,l,m)**

So g is simply f evaluated at a negative index. We keep both names for convenience, as each arises naturally in different contexts.

When there is no risk of confusion, we will write f_n rather than f_n(k,l,m).

### Isolating a Single Power
By the definition of the weighted power sum function, it is possible to isolate individual powers:

- **x^n = f_n(1,0,0)**
- **y^n = f_n(0,1,0)**
- **z^n = f_n(0,0,1)**

We will make use of this fact later.

---
## 2. Elementary Symmetric Polynomials
The three numbers x, y, z determine three fundamental combinations called the elementary symmetric polynomials:

- **s_n = x^n + y^n + z^n**
- **t_n = (xy)^n + (yz)^n + (zx)^n**
- **u_n = (xyz)^n**

A key fact from algebra is that x^n, y^n, z^n are exactly the three roots of the cubic equation:

- **X^3 - s_n X^2 + t_n X - u_n = 0**

This equation is the engine behind everything that follows.

### Case n = 1 for Elementary Polynomials
We also define the special symmetric polynomials s, t, u:

- **s = s_1**
- **t = t_1**
- **u = u_1**

There is a useful relation, which we will use throughout:

- **u_n = u^n**

### Expressing Symmetric Polynomials as Weighted Power Sum Functions

By the definitions of the elementary symmetric polynomials and the weighted power sum functions, we can write:

- **s_n = f_n(1,1,1)**
- **t_n = f_n(y^n,z^n,x^n) = f_n(z^n,x^n,y^n)**
- **u_n = (1/3) f_n(y^nz^n, z^nx^n, x^ny^n)**

---
## 3. Linearity Properties
The functions f_n and g_n are linear in their coefficients:

Homogenity:
- **f_n(ak, al, am) = a f_n(k,l,m)**
- **g_n(ak, al, am) = a g_n(k,l,m)**

Additivity:
- **f_n(k_1+k_2, l_1+l_2, m_1+m_2) = f_n(k_1,l_1,m_1) + f_n(k_2,l_2,m_2)**
- **g_n(k_1+k_2, l_1+l_2, m_1+m_2) = g_n(k_1,l_1,m_1) + g_n(k_2,l_2,m_2)**

This means any weighted sum can be built by using single powers f_n(1,0,0) = x^n, f_n(0,1,0) = y^n, and f_n(0,0,1) = z^n. They serve as the building blocks for everything.

---
## 4. The Generalized Newton Identity

Using the cubic that each x,y,z satisfies and summing up with the right weights gives:

- **f_n = s f_{n-1} - t f_{n-2} + u f_{n-3}**
- **g_n = (t/u) g_{n-1} - (s/u) g_{n-2} + (1/u) g_{n-3}**

Both hold for **any** choice of weights **k, l, m** and for all integers **n**. 

The recurrences can also be rearranged to step backwards:

- **f_{n-3} = (1/u) f_n - (s/u) f_{n-1} + (t/u) f_{n-2}**
- **g_{n-3} = u g_n - t g_{n-1} + s g_{n-2}**

This lets us compute f and g at negative indices from initial values without any issues.

---
## 5. Universal Linear Representation

Because each term depends on the previous three, every value of **f_n** is completely determined by any three consecutive values. In particular, using f_0, f_1, f_2 as the base:

- **f_n = K(n) f_2 + L(n) f_1 + M(n) f_0**
- **g_n = P(n) g_2 + Q(n) g_1 + R(n) g_0**

The coefficients **K(n), L(n), M(n)** and **P(n), Q(n), R(n)**:

- depend only on **s, t, u**,
- **do not depend** on **k, l, m**.

### Expressing single powers with K,L,M

The special case of the formulas above is:
- **x^n = f_n(1,0,0) = K(n) x^2 + L(n) x + M(n)**
- **y^n = f_n(0,1,0) = K(n) y^2 + L(n) y + M(n)**
- **z^n = f_n(0,0,1) = K(n) z^2 + L(n) z + M(n)**

---
## 6. Recursive Computation of Universal Coefficients

### 6.1 Coefficients K, L, M

The sequences **K(n), L(n), M(n)** each satisfy the same recurrence as **f_n**:

- **K(n) = s K(n-1) - t K(n-2) + u K(n-3)**
- **L(n) = s L(n-1) - t L(n-2) + u L(n-3)**
- **M(n) = s M(n-1) - t M(n-2) + u M(n-3)**

with initial conditions chosen so that the three sequences act as a basis:

- **K(0)=0, K(1)=0, K(2)=1**
- **L(0)=0, L(1)=1, L(2)=0**
- **M(0)=1, M(1)=0, M(2)=0**

These recurrences can be verified by induction.

### 6.2 Coefficients P, Q, R

The sequences **P(n), Q(n), R(n)** each satisfy the same recurrence as **g_n**:

- **P(n) = (t/u) P(n-1) - (s/u) P(n-2) + (1/u) P(n-3)**
- **Q(n) = (t/u) Q(n-1) - (s/u) Q(n-2) + (1/u) Q(n-3)**
- **R(n) = (t/u) R(n-1) - (s/u) R(n-2) + (1/u) R(n-3)**

with the same pattern of initial conditions:

- **P(0)=0, P(1)=0, P(2)=1**
- **Q(0)=0, Q(1)=1, Q(2)=0**
- **R(0)=1, R(1)=0, R(2)=0**

---
## 7. Explicit Formulas for K(n) and P(n)

The coefficients K(n) and P(n) have closed-form expressions. These can be derived by applying the universal representation to the three single-variable cases **f_n(1,0,0)**, **f_n(0,1,0)**, **f_n(0,0,1)** and solving the resulting system:

- **-(x-y)(y-z)(z-x) K(n) = x^n(y-z) + y^n(z-x) + z^n(x-y)**
- **-(x-y)(y-z)(z-x) P(n) = (y-z)/x^n + (z-x)/y^n + (x-y)/z^n**

The factor **-(x-y)(y-z)(z-x)** is a non-zero constant (since x, y, z are distinct), so these formulas uniquely determine K(n) and P(n) for all integers n.

**Relation between f_n, g_n and K(n), P(n)**:
From the explicit formulas it's immediately visible that:

- **-(x-y)(y-z)(z-x) K(n) = f_n(y-z, z-x, x-y)**
- **-(x-y)(y-z)(z-x) P(n) = g_n(y-z, z-x, x-y)**

Given the fact that **f_n = g_{-n}** we also obtain
- **K(n) = P(-n)**
- **P(n) = K(-n)**

---

## 8. Relationships Between the Coefficients

Since K(n) and P(n) are the primary sequences, all other coefficients can be expressed in terms of them.

### 8.1 Fundamental Relations

**Relations for L and M:**
- **L(n) = K(n+1) - s K(n)**
- **M(n+1) = u K(n)**

**Relations for Q and R:**
- **Q(n) = P(n+1) - (t/u) P(n)**
- **R(n+1) = (1/u) P(n)**

These relations can be proven by induction. The result is that K and P are master sequences and the other sequences can be expressed using it.

### 8.2 Compact Forms for f_n and g_n

Substituting the relations above into the universal representation gives formulas that depend only on K and P:

- **f_n = K(n) f_2 + (K(n+1) - s K(n)) f_1 + u K(n-1) f_0**
- **g_n = P(n) g_2 + (P(n+1) - (t/u) P(n)) g_1 + (1/u) P(n-1) g_0**

---
## 9. Shift Invariance

The universal representation is not tied to the base indices 0, 1, 2. For any integers **n** and **j**, the same coefficients allow us to shift the base:

- **f_{n+j} = K(n) f_{j+2} + L(n) f_{j+1} + M(n) f_j**
- **g_{n+j} = P(n) g_{j+2} + Q(n) g_{j+1} + R(n) g_j**

### Why This Works

Fix any integer **j** and define the shifted sequence **h_n = f_{n+j}**. Then h_n satisfies exactly the same recurrence as f_n, since the recurrence only involves differences of indices. The universal representation therefore applies to h_n with base values h_0 = f_j, h_1 = f_{j+1}, h_2 = f_{j+2}, giving the result. The argument for g is identical.

---
## 10. The Weight-Sum Identity and Its Consequences

By using shift invariance for **s = -n** and the relation **f_{-n} = g_n** we obtain these relations:

- **k+l+m = P(n) f_{n-2} + Q(n) f_{n-1} + R(n) f_n**
- **k+l+m = K(n) g_{n-2} + L(n) g_{n-1} + M(n) g_n**

The identities hold for all integers **n** and any weights **k, l, m**.

### 10.1 The Case k+l+m = 0

When the weights sum to zero, the identities become:

- **P(n) f_{n-2} + Q(n) f_{n-1} + R(n) f_n = 0**
- **K(n) g_{n-2} + L(n) g_{n-1} + M(n) g_n = 0**

This is a linear relation among three consecutive values of f that holds for **all** integers n. 

### 10.2 The formula for K and P

We already know the relation between **K** and **f_n(y-z, z-x, x-y)**, so we also immediately obtain:

- **P(n+2) K(n) + Q(n+2) K(n+1) + R(n+2) K(n+2) = 0**
- **K(n+2) P(n) + L(n+2) P(n+1) + M(n+2) P(n+2) = 0**

Using the formulas above, we get relation between master sequences P and Q:

- **P(n)K(n+2) + u P(n+2) K(n+1) + u P(n+1) K(n) = t K(n+1) P(n+1)**

### 10.3 The formula for single power

By applying the formula for **k = 1, l = 0, m = 0** we obtain:
- **1 = P(n)x^{n-2} + Q(n)x^{n-1} + R(n)x^n**
- **1 = K(n)/x^{n-2} + L(n)/x^{n-1} + M(n)/x^n**

---
## 11. Compact Formulas for the Ordinary Power Sum

Setting **(k,l,m) = (1,1,1)** in the universal representation and simplifying using the definitions of K, L, M (and P, Q, R) gives clean identities involving only K and P:

- **f_n(1,1,1) = x^n+y^n+z^n = 3K(n+2) - 2s K(n+1) + t K(n)**
- **g_n(1,1,1) = 1/x^n+1/y^n+1/z^n = 3P(n+2) - 2(t/u) P(n+1) + (s/u) P(n)**

These express the classical power sums entirely in terms of the master sequences K and P.

---
## 12. Expressing K via Power Sums - Part 1

From Section 11, the ordinary power sums **s_n = x^n + y^n + z^n** satisfy:

- **s_n = 3K(n+2) - 2s K(n+1) + t K(n)**

Rearranging gives an alternative recurrence for K driven by the power sums:

- **K(0) = 0**
- **K(1) = 0**
- **K(n+2) = (2/3)s K(n+1) - (1/3)t K(n) + (1/3)s_n**

Since the right-hand side at each step introduces exactly one new power sum s_n, iterating this recurrence shows that K(n+2) is always a linear combination of s_0, s_1, ..., s_n. We can therefore write:

- **K(n+2) = Σ_{m=0}^{n} W_m(n-m) s_m**

for some coefficients W_m(n). We are building W_m backwards, because that will be more convenient later.

---

## 13. Expressing K via Power Sums - Part 2

By substituting the expression for K into the recurrence from Section 12, we obtain (for each fixed m) the following recurrence relation for the coefficients W_m(j):

- **W_m(0) = 1/3**
- **W_m(1) = (2/9)s**
- **W_m(j+2) = (2/3)s W_m(j+1) - (1/3)t W_m(j)**

This recurrence is the same for every m including the initial conditions. Therefore, the shape of the recurrence is universal, and we may drop the subscript and simply write:

- **W(0) = 1/3**
- **W(1) = (2/9)s**
- **W(j+2) = (2/3)s W(j+1) - (1/3)t W(j)**

**Reindexing.** In the sum for **K(n+2)** from Section 12, each W_m depends only on the lag j = n-m, not on m itself. Relabelling gives the equivalent form:

- **K(n+2) = Σ_{m=0}^{n} W(m) s_{n-m}**

where now W(m) is the coefficient of s_{n-m}
