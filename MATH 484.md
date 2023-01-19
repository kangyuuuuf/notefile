# MATH 484

#### Timeline

HW1: due 1/27

Exam1: on 2/8

Office Hours

MWF 3-3:50 in ATT 165

#### Unconstrained Optimization Minimize $f(x)$

##### Calculus Review

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