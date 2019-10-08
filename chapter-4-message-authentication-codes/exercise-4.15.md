# Exercise 4.15

### Problem

Show that appending the message length to the end of the message before applying basic CBC-MAC does not result in a secure MAC for arbitrary-length messages.

### Solution

Query

* $$m_1 = B_0 || B_1$$, $$t_1 = MAC_k(m_1 || \langle |m_1| \rangle)$$
* $$m^*_1 = B^*_0 || B^*_1$$,  $$t^*_1 = MAC_k(m^*_1 || \langle |m^*_1| \rangle)$$
  * $$ |m^*_1| = |m_1|$$
* $$m_2 = m_1 || \langle |m_1| \rangle || B_2 || B_3$$, $$t_2 = MAC(m_2 || \langle |m_2| \rangle)$$

To be specific, the process of computing $$t_2$$ for message $$m_2$$ is listed below:

* $$c_0=F_k(B_0)$$
* $$c_1=F_k(c_0 \oplus B_1)$$
* $$ t_1=F_k(c_1 \oplus \langle |m_1| \rangle) $$
* $$ c_3=F_k(t_1 \oplus B_2) $$
* $$ c_4=F_k(c_3 \oplus B_3) $$
* $$ t=F_k(c_4 \oplus \langle | m_2 | \rangle) $$

Hence, if we change $$m_1$$ to $$ m^*_1 $$,

* $$c^*_0=F_k(B^*_0)$$
* $$c^*_1=F_k(c^*_0 \oplus B^*_1)$$
* $$ t^*_1=F_k(c^*_1 \oplus \langle |m^*_1| \rangle) $$

In order to keep the result of MAC, it must hold that $$ t_1 \oplus B_2 = t_1^* \oplus B^*_2$$. Thus

$$
B^*_2 = t_1 \oplus B_2 \oplus  t_1^*
$$

Therefore

* $$ c^*_3=F_k(t^*_1 \oplus B^*_2) = F_k(t^*_1 \oplus  t_1 \oplus B_2 \oplus  t_1^*) = F_k(t_1 \oplus B_2) = c_3$$
* $$ c^*_4 = F_k(c^*_3 \oplus B_3) = F_k(c_3 \oplus B_3) = c_4$$
* $$ t^* = F_k(c^*_4 \oplus \langle | m^*_2 | \rangle)  = F_k(c_4 \oplus \langle | m_2 | \rangle) =t$$
  * $$ |m^*_2|=|m_2|$$ can be easily get since $$ |m^*_1| = |m_1| $$

Hence we get a message and its valid tag $$\langle m^*, t^* \rangle $$ where

$$
m^* := m^*_1 || \langle | m^*_1| \rangle || t_1 \oplus B_2 \oplus  t_1^* || B_3 \\
t^* = t
$$

