# CS 446 Machine Learning

## KNN

It is based on the assumption that **similar points have similar labels.** The overall algorithm cost $O(Nd)$ which is quit expensive.

#### Algorithm

1.  Store the training data $\mathcal D \{(x^{(i)}, y^{(i)}\}^N_{i=1}$ 

2.  For a test input $x$, calculate the distance to every training point 
    $$
    d(x^{(i)},x), \text{ for } i \in \{1, \dots, N\}
    $$

3.  Assign the most common label among its $k$ closest training inputs

#### Backwards

-   It might have a memory issue. 
-   It is sensitive to outliers and easily fooled by irrelevant attributes.
-   If $d$ is large, **curse of dimensionality** 

### Curse of Dimensionality

*Low-dimensional visualizations are misleading! High-dimensional spaces are empty, and “most" points are far apart*.

Assume we have the data lives in $[0,1]^d$, and all training data is sampled uniformly. 

Then, we have a small cube with $l$ length. Then, the probability for a data point inside this small cube will be $l^d$ (Volume of the cube divided by the space volume). Intuitively, length $l$ is a number from 0 to 1. With higher dimensions, larger $d$, $l^d$ will be smaller.

Empirically, the probability of sampling a point inside the small cube is roughly $\frac{k}{N}$. Thus, to estimate $l$, we have
$$
l ^d = \frac{k}{N}  \implies l \approx (\frac{k}{N})^\frac 1 d 
$$
Then, with different $l$, we have

<img src="CS%20446%20Machine%20Learning.assets/image-20230825224358144.png" alt="image-20230825224358144" style="zoom:50%;" />

With higher dimensions, $l$ is close to 1, which means the small box is almost equal to the space.

## Perceptron 

It is based on the assumption that

-   Binary classification: $y \in\set{-1, +1}$
-   Data is linearly separable

#### Notational Hack

If we add a 1 to the end of $x$, we can absorb the bias term $w_0$  into the weight vector. Intuitively, bias term will help use to shifting the decision boundary. Without it, the boundary will always pass through the origin $(0,0)$.

<img src="CS%20446%20Machine%20Learning.assets/image-20230826104450861.png" alt="image-20230826104450861" style="zoom:50%;" />

Observation, since $y^{(i)} \in\set{-1, +1}, y^{(i)}(w^T x^{(i)}) > 0 \iff x \text{ is classified correctly}$.

#### Algorithm 

![image-20230826105126413](CS%20446%20Machine%20Learning.assets/image-20230826105126413.png)

**Question:** How often can a perceptron misclassify a point $x$ repeatedly?

We assume the perceptron will do $k$ times. Then, for each steps, we will $w_{i+1} \leftarrow w_i +yx$. Thus, we get $w_{final} = w_0 + kyx$. When $y^{(i)}(w^T x^{(i)}) \le 0 $, we know it is misclassified. Thus, we have
$$
y(w_0+kyx)^T x\le 0 \\ \implies y(w_0^Tx) + k||x||^2 \le 0 \\ \implies k||x||^2 \le  -y(w_0^Tx) \\ \implies k \le  y(w_0^Tx)/||x||^2
$$
To find $k$.

#### Performance

Three assumption:

1.  Linear separable
2.  $w$ and data point is normalized.
3.  Margin of a hyperplane $γ$ is defined as $γ$ = min $|w^{∗⊤}x ^{(i)} |, ∀x ^{(i)} ∈ D$

If all of the above holds, the perceptron algorithm makes at most $1/γ^2$ updates.