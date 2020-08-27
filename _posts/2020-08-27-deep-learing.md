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

$$d\omega^{[l]} = dz^{[l]}a^{[l-1]^T}$$

$$db^{[l]} = dz^{[l]}$$

$$da^{[l-1]} = \omega^{[l]^T}dz^{[l]}$$

#### Vectorized version
$$dz^{[l]} = dA{[l]} * g^{[l]'}(z^{[l]})$$

$$d\omega^{[l]} = \frac{1}{m}dz^{[l]}A^{[l-1]^T}$$

$$db^{[l]} = \frac{1}{m} np.sum(dz^{[l]}, axis = 1, keepdims = True)$$

$$dA^{[l-1]} = \omega^{[l]^T}dz^{[l]}$$

### A simple example
![an image alt text]({{ site.baseurl }}/images/DL1.png "an image title")

----
## Hyperparameters
Being effective in developing your deep neural networks requires that you not only organize your parameters well but also your hyperparameters. 
- learning rate $$\alpha$$  
- iterations  
- hidden layers L
- hidden units $$n^{[1]}, n^{[2]}, ...$$  

These are hyperparameters that control the ultimate parameters W and b.

Others: momentum, minibatch size, various forms of regularization parameters, etc.

----
## Some words
Applied deep learning is a very empirical process.  
Deep learning technology is very good at learning very flexible and complex functions used to learn X to Y mappings.

----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
