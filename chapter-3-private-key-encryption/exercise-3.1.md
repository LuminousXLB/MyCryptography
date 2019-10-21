# Exercise 3.1

### Problem

Prove Proposition 3.6.

> **PROPOSITION 3.6** Let $$negl_1$$ and $$negl_2$$ be negligible functions. Then, 
>
> 1. The function $$negl_3$$ defined by $$negl_3(n) = negl_1(n)+negl_2(n)$$ is negligible. 
> 2. For any positive polynomial $$p$$, the function $$negl_4$$ defined by $$negl_4(n) = p(n) · negl_1(n)$$ is negligible.

### Solution

#### Part 1

Since $$negl_1$$ is a negligible function, for any positive polynomial $$p$$, there exists an $$N_1$$ such that 

$$
\forall n > N_1, negl_1(n) < \frac{1}{p(n)}
$$

Similarly, there exists an $$N_2$$ such that

$$
\forall n > N_2, negl_2(n) < \frac{1}{p(n)}
$$

Thus for any positive polynomial $$p$$, there exists $$N > \max(N_1, N_2)$$ such that 

$$
\forall n > N, negl_1(n) < \frac{1}{2p(n)}, negl_2(n) < \frac{1}{2p(n)}
$$

Hence, 

$$
\forall n>N, negl_3(n) = negl_1(n)+negl_2(n) < \frac{2}{2p(n)} = \frac{1}{p(n)}
$$

Therefore $$negl_3$$ is also negligible.

#### Part 2

Assuming that $$negl_4$$ is not negligible. That is, exists a integer $$c > 0$$ such that 

$$
\forall n > 0, negl_4(n) = p(n)\cdot negl_1(n) \geq \frac{1}{n^c} \Rightarrow negl_1(n) \geq \frac{1}{p(n)\cdot n^c}
$$

Since $$p$$ is a polynomial, $$p'(n) = p(n)\cdot n^c$$ is also polynomial. That is there exists a positive polynomial $$p'(n)$$ such that 

$$
\forall n > 0, negl_1(n) \geq \frac{1}{p'(n)}
$$

Which is converse to $$negl_1$$ is negligible.

Therefore $$negl_4$$ is negligible.



