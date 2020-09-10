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

$$a^{[l]} = np.multiply(a^{[l]},d^{[l]})    # a^{[l]} *= d^{[l]}$$

(3)Scale up, makeing sure the expected value of $$z^{[l+1]}$$ remain the same.

$$a^{[l]} = a^{[l]} / keep-prob$$

----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
