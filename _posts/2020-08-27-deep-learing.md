---
published: true
---
## Forward propagation & Backward propagation for layer l

### Forward
Input: $$a^{[l-1]}$$

Output: $$a^{[l]}$$, cache$$(z^{[l]})$$

$$z^{[l]} = \omega^{[l]} a^{[l-1]} + b^{[l]}$$

$$a^{[l]} = g^{[l]} \left(z^{[l]} \right)$$

#### Vectorized version
$$z^{[l]} = \omega^{[l]} A^{[l-1]} + b^{[l]}$$

$$A^{[l]} = g^{[l]} \left(z^{[l]} \right)$$

### Backward
Input: $$da^{[l]}$$

Output: $$da^{[l-1]}$$, $$dW^{[l]})$$, $$db^{[l]})$$

$$dz^{[l]} = da{[l]} * g^{[l]'}(z^{[l]})$$

$$d\omega^{[l]} = dz^{[l]}a^{[l-1].T}$$

$$db^{[l]} = dz^{[l]}$$

$$da^{[l-1]} = \omega^{[l].T}dz^{[l]}$$

#### Vectorized version
$$dz^{[l]} = dA{[l]} * g^{[l]'}(z^{[l]})$$

$$d\omega^{[l]} = \frac{1}{m}dz^{[l]}A^{[l-1].T}$$

$$db^{[l]} = \frac{1}{m} np.sum(dz^{[l]}, axis = 1, keepdims = True)$$

$$dA^{[l-1]} = \omega^{[l].T}dz^{[l]}$$

### Process
![an image alt text]({{ site.baseurl }}/images/DL1.png "an image title")

