# Exercise 5.3

### Problem

Let \(Gen, $$H$$\) be a collision-resistant hash function. Is \(Gen, $$\hat H$$\) defined by$$\hat H ^s (x) \overset{def}{=} H^s(H^s(x))$$necessarily collision resistant?

### Solution

Assuming that $$\hat H$$ is not collision-resistent, i.e. 

$$
\exists x\neq y, \hat H^s(x) = \hat H^s(y)
$$

Thus $$H^s(H^s(x)) = H^s(H^s(y)) $$

* If $$ H^s(x) = H^s(y)$$, $$(x,y)$$ is a pair of collision for $$H$$
* If $$ H^s(x) \neq H^s(y)$$, let $$x'=H^s(x)$$, $$y'=H^s(y)$$. 
  * $$H^s(H^s(x)) = H^s(H^s(y)) $$, $$(x',y')$$ is a pair of collision for $$H$$

Therefore, $$\hat H$$ is not collision-resistent implies $$H$$ is not collision-resistent. Then $$H$$ is collision-resistent implies $$\hat H$$ is collision-resistent.





