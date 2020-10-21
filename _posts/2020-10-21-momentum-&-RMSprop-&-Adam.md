---
published: true
---
Three optimization algorithms work almost always faster than the standard gradient descent algorithm.

## 1.Description (gradient descent with momentum)
After applying momentum, the oscillations in the vertical direction will tend to average out to something closer to zero. Whereas, on the horizontal direction, the average will still be pretty big. You can find it ends up with a few iteration, much smaller oscillations in the vertical direction, but are more directed to move toward the minimum in horizontal direction.

![]({{site.baseurl}}/images/momentum_1.PNG)

### 1.1 Implementation
> Initialization: $$v_{dW}=0, v_{db}=0$$  
> on iteration t:
>> Compute $$dW, db$$ on the current mini-batch  
>> $$v_{dW}=\beta v_{dW} + (1-\beta)dW$$  
>> $$v_{db}=\beta v_{db} + (1-\beta)db$$  
>> $$W = W - \alpha v_{dW}, b = b - \alpha v_{db}$$  
  
Hyperparameters:$$\alpha, \beta$$. Generally, $$\beta=0.9$$, representing average over last about 10 gradients.

Another version of momentum is $$v_{dW}=\beta v_{dW} + dW$$, the perpose is that $$v_{dW}$$ ends up being scaled by $$\frac{1}{1-\beta}$$. So when you are performing these gradient descent updates, $$\alpha$$ just needs to change by a corresponding value of $$\frac{1}{1-\beta}$$.

## 2.RMSprop
Similar to momentum, it has the effects of damping out the oscillations in gradient descent, in mini-batch descent. In addition, it allows you to use a larger learning rate $$\alpha$$, speeding up your learning algorithm.

![]({{site.baseurl}}/images/rmsprop_1.PNG)

## 3.Adam

----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
