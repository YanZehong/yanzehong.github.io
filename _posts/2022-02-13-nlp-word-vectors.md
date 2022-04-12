---
layout: post
title: Word2vec
published: true
---

<div class="img-div-any-width" markdown="0">
  <image src="/images/NLP/word2vec.png"/>
  <br />
</div>

<blockquote class='subtle'>
  “<strong>There is in all things a pattern that is part of our universe. It has symmetry, elegance, and grace</strong> ~ Dune (1965)
</blockquote>

In this post, we'll go over the concept of word vector/embedding, and the mechanics of generating embeddings with word2vec. In addition, both word senses and neural network classfiers are covered in this post.
<!--more-->

## Main idea of word2vec
- Start with random word vectors
- Iterate through each word in the whole corpus
- Try to predict surrounding words using word vectors:

$$P(o|c) = \frac{\exp(u_{o}^{T}v_{c})}{\sum_{\omega}\exp(u_{\omega\in V}^{T}v_{c})}$$

where $v_{\omega}$ is a word vector when $\omega$ is a center word and $u_{\omega}$ is a word vector when $\omega$ is a context word.

- Learning: update vectors so they can predict actual surrounding words better
- Doing no more than this, this algorithm learns word vectors that capture well word similarity and meaningful directions in a wordspace!

## Optimization
- We have a cost function $J(\theta)$ we want to minimize

$$J(\theta) = - \frac{1}{T} \prod_{t=1}^{T} \prod_{-m\leq j \leq m, j\neq 0}^{T} logP(\omega_{t+j}|\omega_{t};\theta)$$

- **Gradient Descent** is an algorithm to minimize $J(\theta)$ by changing $\theta$
- Idea: from current value of $\theta$, calculate gradient of $J(\theta)$, then take small step in the direction of negative gradient. Repeat.

<blockquote class="subtle">
“If it falls outside your yardsticks, then you are engaged with intelligence, not with automation”  ~God Emperor of Dune
</blockquote>

I hope that you have a better sense for these concepts. As always, all feedback is appreciated <a href="mailto:yanzehong1101@outllook.com">@Ryan</a>.

## References


## Citation
If you found this work helpful for your research, please cite it as following:
```
Yan, Z. (2022). Word2vec [Blog post]. Retrieved from https://yanzehong.github.io/
```
