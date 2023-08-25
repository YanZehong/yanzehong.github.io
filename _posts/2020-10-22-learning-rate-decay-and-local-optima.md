---
published: false
---
A method that might help speed up your learning algorithm is to slowly reduce learning rate over time. Plus, we will talk about local optima and saddle points in neural networks.
<!--more-->

## 1.Why?
- Suppose we're implementing mini-batch gradient descent, with a reasonably small mini-batch, maybe 64 examples in a mini-batch. Then as we iterate, steps will be a littile bit noisy. It will tend towards the minimum, but it won't exactly converge (shown as blue line). It just wandering around because the value of $$\alpha$$ is fixed.  
- Solution: Afford to take much bigger steps during the initial steps. Then it's able to become smaller to take smaller steps as learning approaches converge (green line).  

![]({{site.baseurl}}/images/lr_decay_1.PNG)

## 2.Implementation
(1) one epoch is one pass through dataset.
(2) set

$$\alpha = \frac{1}{1+decay-rate \ast epoch-num} \alpha_{0}$$

## 3.Other learning rate decay methods
(1) exponential decay

$$\alpha = 0.95^{epoch-num} \cdot \alpha_{0}$$

(2)

$$\alpha = \frac{k}{\sqrt{epoch-num}} \cdot \alpha_{0}$$  

$$\alpha = \frac{k}{\sqrt{t}} \cdot \alpha_{0}$$

where k is a constant, t is a hyperparameter over the mini-batch number.

(3) decrease staircase

![]({{site.baseurl}}/images/lr_decay_2.PNG)

(4) manual decay - works only for a small number of models.  

## 4.Local optima problems
### 4.1 Introduction
I hope this section can help u have a little better intuition about the types of optimization problems.  

It turns out when we create a neural network, most points of zero gradient are not local optima like points shown on the left. Instead, most points of zero gradient in a cost function are saddle points shown as the right side here.  
Informally, a function of very high dimensional space, say, a 20,000 dimensional space, if the gradient is zero, then in each direction it can either be a convex function or a concave function. Therefore, you are much more likely to get some directions where the curve bends up as well as some directions with the curve bending down, called a saddle point.

![]({{site.baseurl}}/images/lr_decay_3.PNG)

### 4.2 Real problem: plateaus
Plateau is a region where derivative is close to zero for a long time.

![]({{site.baseurl}}/images/lr_decay_4.PNG)

lessons:
- Unlikely to get stuck in a bad local optima
- Plateaus can make learning slow. And this is where learning algorithms, like momentum or RMSprop or Adam can really help you.

----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
