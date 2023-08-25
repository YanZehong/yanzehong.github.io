---
published: false
---
Some tips for how to systematically organize your hyperparameter tuning process.
<!--more-->

## 1.Hyperparameters
- 1st (most important)  
(1) learning rate $$\alpha$$  
- 2nd  
(2) momentum $$\beta=0.9$$  
(3) the number of hidden units  
(4) mini-batch size  
- 3rd  
(5) the number of layers  
(6) learning rate decay  
- 4th  
(7) adam optimization $$\beta_{1}=0.9, \beta_{2}=0.999, \epsilon=10^{-8}$$  

## 2.Tuning
### 2.1 Try random values: Don't use a grid
The reason is that it's difficult to know in advance which hyperparameters are going to be the most important for the problem. Take an example, shown as below, if u sample in the grid then u tried out five values of $$\alpha$$. You might find out that all of the different values of $$\epsilon$$ give u essentially the same answer. So you've trained 25 models and only got into trial five values for the learning rate.  
However, if u were to sample at random, then u will have tried out 25 distinct values of the learning rate $$\alpha$$ and therefore u are more likely to find a value that works really well. (see in the right of below figure.)  

![]({{site.baseurl}}/images/hyperpara_1.PNG)

### 2.2 Coarse to fine search
Maybe you found that the red point work the best and some points around it tended to work really well. Then, you can zoom in to a smaller region of the hyperparameters and sample more densely within this area. Such type of a coarse to fine search is frequently used.

![]({{site.baseurl}}/images/hyperpara_2.PNG)

## 3.An approriate scale to pick hyperparameters
Let's look at the following example. It seems more seasonable to search for hyperparameters on a log scale instead of using a linear scale.

![]({{site.baseurl}}/images/hyperpara_3.PNG)

## 4.Practice
- Babysitting one model.(a huge data set but not a lot of computational resources)  

- Training many models in parallel  

![]({{site.baseurl}}/images/hyperpara_4.PNG)

----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
