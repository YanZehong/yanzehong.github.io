---
published: true
---
Ways to speed up the training of neural networks.

## 1.Normalizating inputs

$$x = \frac{x - \mu}{\sigma}$$

- features are all on similar scales.  
- the cost function j looks more symmetric on average.It will be much easier and faster to optimize.    
- take much larger steps with gradient descent rather than needing to oscillate.  

![]({{site.baseurl}}/images/optimization1.png)

## 2.Vanishing / Exploding gradients
When you are training a very deep network, the derivatives or slopes sometimes would get either very small ($$\omega^{[l]}<1$$) or very big ($$\omega^{[l]}>1$$), which makes training difficult.  
Solution: careful choices of the random weight initialization.
ReLu activation function:

$$\omega^{[l]} = np.random.randn(shape)*np.sqrt(\frac{2}{n^{[l-1]}})$$

**Other variance**

$$tanh: \sqrt{\frac{1}{n^{[l-1]}}}$$

$$Xavier: \sqrt{\frac{2}{n^{[l-1]}+n^{[l]}}}$$


----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
