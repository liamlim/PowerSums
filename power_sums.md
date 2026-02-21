# Universal Recurrence Relations for Weighted Power Sums

## Introduction

Throughout this document, let **x, y, z** be distinct non-zero real numbers.

Our goal is to understand how expressions built from powers of these numbers behave, and to show that they follow universal recurrence rules that work in many situations.

---

## Part 1: Setup

---

## 1. Definitions and Notation

For coefficients **k, l, m**, define the weighted power sum. We explicitly allow **n** to be any integer, including negative values.

- **f_n(k,l,m) = kx^n + ly^n + mz^n**
- **g_n(k,l,m) = kx^{-n} + ly^{-n} + mz^{-n}**

The two functions are related by:

- **f_{-n}(k,l,m) = g_n(k,l,m)**

So **g** is simply **f** evaluated at negative index. We keep both names for convenience, as each arises naturally in different contexts.

When there is no risk of confusion we will write **f_n** rather than **f_n(k,l,m)**.

### Examples

- **f_n(1,1,1) = x^n + y^n + z^n**
- **f_n(2,1,1) = 2x^n + y^n + z^n**
- **f_n(1,0,0) = x^n**
- **f_n(0,1,0) = y^n**
- **f_n(0,0,1) = z^n**

---

## 2. Elementary Symmetric Polynomials

The three numbers **x, y, z** determine three fundamental combinations called the elementary symmetric polynomials:

- **e_1 = x + y + z**
- **e_2 = xy + yz + zx**
- **e_3 = xyz**

A key fact from algebra is that **x, y, z** are exactly the three roots of the cubic equation:

- **t^3 - e_1 t^2 + e_2 t - e_3 = 0**

This equation is the engine behind everything that follows. Because each of x, y, z satisfies it, we can always replace a cube of any variable with a combination of lower powers, which is what drives the recurrences in Part 2.

---

## 3. Linearity Properties

The functions **f_n** and **g_n** are linear in their coefficients:

- **f_n(ak, al, am) = a f_n(k,l,m)**
- **g_n(ak, al, am) = a g_n(k,l,m)**
- **f_n(k_1+k_2, l_1+l_2, m_1+m_2) = f_n(k_1,l_1,m_1) + f_n(k_2,l_2,m_2)**
- **g_n(k_1+k_2, l_1+l_2, m_1+m_2) = g_n(k_1,l_1,m_1) + g_n(k_2,l_2,m_2)**

This means any weighted sum can be built by combining simpler ones. In particular, the single-variable cases **f_n(1,0,0) = x^n**, **f_n(0,1,0) = y^n**, **f_n(0,0,1) = z^n** are the building blocks for everything.

---

## Part 2: The Recurrence and Coefficients

---

## 4. The Generalized Newton Identity

Because each of x, y, z satisfies the cubic from Section 2, multiplying through by **t^{n-3}** gives **t^n = e_1 t^{n-1} - e_2 t^{n-2} + e_3 t^{n-3}** for each variable. Summing with weights k, l, m yields the recurrence for **f_n**, and a similar argument for **g_n**:

- **f_n = e_1 f_{n-1} - e_2 f_{n-2} + e_3 f_{n-3}**
- **g_n = (e_2/e_3) g_{n-1} - (e_1/e_3) g_{n-2} + (1/e_3) g_{n-3}**

Both hold for **any** choice of weights **k, l, m** and for all integers **n**. 

**Inversion symmetry**
 Replacing x, y, z by 1/x, 1/y, 1/z transforms f_n into g_n and sends the elementary symmetric polynomials as e_1 → e_2/e_3, e_2 → e_1/e_3, e_3 → 1/e_3. Therefore every result stated for g_n throughout this document follows from the corresponding f_n result by this substitution, without any separate derivation.

 The recurrences can also be rearranged to step backwards:

- **f_{n-3} = (1/e_3) f_n - (e_1/e_3) f_{n-1} + (e_2/e_3) f_{n-2}**
- **g_{n-3} = e_3 g_n - e_2 g_{n-1} + e_1 g_{n-2}**

This lets us compute f and g at negative indices from initial values without any issues.

---

## 5. Universal Linear Representation

