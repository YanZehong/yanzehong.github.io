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

----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
