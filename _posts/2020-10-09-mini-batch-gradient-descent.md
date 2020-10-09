---
published: true
---
An optimizaation algorithm that will enable you to train neural network much faster in the regime of big data.

## 1.Definition

$$X = [x^{(1)},x^{(2)},x^{(3)},...,x^{(1000)},x^{(1001)},...,x^{(2000)},...,x^{(m)}]$$

$$Y = [y^{(1)},y^{(2)},y^{(3)},...,y^{(1000)},y^{(1001)},...,y^{(2000)},...,y^{(m)}]$$

where the shape of X is $$(n_{x},m)$$ and the shape of Y is $$(1,m)$$. If m = 5,000,000, we get 5,000 mini-batches of 1,000 each.

$$X = [X^{{1}},X^{{2}},X^{{3}},...,X^{{5000}}]$$

$$Y = [Y^{{1}},Y^{{2}},Y^{{3}},...,Y^{{5000}}]$$



----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
