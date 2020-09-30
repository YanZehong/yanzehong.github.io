---
published: true
---
A powerful regularization technique. Let's see how it works in this post.

## 1.How?
- Set some probability of eliminating nodes in each of the layers of neural network.
- Get a much smaller, dimished network to be trained.(see in figure below.)
- Toss a set of coins again and keep a different set of nodes and then dropout different nodes. (it means we randomly zero out different hidden units.)

![]({{site.baseurl}}/images/dropout1.png)

## 2.Implementing dropout ("Inverted dropout")
(1)Set dropout vector d, for example

$$d^{[l]} = np.random.rand(a^{[l]}.shape[0], a^{[l]}.shape[1]) < keep-prob$$

(2)Element-wise multiplication

$$a^{[l]} = np.multiply(a^{[l]},d^{[l]})\quad \textrm{or} \; a^{[l]} *= d^{[l]}$$


(3)Scale up, makeing sure the expected value of $$z^{[l+1]}$$ remain the same.

$$a^{[l]} = a^{[l]}\: / \: keep-prob$$

**Python: Forward**

![]({{site.baseurl}}/images/dropout3.png)


**Python: Backward**

![]({{site.baseurl}}/images/dropout4.png)

## 3.Prediction
**There is no dropout while making prediction at test time.**

## 4.Why does it work?
Can't rely on any one feature, so have to spread out/shrink weights.

For the layer with the biggest weight matrix, a lot of parameters, you should set a relatively low keep-prob. On the contrary, whereas for different layers where you might less worry about over-fitting, you could have a higher keep-prob, like 0.7 or 1. (As shown in the following figure.)

![]({{site.baseurl}}/images/dropout2.png)

After dropping out, the cost function is no longer well-defined. Consequently, you need turn off drop out at first and set key prop equals one. Then, you run your code and make sure that it is monotonically decreasing cost. Finally, turn on drop out and hope that we didn't introduce bugs into code during drop out.

## 5.Note
- A common mistake when using dropout is to use it both in training and testing. You should use dropout (randomly eliminate nodes) only in training.  
- Apply dropout both during forward and backward propagation.  
- During training time, divide each dropout layer by keep_prob to keep the same expected value for the activations. For example, if keep_prob is 0.5, then we will on average shut down half the nodes, so the output will be scaled by 0.5 since only the remaining half are contributing to the solution. Dividing by 0.5 is equivalent to multiplying by 2. Hence, the output now has the same expected value.  

----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
