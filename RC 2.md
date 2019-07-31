# RC 2



#### 1. Memoryless property

##### Geometric Distribution

For ${x \sim \operatorname{Geom}(p)}$ with probability function ${f_{X}(x)=(1-p)^{x-1} p} $.
$$
{P(X=a+b | X \geq b)=P(X=a)}
$$

##### Exponential Distribution

The cumulative density function for exponential distribution is $F(T \leq t) = 1-e^{-\lambda t}$, $t \geq 0$.
$$
P[X>x+s | X>x]=P[X>s]
$$


#### 2. Decay rate vs. rate of arrival

- Expectation of Poisson distribution $p(x)=\frac{(\lambda t)^{x}}{x !} e^{-\lambda t}, \quad x \in \mathbb{N}$:
  $$
  E[X]= \lambda
  $$
  

- Expectation of Exponential distribution $f_\lambda(x) = \lambda e^{-\lambda x}, \quad x>0$:
  $$
  \mathrm{E}[X] = \frac{1}{\lambda}
  $$

> **Think of the fixed conditions and focused variables**:
>
> - what is Poisson distribution foces on?
> - what is Exponential distribution focues on?
> - why are the expectations inverse of each other?



#### 3. Independent exponential distributions

##### The scary Gamma distribution

In class we have seen the gamma distribution with parameters $\alpha, \beta$ to be
$$
f_{\alpha, \beta}(x)=\left\{\begin{array}{ll}{\frac{1}{\Gamma(\alpha) \beta^{\alpha}} x^{\alpha-1} e^{-x / \beta},} & {x>0} \\ {0,} & {x \leq 0}\end{array}\right.
$$
which is quite unfriendly. Now we try to view it another way.

Suppose $n = \alpha\in N^*$, and let $\lambda = 1/\beta$. 
$$
f(x) = \frac{1}{\Gamma(\alpha) \beta^{\alpha}} x^{\alpha-1} e^{-x / \beta} = \frac{\lambda^n x^{n-1}e^{-\lambda x }}{(n-1)!} = \frac{~~~(\lambda x)^{n-1}}{(n-1)!}\lambda e^{-\lambda x }
$$
We know that for Poisson distribution,
$$
p(x)=\frac{~~(\lambda t)^{x}}{x !} e^{-\lambda t}
$$
A gamma variable can be viewed as the last arrival time of a sum of $n$ identical indepenent exponential variable.

####4. Two independent exponential distributions

##### Exponential races

Let $T_1$, . . . , $T_n$ be independent, $T_{i}=\exp\left(\lambda_{i}\right)$, then $S=\exp\left(\lambda_{1}+\cdots+\lambda_{n}\right)$ and
$$
P\left(T_{i}=\min \left(T_{1}, \ldots, T_{n}\right)\right)=\frac{\lambda_{i}}{\lambda_{1}+\cdots+\lambda_{n}}
$$

##### Exercise

Alice and Betty enter a beauty parlor simultaneously, Alice to get a manicure and Betty to get a haircut. Suppose the time for a manicure (haircut) is exponentially distributed with mean 20 (30) minutes.
(a) What is the probability Alice gets done first?
(b) What is the expected amount of time until Alice and Betty are both done?

> ###### Solution:
>
> (a) We want to compute $P(T_A < T_B)$. This is possible by integrating the joint PDF of $T_A$ and $T_B$. 
> $$
> P\left(T_{A}<T_{B}\right)=\frac{1 / 20}{(1 / 20)+(1 / 30)}=\frac{30}{30+20}=\frac{3}{5}
> $$
> (b) We want to find $E\left[\max \left\{T_{A}, T_{B}\right\}\right]$, where  $\max \left\{T_{A}, T_{B}\right\}$: *time until both Alice and Betty are done*. 
> We start by finding the CDF of T:
> $$
> \begin{aligned} P(T \leq t) &=P\left(T_{A} \leq t, T_{B} \leq t\right) \\ &=P\left(T_{A} \leq t\right) P\left(T_{B} \leq t\right) \\ &=\left(1-e^{-\lambda_{A} t}\right)\left(1-e^{-\lambda_{B} t}\right) \\ &=1-e^{-\lambda_{A} t}-e^{-\lambda_{B} t}+e^{-\left(\lambda_{A}+\lambda_{B}\right) t} \end{aligned}
> $$
> Thus, taking the derivative we can get 
> $$
> f_{T}(t)=\left\{\begin{array}{ll}{\lambda_{A} e^{-\lambda_{A} t}+\lambda_{B} e^{-\lambda_{B} t}-\left(\lambda_{A}+\lambda_{B}\right) e^{-\left(\lambda_{A}+\lambda_{B}\right) t}} & {\text { if } t \geq 0} \\ {0} & {\text { otherwise }}\end{array}\right.
> $$
> with which we can calculated $E[T]$,
> $$
> \begin{aligned} E[T] &=\int_{0}^{\infty} t f_{T}(t) d t \\ &=\int_{0}^{\infty} t \lambda_{A} e^{-\lambda_{A} t} d t+\int_{0}^{\infty} t \lambda_{B} e^{-\lambda_{B} t} d t-\int_{0}^{\infty} t\left(\lambda_{A}+\lambda_{B}\right) e^{-\left(\lambda_{A}+\lambda_{B}\right) t} d t \\ &=\frac{1}{\lambda_{A}}+\frac{1}{\lambda_{B}}-\frac{1}{\lambda_{A}+\lambda_{B}} \end{aligned}
> $$

