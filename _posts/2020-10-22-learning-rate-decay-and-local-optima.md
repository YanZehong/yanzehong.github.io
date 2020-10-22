---
published: true
---
A method that might help speed up your learning algorithm, is to slowly reduce the learning rate over time. Plus, we will talk about local optima and saddle points in neural networks.

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
I hope this section can help u have a little better intuition about the types of optimization problems.

----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
