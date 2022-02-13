---
published: true
---
Ways to speed up the training of neural networks.
<!--more-->

## 1.Normalizating inputs

$$x = \frac{x - \mu}{\sigma}$$

- features are all on similar scales.  
- the cost function j looks more symmetric on average.It will be much easier and faster to optimize.    
- take much larger steps with gradient descent rather than needing to oscillate.  

![]({{site.baseurl}}/images/optimization1.png)

## 2.Vanishing / Exploding gradients
When you are training a very deep network, the derivatives or slopes sometimes would get either very small ($$\omega^{[l]}<1$$) or very big ($$\omega^{[l]}>1$$), which makes training difficult.  

Solution: careful choices of the random weight initialization.  

**ReLu activation function:**

$$\omega^{[l]} = np.random.randn(shape)*np.sqrt(\frac{2}{n^{[l-1]}})$$

**Other variance**

$$tanh: \sqrt{\frac{1}{n^{[l-1]}}}$$

$$Xavier: \sqrt{\frac{2}{n^{[l-1]}+n^{[l]}}}$$

## 3.Gradient checking
### 3.1 Nemerical approximation of gradients

$$\frac{f(\theta+\epsilon)-f(\theta-\epsilon)}{2\epsilon} \approx f^{'}(\theta)$$

![]({{site.baseurl}}/images/optimization2.png)

### 3.2 Steps
(1)Reshape all parameters, $$\omega^{[1]},b^{[1]}...\omega^{[L]},b^{[L]}$$,into a giant vector $$\theta$$  
(2)Reshape $$d\omega^{[1]},db^{[1]}...d\omega^{[L]},db^{[L]}$$,into a big vector $$d\theta$$  
(3)Implement a for loop  
![]({{site.baseurl}}/images/optimization3.png)

### 3.3 Notes about grad check
- Don't use gradient check in training - only to debug.  
- If algorithm fails grad check, look at components to try to identify bug. For example, the values of $$d\theta_{approx}[i]$$ and $$d\theta[i]$$. Then, locate $$d\omega^{[l]},db^{[l]}$$ in certain layer.  
- Remember regularization.  
- Doesn't work with dropout.You need to set $$keep-prob = 1.0$$  
- Run at random initialization; perhaps again after some training.  

----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
