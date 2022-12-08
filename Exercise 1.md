# Stochastic Optimization Project

Kangyu Feng

Fall 2022

#### Exercise 1

For $E[g(\theta)]$:
$$
E[g(\theta)] = E[Q(\theta,i)] = \frac{1}k\sum_{i=1}^k Q(\theta,i) = f(\theta)
$$
Then, since $g(\theta) = f(\theta)+z$, we have
$$
E[g(\theta)] = E[f(\theta)]+E[z] \implies f(\theta) = f(\theta) +z \implies z =0
$$
This is because an expected value of a constant is itself.

For $E[\triangledown g(\theta)]$:
$$
E[\triangledown g(\theta)] = \frac 1 k\sum_{i=1}^k \triangledown Q(\theta,i) = \triangledown f(\theta)
$$

#### Exercise 2

|                                       | SGD                    | GD                         |
| ------------------------------------- | ---------------------- | -------------------------- |
| Computational Cost per Update         | $O(1)$                 | $O(k)$                     |
| Number of updates to reach $\epsilon$ | $O(\frac 1 \epsilon )$ | $O(\ln \frac 1 \epsilon)$  |
| Total Cost                            | $O(\frac 1 \epsilon )$ | $O(k\ln \frac 1 \epsilon)$ |

$\triangledown f(\theta^*) = 0$ means that $\triangledown f$ has a unique root $\theta^*$. And we also have the condition that “f is strongly convex and is twice continuously differentiable” and “we use the ηt = $\frac 1t $ learning rate sequence.” Then, we could use **Theorem 1.1** to show that stochastic gradient descent requires $t= O(\frac 1 \epsilon)$ updates.

$\triangledown f(\theta^*) = 0$ means that $\triangledown f$ has a unique root $\theta^*$. And “We want to achieve a training precision of $\epsilon = |E[f(\theta_t)]- f(\theta^*)|$.” Then, we could use **Theorem 1.3** to show that gradient descent requires $t= O(\ln \frac 1 \epsilon)$ updates.

#### Exercise 3

(1)

|                                   | SGD                | GD                                            |
| --------------------------------- | ------------------ | --------------------------------------------- |
| Computational Cost per Update     | $O(1)$             | $O(\rho^{-\frac{1}{\gamma}})$                 |
| Number of updates to reach $\rho$ | $O(\frac 1 \rho )$ | $O(\ln \frac 1 \rho)$                         |
| Total Cost                        | $O(\frac 1 \rho )$ | $O(\rho^{-\frac{1}{\gamma}}\ln \frac 1 \rho)$ |

We have $\rho = c k^{-\gamma}$ for some constant $c$.
$$
\rho = c k^{-\gamma} \implies \ln (\frac \rho c) = - \gamma  \ln (k) \implies  k =\frac \rho c ^{- \frac 1\gamma} \implies  k = O(\rho ^{- \frac 1\gamma} )
$$
Since we know the $k$, we know that GD’s Computational Cost per Update is $O(\rho^{-\frac{1}{\gamma}})$.

Since we assume $\epsilon = \Theta(\rho)$m we get  $O(\frac 1 \rho )$ for SGD in the number of updates to reach $\rho$.

It is similar Similar to  get $O(\ln \frac 1 \rho)$ for GD in the number of updates to reach $\rho$ since $\epsilon = \Theta(\rho)$

Finally, the total cost will just be the Computational Cost per Update $\times$ Number of updates to reach $\rho$.

(2)

Since we have $\gamma = 0.2$ and $\rho  = O(k^{-\gamma})$, we get $\rho$ is less than 1. It means that GD’s Computational Cost per Update will be extremely large, which will be $(\frac 1 \rho)^5$. Then, just for the update od GD, the cost is already bigger than the cost of SGD. 

#### Exercise 4

(1) We have the formular $\theta = (x^Tx)^{-1}x^Ty$. Using this formualr, we couold get the theta predicted:

Empirical theta [0.99667444 1.00389401 0.99647909 1.00978171 0.98300854 1.0051994 1.00241769 0.99180672 0.99768231 0.99393583]

And we get the error using predicted value - true value:

[-0.00332556  0.00389401 -0.00352091  0.00978171 -0.01699146  0.0051994  0.00241769 -0.00819328 -0.00231769 -0.00606417]