Because each term depends on the previous three, every value of **f_n** is completely determined by any three consecutive values. In particular, using f_0, f_1, f_2 as the base:

- **f_n = K(n) f_2 + L(n) f_1 + M(n) f_0**
- **g_n = P(n) g_2 + Q(n) g_1 + R(n) g_0**

The coefficients **K(n), L(n), M(n)** and **P(n), Q(n), R(n)**:

- depend only on **e_1, e_2, e_3**,
- **do not depend** on **k, l, m**.

### Initial values

For f_n:
- **f_0 = k+l+m**
- **f_1 = kx+ly+mz**
- **f_2 = kx^2+ly^2+mz^2**

Similarly for g_n:
- **g_0 = k+l+m**
- **g_1 = k/x+l/y+m/z**
- **g_2 = k/x^2+l/y^2+m/z^2**

The same coefficients work for every choice of weights — only the initial values change. For example:

- **f_n(1,1,1) = K(n)(x^2+y^2+z^2) + L(n)(x+y+z) + 3M(n)**
- **f_n(2,1,1) = K(n)(2x^2+y^2+z^2) + L(n)(2x+y+z) + 4M(n)**
- **f_n(1,0,0) = x^n = K(n)x^2 + L(n)x + M(n)**

---

## 6. Recursive Computation of Universal Coefficients

### 6.1 Coefficients K, L, M

The sequences **K(n), L(n), M(n)** each satisfy the same recurrence as **f_n**:

- **X(n) = e_1 X(n-1) - e_2 X(n-2) + e_3 X(n-3)**

with initial conditions chosen so that the three sequences act as a basis:

- **K(0)=0, K(1)=0, K(2)=1**
- **L(0)=0, L(1)=1, L(2)=0**
- **M(0)=1, M(1)=0, M(2)=0**

It can be verified by induction that **f_n = K(n) f_2 + L(n) f_1 + M(n) f_0** holds for all n given these definitions.

### 6.2 Coefficients P, Q, R

The sequences **P(n), Q(n), R(n)** each satisfy the same recurrence as **g_n**:

- **X(n) = (e_2/e_3) X(n-1) - (e_1/e_3) X(n-2) + (1/e_3) X(n-3)**

with the same pattern of initial conditions:

- **P(0)=0, P(1)=0, P(2)=1**
- **Q(0)=0, Q(1)=1, Q(2)=0**
- **R(0)=1, R(1)=0, R(2)=0**

### 6.3 Helper sequence Px

Define the sequence Px by this definition:
- **Px(0) = 0**
- **Px(1) = 0**
- **Px(2) = e_3^2**
- **Px(n) = e_2 Px(n-1) - e_1 e_3 Px(n-2) + e_3^2 Px(n-3)**

By induction it's possible to prove the relation:
- **Px(n) = e_3^n P(n)**

As a consequence of this definition we know that if x,y,z are integers, then the way how to turn P(n) into an integer is simply multiplication by **e_3^n**

---

## 7. Explicit Formulas for K(n) and P(n)

The coefficients K(n) and P(n) have closed-form expressions. These can be derived by applying the universal representation to the three single-variable cases **f_n(1,0,0)**, **f_n(0,1,0)**, **f_n(0,0,1)** and solving the resulting system:

- **-(x-y)(y-z)(z-x) K(n) = x^n(y-z) + y^n(z-x) + z^n(x-y)**
- **-(x-y)(y-z)(z-x) P(n) = (y-z)/x^n + (z-x)/y^n + (x-y)/z^n**

The factor **-(x-y)(y-z)(z-x)** is a non-zero constant (since x, y, z are distinct), so these formulas uniquely determine K(n) and P(n) for all integers n.

Substituting n=2 into the formula for K(n) and simplifying, one finds that **K(2) = 1** which is consistent with the already established fact.

**Relation between f_n, g_n and K(n), P(n)**:
From the explicit formulas it's immediately visible that:

- **-(x-y)(y-z)(z-x) K(n) = f_n(y-z, z-x, x-y)**
- **-(x-y)(y-z)(z-x) P(n) = g_n(y-z, z-x, x-y)**

Given the fact that **f_n = g_{-n}** we also obtain
- **K(n) = P(-n)**

---

## 8. Relationships Between the Coefficients

