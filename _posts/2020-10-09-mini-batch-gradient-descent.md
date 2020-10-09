---
published: true
---
An optimizaation algorithm that will enable you to train neural network much faster in the regime of big data.

## 1.Definition

$$X = [x^{(1)},x^{(2)},x^{(3)},...,x^{(1000)},x^{(1001)},...,x^{(2000)},...,x^{(m)}]$$

$$Y = [y^{(1)},y^{(2)},y^{(3)},...,y^{(1000)},y^{(1001)},...,y^{(2000)},...,y^{(m)}]$$

where the shape of X is $$(n_{x},m)$$ and the shape of Y is $$(1,m)$$. If m = 5,000,000, we get 5,000 mini-batches of 1,000 each.

$$X = [X^{\{ 1 \}},X^{\{ 2 \}},X^{\{ 3 \}},...,X^{\{ 5000 \}}]$$

$$Y = [Y^{\{ 1 \}},Y^{\{ 2 \}},Y^{\{ 3 \}},...,Y^{\{ 5000 \}}]$$

## 2.Implementation
![]({{site.baseurl}}/images/minibatch_1.PNG)

The code above is called doing one epoch of training and epoch means a single pass through the training set. A single passs allows you to take only one gradient descent step. With mini-batch gradient descent, a single pass through the traning set (one epoch) allows you to take 5,000 gradient descent steps. Of course, you can also add multiple passes through the training set until it hopefully converges approximately.

## 3.Details
![]({{site.baseurl}}/images/minibatch_2.PNG)

![]({{site.baseurl}}/images/minibatch_3.PNG)

### Choose mini-batch size (A hyper-parameter)

(1) If it is a small training set, like m <= 2000, use batch gradient descent (size = m).  
(2) Typical mini-batch size: 64, 128, 256, 512  
(3) Make sure mini-batch $$(X^{\{ t \}},Y^{\{ t \}})$$ fits in CPU/GPU memory.  

----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
