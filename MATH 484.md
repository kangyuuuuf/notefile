# MATH 484

#### Timeline

HW1: due 1/27

Exam1: on 2/8

Office Hours

MWF 3-3:50 in ATT 165

### Unconstrained Optimization Minimize $f(x)$

#### Calculus Review

A point $x^*$ is a global minimizer of $f(x)$ if $f(x^*) \le f(x)$ for all $x \in \mathbb R$

A point $x^*$ is a local minimizer of $f(x)$ if $\exist r$ so $f(x^*) \le f(x)$ whenever $|x-x^*| < r$

A minimizer is strict if the inequality is strict $f(x^*) < f(x)$ or all $x \in \mathbb R$ or whenever $|x-x^*| < r$

##### Notation

$^*$ to denote optimal points

**Theorem 1.1**  	Suppose $f: I \rightarrow R$ is differentiable on $I$ and $x^* \in I$ is a local min, then either $x^*$ is an endpoint of $I$ or $f'(x^*) = 0$. $x^*$ is called a critical point if $f'(x^*)=0$

**Theorem 1.2**	Suppose $f: I \rightarrow \mathbb R$ has a cont second derivative and $x^*$ is a critical point, 

-   (a) if $f''(x) \ge 0 \quad \forall x \in I$ then $x^*$ is a global min, 
-   (b) if $f''(x) > 0 \quad \forall x \in I-x^*$ then $x^*$ is a strict global min, 
-   (c) if $f''(x^*) > 0$ then $x^*$ is a strict local min

**Taylor’s Theorem**	If $f''$ is continuous on $I$ and $x,x^* \in I$ then $f(x) = f(x^*) + f'(x^*)(x-x^*) + \frac{1}{2} f''(z)(x-x^*)^2$ for some $z $ between $x$ and $x^*$

Taylor’s Theorem could prove **Theorem 1.2**

### Geometry of $\mathbb R^n$

$\mathbb R ^n=$ column vector

Vectors - arrows with magnitude + direction

Multiplication: $row \times column \rightarrow \mathbb R$

Dot Production: $x \cdot y = x^T y = x_1y_1+x_2y_2+ \dots +x_ny_n $

Define the length, **norm**: $||x|| = \sqrt{x\cdot x} $

Distance: between $x$, $y$ is $||x-y||$

#### Properties

##### Dot product

-    Linearity: $(ax+by)\cdot z = a(x\cdot z)+b(y \cdot z)$
-   symmetry: $x+y = y+x$
-   positivity: $x \cdot x \ge 0$ and only $= 0$ if $x =0$

##### Norms

-   Linearity: $||ax|| = |a |||x||$ for every $a \in \mathbb R$ and $x \in \mathbb R^n$
-   Positivity: $||x|| \ge 0$ and only $= 0$ if $x =0$
-   Triangle Inequality: $||x||+||y|| \ge ||x+y||$

Taxicab/one norm: $||x||_1 = |x_1|+|x_2|+ \dots+|x_n|$

Inf norm: $||x||_\infin = max(|x_1|,|x_2|, \dots,|x_n|)$

P-norm: $||x||_p = \sqrt[p]{\sum|x|^p}$

#### Cauchy-Schwartz Inequality

$$
|x\cdot y| \le||x||\cdot||y||
$$

Define angles by
$$
cos(\theta_{xy}) = \frac{x\cdot y}{||x||||y||}
$$

#### Matrices

A matrix is $n\times m$ array, add & scalar multiply like vectors.

##### Matrix Multiplication

$A: k \times n$ and $B:n \times m \implies AB: k\times m$

$(AB)_{ij} = \sum_{k=1}^na_{ik}b_{kj}$

Usually, it will take $n^3$ times. However, by the Strasser algorithm, it will take about $ n^{2.71}$

#### Eigenvalue/vector

For a $A : n\times n,\mathbb R^n \rightarrow \mathbb R^n$, $x$ is the eigenvector with the eigenvalue of $\lambda$ if $Ax = \lambda x$

This means that $Ax = \lambda x \implies (A-\lambda I) x = 0 \implies det(A-\lambda I) = 0$

**Theorem 2.1**	If $n\times n$ $A$ has $n$ independent eigenvectors $x_1, \dots,x_n$, and eigenvalues $\lambda_1, \dots, \lambda_n$, then $A  = PDP^{-1}$

### Critical Points in $\mathbb R$

