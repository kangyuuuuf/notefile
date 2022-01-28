# MATH 416 Final

## Chapter 5

### 5.1 Singular Value Decomposition of Linear Maps

#### Define SVD

**Theorem 5.1**	(Singular Value decomposition (SVD)) Let $V$ and $W$ be finite-dimensional inner product spaces and let $T \in \mathcal{L}(V,W)$ have rank $r$. Then there exisit **orthonormal** bases $(e_1,\dots,e_n)$ of $V$ and $(f_1,\dots,f_m)$ of $W$ and numbers $\sigma_1 \geq\dots \geq \sigma_r>0$ such that $Te_j=\sigma_jf_j$ for $j=1,\dots,r$ and $Te_j=0$ for $j=r+1,\dots,n$.

**Lemma 5.2**	Let V and W be finite-dimensional inner product spaces, and let $T\in\mathcal{L}(V,W)$. Let $e\in V$ be a unit vector such that 
$$
\norm{T}_{op} = \norm{Te}.
$$
Then for any vector $u \in V$ with $\langle u,e\rangle = 0$, 
$$
\langle Tu,Te\rangle=0.
$$

#### Uniqueness of Singular Values

**Theorem 5.3**	Let $V$ and $W$ be finite-dimensional inner product spaces, and let $T\in \mathcal{L}(V,W)$ wiht $rank(T) = r$. Suppose there are orthonormal bases $(e_1\dots,e_n)$ and $(\tilde{e}_1,\dots,\tilde{e}_n)$ of $V$ and $(f_1,\dots,f_m)$ and $(\tilde{f}_1,\dots,\tilde{f}_n)$of $W$, and real scalas $\sigma_1\ge\dots\ge\sigma_r > 0$ and $\tilde{\sigma}_1 \ge\dots\ge \tilde{\sigma}_r >0$ such that
$$
Te_j = \left\{
\begin{array}{lr}
\sigma_jf_j & if\ 1\leq j\leq r, \\
0 & otherwise;
\end{array}\qquad
\right.
&T\tilde{e}_j = \left\{
\begin{array}{lr}
\tilde{\sigma}_j\tilde{f}_j & if\ 1\leq j\leq r, \\
0 & otherwises.
\end{array}
\right.
$$
Then $\sigma_j = \tilde{\sigma}_j$ for all $j\in {1,\dots,r}$.

**Definition**	Let $V$ and $W$ be finite-dimensional inner product spaces, and let $T\in \mathcal{L}(V, W)$. The **singular values** of $T$ are the numbers $\sigma_1 \ge \dots \ge \sigma_p\ge0$, where $p =  \min\{m,n\}$, $\sigma_1, \dots, \sigma_r$ are given in the statement of Theorem  5.1, and $\sigma_j$= 0 for $r+1 \leq j \leq p$.

### 5.2 Singular Value Decomposition of Matrices

#### Matrix Version of SVD

**Theorem 5.4**	Let $A\in M_{m,n}(\mathbb{F})$ have rank $r$. Then there exist matrices $U\in M_m\mathbb{F}$ and $V\in M_n(\mathbb{F})$ with $U$ and $V$ unitary or orthogonal and unique real numbers $\sigma_1\ge\dots\ge\sigma_r > 0$ such that
$$
A = U\Sigma V^*,
$$
where $\Sigma \in M_{m,n}(\mathbb{R})$ has $(j,j)$ entry $\sigma_j$ for $1\leq j \leq r$, and all other entries $0$.

Note: The **singular value** of $A$ are the entries $[\Sigma]_{jj}$. 

**Proposition 5.5**	Let $A\in M_{m,n}(\mathbb{F})$ Have singular values $\sigma_1 \ge ...\ge\sigma_p$, where $p =  \min\{m,n\}$. Then for each $j = 1,\dots, p$, $\sigma_j^2$ is an eigenvalue of $A^*A$ and of $AA^*$. Moreover, whichever of $AA^*$ and $A^*A$ is a $p \times p$ matrix has exactly $\sigma_1^2, \dots,\sigma_p^2$  as eigenvalues; if the other is large, it has eigenvalues $\sigma^2_1, \dots, \sigma_p^2$ together with zero. 

#### SVD and Geometry

Since $V$ is unitary, the transformation of $V^*x$ is acted as a reflection or rotation, the same as $U$. For the transformation of $\Sigma$, it stretches the standard basis vectors according to the singular values.

![image-20211206170318744](MATH 416.assets/image-20211206170318744.png)

**Proposition 5.6**	If $\sigma_1, \dots,\sigma_r$ are the positive singular values of $A \in M_{m,n}(\mathbb{C})$, then
$$
\norm{A}_F = \sqrt{\sum^r_{j=1}\sigma^2_j}.
$$

#### Low-rank Approximation

**Theorem 5.7**	Let $A \in M_{m,n}(\mathbb{F})$. Then there exist orthonormal bases $ (u_1,\dots, u_m)$ of  $\mathbb{F}^m$ and $(v_1,\dots,v_n)$ of $\mathbb{F}^n$ such that 
$$
A=\sum^r_{j=1}\sigma_ju_jv^*_j,
$$
where $\sigma_1 \ge \dots\ge \sigma_r >0$ are the non-zero singular values of $A$.

**Theorem 5.8** Let $A\in M_{m,n}(\mathbb{C})$ be fixed with positive singular values $\sigma_1 \ge \dots\ge \sigma_r>0$. Then for any $B \in M_{m,n} (\mathbb{C})$ with rank $k < r$,
$$
\norm{A-B}_{op} \ge \sigma_{k+1}, 
$$
and equality is achieved for 
$$
B=\sum^r_{j=1}\sigma_ju_jv^*_j,
$$
where the notation is as in the statement of Theorem 5.7.

**Theorem 5.9** Let $A\in M_{m,n}(\mathbb{C})$ be fixed with positive singular values $\sigma_1 \ge \dots\ge \sigma_r>0$. Then for any $B \in M_{m,n} (\mathbb{C})$ with rank $k < r$,
$$
\norm{A-B}_F \ge \sqrt{\sum_{j=k+1}^r\sigma^2_j}
$$
and equality is achieved for 
$$
B=\sum^r_{j=1}\sigma_ju_jv^*_j,
$$
where the notation is as in the statement of Theorem 5.7.

### 5.3 Adjoint Maps

#### The Adjoint of a Linear Map

Recall that if we do the standard dot product in $\mathbb{C}^n$ , we have the rules: $\langle x,y \rangle = y^*x$. If we  consider an $n \times n$ matrix $A$ as an operator on $\mathbb{C}^n$, then since $(By)^*=y^*B^*$, we have $\lang Ax,y\rang = y^* Ax = (A^*y)^*x= \lang x, A^*y\rang $. 

**Definition**	Let $V$ and $W$ be finite-dimensional inner product spaces, and let $T\in \mathcal{L}(V, W)$. A linear map $S\in \mathcal{L} (W,V)$ is called an adjoint of $T$ if $\lang Tv,w\rang = \lang v,Sw\rang$ for every $v\in V$ and $w \in W$. We then write $S = T^*$.

**Lemma 5.11**	Let $T \in \mathcal{L}(V,W)$ be a linear map between inner product spaces. If $T$ has an adjoint, then its adjoint is unique.

**Theorem 5.12**	 If $V$ is a finite-dimensional inner product space and W is any inner product space, then every $T\in \mathcal{L}(V,W)$ has an adjoint. 

**Theorem 5.13**	Suppose that $\mathcal{B}_v$ and  $\mathcal{B}_w$ are orthonormal bases of V and W, respectively. Then for $T\in \mathcal{L}(V,W)$, $[T^*]_{\mathcal{B}_v,\mathcal{B}_w} = [T]^*_{\mathcal{B}_v,\mathcal{B}_w} $.

Then, for the adjoint maps, we have the following rules:

1. $(T^*)^*=T$
2. $(S+T)^*=S^*+T^*$
3. $(aT)^* = \bar{a}T^*$
4. $(RT)^* = T^*R^*$
5. if $T$ is invertible, then $(T^{-1})^*=(T^*)^{-1}$

#### Self-adjoint Maps and Matrices

**Definition**	 A linear map $T\in \mathcal{L}(V)$ is self-adjoint if $T^*=T$. For field $\mathbb{C}$, a matrix is Hermitian if $A^*=A$; for field $\mathbb{R}$, a matrix is symmetric if $A^T=A$.



**Proposition 5.15**	Let  $T\in \mathcal{L}(V)$ be self-adjoint. If $Tv_1 = \lambda_1v_1$ and $Tv_2=\lambda_2v_2$, and $\lambda_1 \ne \lambda_2$, then $\lang v_1, v_2\rang = 0$.

![image-20211206170253060](MATH 416.assets/image-20211206170253060.png)

#### The Four Subspaces

**Proposition 5.16** 	Let $V$ and $W$ be finite-dimensional inner product spaces, and let $T\in \mathcal{L}(V, W)$. Then

1. $\ker T^* = (\text{range }T)^\perp$.
2. $\text{range } T^* = (\ker T)^\perp$.

#### Computing SVD

**Algorithm 5.17**	To find an SVD for the matrix $A\in M_{m,n}(\mathbb F)$:

- Find the eigenvalues of $AA^*$ or $A^*A$ \. The square root of the largest $p = \min\{m,n\}$ of them are the singular values $\sigma_1 \ge ...\ge\sigma_p$ of $A$.

- Find an orthonormal basis for each eigenspace of $AA^*$ or $A^*A$; put the resulting collection of vectors $(v_1,\dots,v_n)$ in a list so that the corresponding eigenvalues are in decreasing order. Take
  $$
  V:= \begin{bmatrix}
  \mid & & \mid\\
  v_1 & \dots &v_2 \\
  \mid & & \mid
  \end{bmatrix}.
  $$

- Let $r = \rank A$. For $1\leq j\leq r $, define $u_j :=\frac{1}{\sigma_j}Av_j$, and extend $(u_1,\dots,u_r)$ to an orthonormal basis $(u_1,\dots,u_m)$ of $\mathbb{F}^m$. Take

$$
U:= \begin{bmatrix}
\mid &&\mid\\
u_1 & \dots & u_m\\
\mid && \mid
\end{bmatrix}.
$$

Then if $\Sigma \in M_{m,n}$ has $\sigma_j$ in the $(j,j)$ position for $1\leq j \leq p$ and $0$ otherwise,
$$
A = U \Sigma V^{*}
$$
is an SVD of $A$.

### 5.4 The Spectral Theorems

**Lemma 5.18**	If $A\in M_n(\mathbb{F})$ is **Hermitian**, then $A$ has an eigenvector in $\mathbb F^n$.

​	If $V$ is a nonzero finite-dimensional inner product space and $T\in \mathcal L (V)$ is self-adjoint, then $T$ has an **eigenvector**.

**Theorem 5.19** (The Spectral Theorem for self-adjoint maps and Hermitian matrices) If $V$ is a finite-dimensional inner product space and $T\in \mathcal L(V)$ is self-adjoint, then there is an orthonormal basis of V consisting of eigenvectors of $T$.

​	If $A\in M_n(\mathbb F)$ is Hermitian or symmetrical then there exist a unitary or orthogonal matrix $U\in M_n(\mathbb F)$ and **real** numbers $\lambda_1, \dots,\lambda_n\in \mathbb R$ such that 
$$
A=U\text{diag}(\lambda_1, \dots,\lambda_n)U^*.
$$
**Theorem 5.20**	Let $A\in M_n(\mathbb C)$ be Hermitian. The following are equivalent:

1. Every eigenvalue of $A$ is positive.
2. For every $0 \ne x \in \mathbb C^n$, we have $\lang Ax,x\rang>0$.

**Definition**	A matrix satisfying the equivalent properties in Theorem 5.20 is called **positive definite**.

#### Normal Maps and Matrices

**Definition**	A matrix $A\in M_n(\mathbb C)$ is normal if $A^*A=AA^*$. A linear map $T\in \mathcal L (V)$ is normal if $T^*T=TT^*$.

**Lemma 5.21**	Let V be a complex inner product space. Given $T\in \mathcal L(V)$, define 
$$
T_r := \frac{1}{2}(T+T^*)\qquad \text{and} \qquad T_i:= \frac{1}{2i}(T-T^*)
$$
Then $T_r$ and $T_i$ are both self-adjoint, and $T$ is normal if and only if
$$
T_rT_i = T_iT_r
$$
**Lemma 5.22**	Suppose that $S,T \in \mathcal L(V)$ and that $ST=TS$. If $\lambda$ is an eigenvalue of $T$ and $v\in \text{Eig}_{\lambda}$, then $S_v \in \text{Eig}_{\lambda}$.

**Theorem 5.23** (The Spectral Theorem for normal maps and normal matrices) If $V$is a finite-dimensional inner product space over $\mathbb C$ and $T\in \mathcal L(V)$ is normal, then there is an orthonormal basis of V consisting of eigenvectors of $T$.

​	If $A\in M_n(\mathbb F)$ is normal, then there exists a unitary matrix $U\in M_n(\mathbb C)$ and **complex** numbers $\lambda_1, \dots,\lambda_n\in \mathbb C$ such that 
$$
A=U\text{diag}(\lambda_1, \dots,\lambda_n)U^*.
$$
**Corollary 5.24**	(The Schur decomposition) Suppose that V is a finite-dimensional complex inner product space, and $T\in \mathcal L(V) $. Then there is an orthonormal basis $\mathcal B$ of $V$ such that $[T]_\mathcal B$ is upper triangular.

​	Equivalently, if $A\in M_n(\mathbb C)$, then there exists a unitary matrix $U\in M_n(\mathbb C)$ and an upper triangular matrix $T\in M_n(\mathbb C)$ such that $A=UTU^*$.

## Chapter 6

### 6.1 Determinants

**Definition**	A function $f:M_n(\mathbb F)\rarr \mathbb F$ is called **isoscopic** if $f(A) = 0$ whenever $A$ has two identical columns.

#### Multilinear

$$
D\left( \begin{bmatrix}
\mid&&\mid&&\mid \\
a_1& \dots &a_j+b_j& \dots&a_n\\
\mid&&\mid&&\mid
\end{bmatrix}\right)= D\left( \begin{bmatrix}
\mid&&\mid&&\mid \\
a_1& \dots &a_j& \dots&a_n\\
\mid&&\mid&&\mid
\end{bmatrix}\right) = D\left( \begin{bmatrix}
\mid&&\mid&&\mid \\
a_1& \dots &b_j& \dots&a_n\\
\mid&&\mid&&\mid
\end{bmatrix}\right)
$$



and
$$
D\left( \begin{bmatrix}
\mid&&\mid&&\mid \\
a_1& \dots &ca_j& \dots&a_n\\
\mid&&\mid&&\mid
\end{bmatrix}\right) =cD\left( \begin{bmatrix}
\mid&&\mid&&\mid \\
a_1& \dots &a_j& \dots&a_n\\
\mid&&\mid&&\mid
\end{bmatrix}\right)
$$
That is, $D(A)$ is linear when the thought of as a function of one of the columns of A, with the other columns held fixed.

**Lemma 6.1**	Suppose $D:M_n(\mathbb F)\rarr\mathbb F$ is an isoscopic multilinear function. If $A\in M_n(\mathbb F)$ is singular, then $D(A) = 0$.

#### Alternating

A multilinear function $D:M_n(\mathbb F)\rarr\mathbb F$ is called alternating if 
$$
D\left( \begin{bmatrix}
\mid&&\mid \\
a_1& \dots&a_n\\
\mid&&\mid 
\end{bmatrix}\right) =0
$$
**Lemma 6.2**	Suppose $D:M_n(\mathbb F)\rarr\mathbb F$ is an alternating multilinear function. Given $A\in M_n(\mathbb F)$ And $1\leq i \leq j \leq n$, let $B\in M_n(\mathbb F)$ be the matrix obtained from $A$ by exchanging the ith and jth columns. Then $D(B) = -D(A)$.

**Theorem 6.3**	For each $n$, there is a unique alternating multilinear function $D:M_n(\mathbb F)\rarr \mathbb F$ such that $D(I_n)=1$.

​	This function is called the determinant; the determinant of a matrix $A$ os denoted $\det(A)$.

**Corollary 6.4**	If $D:M_n(\mathbb F) \rarr\mathbb F$ is an alternating multilinear function, then
$$
D(A)= D(I_n)\det A
$$
for evert $A\in M_n(\mathbb F)$.

**Theorem 6.5**	 If $A,B \in M_n(\mathbb F)$, then $\det(AB) = \det(A)\det(B)$.

**Corollary 6.6**	A matrix $A\in M_n(\mathbb F)$ is invertible $\iff \det(A) \ne0$. In that case, $\det(A^{-1})=\det(A)^{-1}$.

**Corollary 6.7**	If $A,B \in M_n(\mathbb F)$ are similar, then $\det A = \det B$.

**Lemma 6.8**	For each $n$, there exists a determinant function on $M_n(\mathbb F)$.

### 6.2 Computing Determinants

**Corollary 6.10**	If $A\in M_n(\mathbb F)$ is upper triangular, then $\det A= a_{11}\dots a_{nn} $

**Theorem 6.11**	If $A\in M_n(\mathbb F)$, then $\det A^T = \det A$.

**Corollary 6.13**	If $A\in M_n(\mathbb C)$, then $\det A^*=\overline{\det A}$.

#### Permutations

**Definition**	A **permutation** of $\{1,\dots,n\}$ is a bijective function $\sigma:\{1,\dots,n\}\rarr\{1,\dots,n\}$.

Equivalently, $(\sigma(1),\dots,\sigma(n))$ is a list of all the numbers in $\{1,\dots,n\}$ in some order. The set of all permutations of $\{1,\dots,n\}$ is denoted $S_n$ and is called the symmetric group on $n$ letters.

 