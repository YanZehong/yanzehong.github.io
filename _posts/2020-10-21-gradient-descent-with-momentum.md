---
published: true
---
Introduce an optimization algorithm that are much faster than gradient descent.

## 1.Intuition

$$v_{t}=\beta v_{t-1} + (1-\beta)\theta_{t}$$

$$v_{t} \approx \frac{1}{1-\beta}$$

since $$(1-\epsilon)^{1/\epsilon}=\frac{1}{e}$$ and $$\epsilon = 1 - \beta$$

![]({{site.baseurl}}/images/ewa_1.PNG)


----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