The restriction of $f$ to the line through $x$ in the direction of $u$ us the function
$$
\phi_u = f(x+tu)
$$
**Definition 3.1.1**	A point $x^*\in \mathbb R^n$ is a global minimizer of $f:\mathbb R^n \rightarrow \mathbb R$ if  $f(x^*) \le f(x)$ for all $x \in \mathbb R^n$.

**Lemma 3.1.2**	A point $x^*\in \mathbb R^n$ is a global minimizer of $f:\mathbb R^n \rightarrow \mathbb R$ if and only if for every direction $u\in \mathbb R^n, t =0$ is a global minimizer of $\phi_u = f(x^*+tu)$

Also, just mention the **chain rule**:
$$
\frac{d}{dt}f(g(t)) =  \sum_{i=1}^n \frac{\partial f}{\partial x_i}\frac{d}{dt}g_i(t)
$$
Also, the gradient $\bigtriangledown f (x)$,
$$
\bigtriangledown f (x)^T = [\frac{\partial f}{\partial x_1}(x) \quad\frac{\partial f}{\partial x_2}(x) \quad \cdots  \quad\frac{\partial f}{\partial x_n}(x)]
$$
Then, we have
$$
\phi'_u(t) =\bigtriangledown f (x+tu)\cdot u
$$
**Theorem 3.2.1**	Given a function $f:\mathbb R^n \rightarrow \mathbb R$ if $\bigtriangledown f $ is continuous and $x^*$ is a global minimizer of $f$, then $\bigtriangledown f(x^*) = 0$.

**Definition 3.2.2**	A point $x^* \in \mathbb R^n$ with $\bigtriangledown f(x^*) = 0$ is called a **critical point** of $f$.

**Definition 3.2.3**	The quantity $\phi' _u = \bigtriangledown f(x^*)\cdot u$ as a function of $u$ is known as the directional derivative of $f$.

**Definition 3.3.1**	The Hessian matrix of $f$ is the matrix
$$
H_f(x) =\begin{bmatrix}
\frac{\partial^2 f}{\partial x_1^2} & \dots& \frac{\partial^2 f}{\partial x_1 \part x_n}\\
\vdots & \ddots &\vdots \\
\frac{\partial^2 f}{\part x_n\partial x_1} &\dots & \frac{\partial^2 f}{\partial x_n^2}
\end{bmatrix}.
$$
**Theorem 3.3.2**	 Let $f:\mathbb R^n \rightarrow \mathbb R$ have continuous $Hf$. Suppose that $\bigtriangledown f(x^*) = 0$, and for any $x,u \in \mathbb R^n$,
$$
u^T Hf(x) u \ge 0.
$$
Then, $x^*$ is a global minimizer of $f$.

**Definition 3.4.1**	A point $x^*$ is a local minimizer of $f(x)$ if there is some radius$r > 0$ so $f(x^*) \le f(x)$ whenever $|x-x^*| < r$.

**Theorem 3.4.2**	Suppose $f: D \rightarrow \mathbb R $ has continuous $\bigtriangledown f$ and $x^*$ is not on the boundary of $D$, If $x^*$ is a local minimizer of $f$, then $x^*$ is a critical point of $f$.

**Theorem 3.4.3**	Suppose $f: D \rightarrow \mathbb R $ has continuous $HF$ and $x^*$ is a critical point of $f$. Uf we can pick an $r>0$ such that whenever $||x-x^*|| < r$, Hf(x)has the property
$$
u^T Hf(x) u \ge 0 \qquad \text{for all } u \in \mathbb R ^n,
$$
then $x^*$ is a local minimizer of $f$.

### Positive Definite Matrices

**Definition 4.1**	A symmetric $n \times n$ matrix $A$ is 

-   Positive definite if $x^TAx >0$ for all $x\ne0$
-   Positive semidefinite if $x^TAx \ge0$ for all $x\ne0$
-   Negative definite if $x^TAx <0$ for all $x\ne0$
-   Negative semidefinite if $x^TAx \le0$ for all $x\ne0$
-   Indefinite if NOTA

**Definition 4.2**	The expression $x^TAx$ is a function of $x$ called the quadratic form associated to $A$.
$$
x^TAx = \sum^n_{i=1}\sum^n_{i=1}a_{ij}x_i x_j
$$

### Better Condition on $A\succ 0 $

$n \times n$ symmetric A

Define $A^{k}$
