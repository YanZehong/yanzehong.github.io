---
published: true
---
A good starting point for many programming problems when you are using Python, specifically with object-oriented programming (OOP).

## 1.Process (It is "top down")
- Write or draw about the problem.  
- Extract key concepts and research them.  
- Create a class hierarchy and object map for the concepts.  
- Code the classes and a test to run them.  
- Repeat and refine.  

It starts from the very abstract loose idea and then slowly refines it until the idea is solid and something you are able to code. 

### Example
A game description from [1]:  
”Aliens have invaded a space ship and our hero has to go through a maze of rooms defeating them so he can escape into an escape pod to the planet below. The game will be more like a Zork or Adventure type game with text outputs and funny ways to die. The game will involve an engine that runs a map full of rooms or scenes. Each room will print its own description when the player enters it and then tell the engine what room to run next out of the map.”  

* Map  
  next_scene  
  opening_scene  
* Engine
  play  
* Scene  
  enter  
  * Death  
  * Central Corridor  
  * Laser Weapon Armory  
  * The Bridge  
  * Escape Pod  

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
[1] Zed A. Shaw (2017). _Learn Python3 the Hard Way_ (3nd ed.). Boston:Addison-Wesley.
