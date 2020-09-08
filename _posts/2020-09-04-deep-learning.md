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
### 2.1 Bias/Variance --tradeoff
high bias (training data performance)  
solution:bigger network; train longer  
high variation(dev set performance)  
solution: more data; regularization  
### 2.2 Regularization
$$\min_{\omega, b} J(\omega, b)$$  
$$J(\omega, b) = \frac{1}{m} \sum_{i=1}^{m} L(y^{(i)}, y^{(i)}) + \frac{\lambda}{2m} ||\omega||_{2}^{2}$$

**$$L_{2}$$ regularization**  
**$$L_{1}$$ regularization**

----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
