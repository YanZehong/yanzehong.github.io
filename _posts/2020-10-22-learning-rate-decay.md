---
published: true
---
A method that might help speed up your learning algorithm, is to slowly reduce the learning rate over time.

## 1.Why?
- Suppose we're implementing mini-batch gradient descent, with a reasonably small mini-batch, maybe 64 examples in a mini-batch. Then as we iterate, steps will be a littile bit noisy. It will tend towards the minimum, but it won't exactly converge (Shown as blue line). It just wandering around because the value of $$\alpha$$ is fixed.  
- Solution: Afford to take much bigger steps during the initial steps. Then it's able to become smaller to take smaller steps as learning approaches converge (green line).  

![]({{site.baseurl}}/images/lr_decay_1.PNG)


----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
