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

## 3.Adam (Adaptive moment estimation)
Many optimization algorithms proposed by some well-known researchers showed that they worked weill in a few problems. However, those algorithms subsequently were shown not to generalize that well to the wide range of neural network.  
Adam optimization algorithm is basically combining momentum with RMSprop. Let's see how it works.

> Initialization: $$v_{dW}=0, s_{dW}=0, v_{db}=0, s_{db}=0$$  
> on iteration t:
>> Compute $$dW, db$$ on the current mini-batch  
>> $$v_{dW}=\beta_{1} v_{dW} + (1-\beta_{1})dW, v_{db}=\beta_{1} v_{db} + (1-\beta_{1})db$$  
>> $$s_{dW}=\beta_{2} s_{dW} + (1-\beta_{2})dW^{2}, s_{db}=\beta_{2} s_{db} + (1-\beta_{2})db^{2}$$  
>> Implement bias correction  
>> $$v_{dW}^{corrected} = \frac{v_{dW}}{1 - \beta_{1}^{t}}, v_{db}^{corrected} = \frac{v_{db}}{1 - \beta_{1}^{t}}$$  
>> $$s_{dW}^{corrected} = \frac{s_{dW}}{1 - \beta_{2}^{t}}, s_{db}^{corrected} = \frac{s_{db}}{1 - \beta_{2}^{t}}$$  
>> $$W = W - \alpha \frac{v_{dW}^{corrected}}{\sqrt{s_{dW}^{corrected}}+\epsilon}, b = b - \alpha \frac{v_{db}^{corrected}}{\sqrt{s_{db}^{corrected}}+\epsilon}$$ 

### 3.1 Hyperparameters choice
- $$\alpha$$ needs to be tune.  
- $$\beta_{1} = 0.9$$  
- $$\beta_{2} = 0.999$$  
- $$\epsilon = 10^{-8}$$  

----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