Since K(n) and P(n) are the primary sequences, all other coefficients can be expressed in terms of them.

### 8.1 Fundamental Relations

**Relations for L and M:**
- **L(n) = K(n+1) - e_1 K(n)**
- **M(n+1) = e_3 K(n)**

**Relations for Q and R:**
- **Q(n) = P(n+1) - (e_2/e_3) P(n)**
- **R(n+1) = (1/e_3) P(n)**

Note that:
- **e_3^{n+1} R(n+1) = Px(n)**
- **e_3^{n+1} Q(n) = Px(n+1) - e_2 Px(n)**

These identifies show that if we have integers x,y,z then we transform R and Q into integers by multiplying by the right power of e_3.

### 8.2 Compact Forms for f_n and g_n

Substituting the relations above into the universal representation gives formulas that depend only on K and P:

- **f_n = K(n) f_2 + (K(n+1) - e_1 K(n)) f_1 + e_3 K(n-1) f_0**
- **g_n = P(n) g_2 + (P(n+1) - (e_2/e_3) P(n)) g_1 + (1/e_3) P(n-1) g_0**

---

## Part 3: Identities and Applications

---

## 9. Shift Invariance

The universal representation is not tied to the base indices 0, 1, 2. For any integers **n** and **s**, the same coefficients allow us to shift the base:

- **f_{n+s} = K(n) f_{s+2} + L(n) f_{s+1} + M(n) f_s**
- **g_{n+s} = P(n) g_{s+2} + Q(n) g_{s+1} + R(n) g_s**

### Why This Works

Fix any integer **s** and define the shifted sequence **h_n = f_{n+s}**. Then h_n satisfies exactly the same recurrence as f_n, since the recurrence only involves differences of indices. The universal representation therefore applies to h_n with base values h_0 = f_s, h_1 = f_{s+1}, h_2 = f_{s+2}, giving the result. The argument for g is identical.

---

## 10. The Weight-Sum Identity and Its Consequences

### 10.1 The Main Identities

- **k+l+m = P(n) f_{n-2} + Q(n) f_{n-1} + R(n) f_n**
- **k+l+m = K(n) g_{n-2} + L(n) g_{n-1} + M(n) g_n**

Both identities can be derived using shift invariance for **s = -n** and **f_n = g_{-n}**. The identities hold for all integers **n** and any weights **k, l, m**.

### 10.2 The Case k+l+m = 0

When the weights sum to zero, the identities become:

- **P(n) f_{n-2} + Q(n) f_{n-1} + R(n) f_n = 0**
- **K(n) g_{n-2} + L(n) g_{n-1} + M(n) g_n = 0**

This is a linear relation among three consecutive values of f that holds for **all** integers n. 

### 10.3 The formula for K and P

We already know the relation between **K** and **f_n** with the right weights, so we also immediately obtain:

- **P(n+2) K(n) + Q(n+2) K(n+1) + R(n+2) K(n+2) = 0**
- **K(n+2) P(n) + L(n+2) P(n+1) + M(n+2) P(n+2) = 0**

Using the formulas above, we get relation between master sequences P and Q:

- **P(n)K(n+2) + e_3 P(n+2) K(n+1) + e_3 P(n+1) K(n) = e_2 K(n+1) P(n+1)**

### 10.4 The formula for K and Px

By simple multiplication of the previous formula with **e_3^{n+1}** we obtain:
- **e_3 Px(n) K(n+2) + Px(n+2) K(n+1) + e_3 Px(n+1) K(n) = e_2 K(n+1) Px(n+1)**


---

## 11. Compact Formulas for the Ordinary Power Sum

Setting **(k,l,m) = (1,1,1)** in the universal representation and simplifying using the definitions of K, L, M (and P, Q, R) gives clean identities involving only K and P:

- **f_n(1,1,1) = x^n+y^n+z^n = 3K(n+2) - 2e_1 K(n+1) + e_2 K(n)**
- **g_n(1,1,1) = 1/x^n+1/y^n+1/z^n = 3P(n+2) - 2(e_2/e_3) P(n+1) + (e_1/e_3) P(n)**

These express the classical power sums entirely in terms of the master sequences K and P.

