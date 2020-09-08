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
