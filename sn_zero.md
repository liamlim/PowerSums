Throughout this document, let x, y, z be non-zero integers such that
- **gcd(x,y) = 1**
- **gcd(y,z) = 1**
- **gcd(z,x) = 1**

---

## Modulo s_n

All equalities in this section are understood **modulo s_n**.

### Basic relations for t_n modulo s_n:**

This follows immediately from definition of t_n and f_n using s_n = 0:
- **t_n = f_n(y^n,0,-z^n)**
- **t_n = f_n(-x^n,z^n,0)**
- **t_n = f_n(0,-y^n,x^n)**

### Main relation for t_n modulo s_n:

Apply the universal linear representation **f_k = K(k) f_2 + L(k) f_1 + M(k) f_0** to each of the three basic relations above and add them together:

- **3t_n = K(n) f_n(z^2-x^2, x^2-y^2, y^2-z^2) + L(n) f_n(z-x,x-y,y-z)**
