---
published: true
---
Practical aspects of deep learning.

## Train/Dev/Test sets
### Basic rules for spliting datasets  
train/test: 70% / 30%  
train/dev/test: 60% / 20% / 20%  
Big data era (like 1,000,000 examples): 98/1/1 or 99.5/0.4/0.1  

### Mismatched train/test distribution
For example,  
- Training set: cat pictures from webpages  
- Dev/test set: cat pictures from users using apps  
**** Make sure dev and test come from the same distribution.****
**** Not having a test set might be okay. (only dev set.)****

----
## Reference
Andrew Y Ng. (n.d.). _Deep Learning Specialization_ [Video]. Coursera.  
<https://www.coursera.org/specializations/deep-learning/>
