---
published: true
---
Practical aspects of deep learning.

## 1.Train/Dev/Test sets
### 1.1 Basic rules for splitting datasets  
train/test: 70 / 30 (%)  
train/dev/test: 60 / 20 / 20 (%)  
Big data era (like 1,000,000 examples): 98 / 1 / 1 or 99.5 / 0.4 / 0.1  

### 1.2 Mismatched train/test distribution
For example,  
- Training set: cat pictures from webpages  
- Dev/test set: cat pictures from users using apps  

**Make sure dev and test come from the same distribution.**  
**Not having a test set might be okay. (only dev set.)**

## 2.Basic recipie for machine learning
### 2.1 Bias/Variance (tradeoff)
- High bias (training data performance)  
solution:bigger network; train longer  
- High variation(dev set performance)  
solution: more data; regularization

**Model**

$$y^{'} = \omega_{0} + \omega_{1}x + \omega_{2}x^{2} + \omega_{3}x^{3} + ...$$

$$J(\omega, b) = \frac{1}{m} \sum_{i=1}^{m} L(y^{'(i)}, y^{(i)}) + \frac{\lambda}{2m} ||\omega||_{2}^{2}$$

If we set $$\lambda$$ to be very very large, the punishment term will be large, which makes the curve become a horizontal line with all coefficient tending to 0. _E.g._, if $$\lambda = 10000$$, we will get $$\omega_{1} \approx 0, \omega_{2} \approx 0, ... y^{'} \approx \omega_{0}$$. By contrast, the curve will overfit when is too $$\lambda$$ small.  
Therefore, the general approach is to use validation to select the appropriate $$\lambda$$, and then apply it on the test set.  
### Linear regression with regularization
![]({{site.baseurl}}/images/bias:variance1.png)

### B/V as a function of the regulatization parameter
![]({{site.baseurl}}/images/bias:variance2.png)

### Learning curve
Draw the Learning Curve to help us understand whether the current model is in the bias or variance stage. Thus, we can adjust the model according to it.

![]({{site.baseurl}}/images/bias:variance3.png)

In the case of high bias, increase the number of samples m, we can see that the error will not change much soon, and the cost of training and validation set will be very large.

![]({{site.baseurl}}/images/bias:variance4.png)

However, for the high variance problem, if the number of m is increased, it will help decrease the cost of the model.

### 2.2 Regularization
To prevent overfitting  
Objective function:

$$\min_{\omega, b} J(\omega, b)$$

$$J(\omega, b) = \frac{1}{m} \sum_{i=1}^{m} L(y^{'(i)}, y^{(i)}) + \frac{\lambda}{2m} ||\omega||_{2}^{2}$$  

**$$L_{2}$$ Regularization**

$$||\omega||_{2}^{2} = \sum_{j=1}^{n_{x}} \omega_{j}^{2} = \omega^{T}\omega$$  

**$$L_{1}$$ Regularization**

$$\frac{\lambda}{2m}\sum_{i=1}^{n_{x}} |\omega_{i}| = \frac{\lambda}{2m}||\omega||_{1}$$  

**Frobenius norm**

$$||\omega^{[l]}||_{F}^{2} = \sum_{i=1}^{n^{[l]}}\sum_{j=1}^{n^{[l-1]}}(\omega_{i,j}^{[l]})^{2}$$

**Weight decay**  
Update

$$\omega^{[l]} = \omega^{[l]}-\alpha d\omega^{[l]}$$

$$\omega^{[l]} = \omega^{[l]}-\alpha[(from-backprop) + \frac{\lambda}{m}\omega^{[l]}]$$

$$   = \omega^{[l]} - \frac{\alpha\lambda}{m}\omega^{[l]} - \alpha(from-backprop)$$

----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