Multiplying the g_n formula through by **e_3^{n+2}** and using helper sequence **Px** gives:
- **e_3^2 f_n(y^n,z^n,x^n) = 3 Px(n+2) - 2e_2 Px(n+1) + e_1 e_3 Px(n)**

Where where f_n(y^n, z^n, x^n) stands for y^n x^n + z^n y^n + x^n z^n.

---

## 12. Expressing K via Power Sums - Part 1

From Section 11, the ordinary power sums **s_n = x^n + y^n + z^n** satisfy:

- **s_n = 3K(n+2) - 2e_1 K(n+1) + e_2 K(n)**

Rearranging gives an alternative recurrence for K driven by the power sums:

- **K(0) = 0**
- **K(1) = 0**
- **K(n+2) = (2/3)e_1 K(n+1) - (1/3)e_2 K(n) + (1/3)s_n**

Since the right-hand side at each step introduces exactly one new power sum s_n, iterating this recurrence shows that K(n+2) is always a linear combination of s_0, s_1, ..., s_n. We can therefore write:

- **K(n+2) = Σ_{m=0}^{n} W_m(n-m) s_m**

for some coefficients W_m(n). We are building W_m backwards, because that will be more convenient later.

---

## 13. Expressing K via Power Sums - Part 2

By substituting the expression for K into the recurrence from Section 12, we obtain (for each fixed m) the following recurrence relation for the coefficients W_m(j):

- **W_m(0) = 1/3**
- **W_m(1) = 2/9 e_1**
- **W_m(j+2) = (2/3)e_1 W_m(j+1) - (1/3)e_2 W_m(j)**

Remarkably, this recurrence is the same for every m including the initial conditions. Therefore, the shape of the recurrence is universal, and we may drop the subscript m and simply write W(j) to refer to the general sequence satisfying:

- **W(0) = 1/3**
- **W(1) = 2/9 e_1**
- **W(j+2) = (2/3)e_1 W(j+1) - (1/3)e_2 W(j)**

**Reindexing.** In the sum for **K(n+2)** from Section 12, each W_m depends only on the lag j = n-m, not on m itself. Relabelling gives the equivalent form:

- **K(n+2) = Σ_{m=0}^{n} W(m) s_{n-m}**

where now W(m) is the coefficient of s_{n-m}

---

## 14. Three New Sequences from the Convolution

The convolution formula for **K(n+2)** expresses K in terms of the ordinary power sums **s_n**. A natural question is whether the same approach applies when s_n is itself replaced by its universal representation **s_n = K(n) s_2 + L(n) s_1 + M(n) s_0**. Substituting this into the convolution gives:

- **K(n+2) = A(n) s_2 + B(n) s_1 + C(n) s_0**

where the three new sequences are defined as the convolutions of W against K, L, and M respectively:

- **A(n) = Σ_{m=0}^{n} W(m) K(n-m)**
- **B(n) = Σ_{m=0}^{n} W(m) L(n-m)**
- **C(n) = Σ_{m=0}^{n} W(m) M(n-m)**

This identity holds for all n ≥ 0. Their initial values are:

- **A(0)=0, A(1)=0**
- **B(0)=0, B(1)=W(0)**
- **C(0)=W(0), C(1)=W(1)**

The formulas below can be proven by mathematical induction:
- **3A(n+2) - 2e_1 A(n+1) + e_2 A(n) = K(n+2)**
- **3B(n+2) - 2e_1 B(n+1) + e_2 B(n) = L(n+2)**
- **3C(n+2) - 2e_1 C(n+1) + e_2 C(n) = M(n+2)**

---

## 15. Master Sequence A

It's not difficult to show that these identities hold:
- **B(n) = A(n+1) - e_1 A(n)**
- **C(n+1) = W(n+1) + e_3 A(n)**

When we substitute this into the formula from Section 14 then we get
- **A(n+2) = e_1 A(n+1) - e_2 A(n) + e_3 A(n-1) + W(n)**
- **B(n+2) = e_1 B(n+1) - e_2 B(n) + e_3 B(n-1) + W(n+1) - e_1 W(n)**
- **C(n+2) = e_1 C(n+1) - e_2 C(n) + e_3 C(n-1) - (1/3)e_1 W(n+1) + (2/3)e_2 W(n)**