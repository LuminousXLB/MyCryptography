# Exercise 4.14

### Problem

Prove that the following modifications of basic CBC-MAC do not yield a secure MAC \(even for fixed-length messages\):

1. Mac outputs all blocks $$t_1, \ldots , t_l$$rather than just $$t_l$$. \(Verification only checks whether $$t_l$$ is correct.\)
2. A random initial block is used each time a message is authenticated. That is, choose uniform $$t \in \{0, 1\}^n$$, run basic CBC-MAC over the “message” $$t_0,m_1, \ldots ,m_l$$, and output the tag $$ \langle t_0, t_l \rangle$$. Verification is done in the natural way.

### Solution

#### Part 1

Query

* $$m^1 = B_0 || B_1$$, $$t^1 = t_0 || t_1$$
* $$m^2 = B_2 || B_3$$, $$t^2 = t_2||t_3$$

We know $$F_k(B_0) = t_0$$ and $$F_k(B_2) = t_2$$. Hence 

$$
MAC_k(B_0 || B^*_2) = F_k(B_0) || F_k(F_k(B_0) \oplus B^*_2) = t_0 || F_k(t_0 \oplus B^*_2)
$$

Let $$t_0 \oplus B^*_2 = B_2$$, i.e., $$B^*_2 = t_0 \oplus B_2$$. Then

$$
MAC_k(B_0 || t_0 \oplus B_2) = t_0 || F_k(t_0 \oplus t_0 \oplus B_2) = t_0 || F_k(B_2) = t_0 || t_2
$$

Therefore, $$\langle B_0 || t_0 \oplus B_2, t_0 || t_2 \rangle$$ is a valid pair of message and tag.

#### Part 2

Query

* $$m^1 = B_0 || B_1$$, $$t^1 = \langle r_1, t_1 \rangle$$
* $$ m^2 = B_2 || B_3 $$, $$ t^2 = \langle r_2, t_2 \rangle $$

Hence for $$m^* = B_0 || B_1 || t_2 \oplus r_2 || B_2 || B_3 $$, $$ t^* = \langle r, t_2 \rangle$$ should be a valid tag.