It is very close to the true value.

(2) In this question, we use the chain rule to solve the gradient. We define $e(\theta) = x^T_j \theta -y_j$. Then, we have 
$$
\triangledown Q(\theta,j) = \frac{\part(|e(\theta)|^\gamma)}{\part e}\cdot \triangledown e(\theta)= sign(e(\theta))\gamma |e(\theta)|^{\gamma-1}\cdot x_j
$$
(3) For the 1000 update, we find that the green line, which is ADAMGRAD do not have many loss. The blue line, which is ADAM, have nearly 1.5 more loss than adagrad. And, the yellor line, which is SGD, has even more loss then ADAM.

![img](Exercise%201.assets/908E749E-9E48-49BE-AD78-430482FE802C.png)

$\theta$ for ADAM

 [0.34175046 0.37502261 0.26473905 0.32415393 0.25413393 0.39152685 0.35685647 0.27265072 0.30548176 0.28804087]

$\theta$ for SGD

 [0.55794183 0.55111476 0.47684872 0.47362559 0.51812203 0.52356749 0.52953713 0.47676203 0.53631862 0.41088533]

$\theta$ for ADAGARD

[0.06519517 0.10927923 0.01789181 0.02800964 0.03333027 0.09712481 0.11802857 0.0223396  0.07027341 0.0439528 ]

(4) The result remains unchange after we adjust the “test_exp_interval”

![img](Exercise%201.assets/12D431A6-5099-4C2E-885F-74ED204BFE94.png)

(5) $\gamma = 0.4$:

We could find the test loss is not stable. But we still could find that SGD outperforms ADAM.

![img](Exercise%201.assets/1E2906F1-E1A6-4664-9C21-62EE0B1E2494.png)



$\gamma = 0.7$:

We could find the clear difference of slope of test loss starting updates 0. And we could find that SGD outperforms ADAM.

![img](Exercise%201.assets/24E37901-CFC5-443D-AB20-29558B4C24DE.png)

$\gamma = 1$:

Similarly, We could find the clear difference of slope of test loss starting updates 0. And we could find that SGD outperforms ADAM.

![img](Exercise%201.assets/A970F214-7986-4D6C-86EC-CCF9F88496A7.png)

$\gamma = 2$:

However, we the $\gamma$ become 2, the relationship of ADAM and SGD start to switch. As the plot shown, the ADAM has the better performance.

![img](Exercise%201.assets/9E91E4DD-5585-4150-9813-6F0808C33EEF.png)

$\gamma = 3$:

We could find that ADAM outperforms SGD. But the test loss is nolanger a linear relationship anymore. The SGD become a curve instead of a line. It means that SGD loss all of it information dramaticly with the updates increase.

![img](Exercise%201.assets/6873D089-53E5-4699-8EE8-E56D9651836F.png)

$\gamma = 5$:

Finally, the SDG’s test lose quickly, deducing to 0. And the ADAM still remain its change shape. We could find that ADAM outperforms SGD

![img](Exercise%201.assets/91CD62FB-7DC6-418C-8514-A12086E40B3E.png)

We find that if $\gamma$ is greater than 1, the ADAM is out performs SGD while if it is less than 1, SGD shows a better performance.

#### Exercise 5

(1)This is the same as the GD algorithm if we are using SGD optimizer because the code logic of SGD and GD algorithm is basiclly the same. And SGD is a fast algorithm that does not run all the data.

The outcome we get is 

Number Of Images Tested = 10000 Model Accuracy = 0.072

Predicted Digit = 3

<img src="Exercise%201.assets/F6A06002-3B5D-4D65-95C9-6B64861088D9.png" alt="img" style="zoom:50%;" />

To improve the accuracy, we could modiy the learning rate. Change the learning rate could help us to increase the accuracy. Also, we could increase the number of epochs, the more times we train, the better outcome we have.

(2) The outcome we get is

Number Of Images Tested = 10000

Model Accuracy = 0.924

The model accuracy has dramaticly increased and the training loass remains at 0.3. We could conclude that change the mini batch size will also help us to improve the accuracy.

(3)The outcome we get is

Number Of Images Tested = 10000

Model Accuracy = 0.9021

It is because Adam could tackle noise better than SGD. It is very useful in the training that has noice such as writing number picture.