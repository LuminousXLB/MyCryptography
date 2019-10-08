# Exercise 4.8

### Problem

Let $$F$$ be a pseudorandom function. Show that the following MAC for messages of length $$2n$$ is insecure: Gen outputs a uniform $$k \in \{0, 1\}^n$$. To authenticate a message $$m_1 || m_2$$ with $$|m_1| = |m_2| = n$$, compute the tag $$F_k(m_1) || F_k(F_k(m_2))$$.

### Solution

Query

* $$m^1=m^*_1||m^*_1$$, $$t^1= t^1_1||t^1_2 = F_k(m^*_1) || F_k(F_k(m^*_1)) $$
* $$m^2=m^*_2||m^*_2$$, $$t^2= t^2_1 || t^2_2 = F_k(m^*_2) || F_k(F_k(m^*_2)) $$

Hence for $$m^*=m^*_1||m^*_2$$, $$t^* = t^1_1||t^2_2$$

