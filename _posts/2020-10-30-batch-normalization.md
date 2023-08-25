---
published: false
---
BN makes your hyperparameter search much easier, makes your neural network much more robust, and also enable you to much more easily train even very deep networks.
<!--more-->

## 1.Normalizing inputs to sepeed up learning
There are some debates about whether or not we should normalize the value before the activation funciton, $$z^{[l]}$$, or normalize the value after applying activation function, $$a^{[l]}$$. Actually, normalizing $$z^{[l]}$$ is done much more often.

### 1.1 Implementing Batch Norm
Give some intermediate values in neural network, like hidden unit values $$z^{[l](1)}, z^{[l](2)}, ..., z^{[l](m)}$$

![]({{site.baseurl}}/images/bn_1.PNG)

If we don't want the hidden units to always have mean 0 and variance 1. Maybe it makes sense for hidden units to have a different distribution as follows.

![]({{site.baseurl}}/images/bn_2.PNG)

where $$\gamma$$ and $$\beta$$ are learnable parameters. So it allows you to set mean or variance to whatever you want.

## 2.Fitting Batch Norm into a neural netowrk


----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
