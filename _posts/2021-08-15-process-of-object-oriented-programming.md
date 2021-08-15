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

First we need to make a list of all the nouns and research  each of these concepts and anything we don't know right now. Then, we can turn it into a class hierarchy by asking "What is similar to other things?" and "What is basically just another word for another thing?". Type it down in text editor:

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

Once we have this tree of classes and some of the functions we can try to write the code of it.  

![]({{site.baseurl}}/images/process_1.PNG)

The last step in the process isn't much a step as it is a while-loop. We don’t ever do this as a one-pass operation. Instead we go back over the whole process again and refine it based on information we’ve learned from later steps. Sometimes I’ll get to step 3 and realize that I need to work on 1 and 2 more, so I’ll stop and go back and work on those. Sometimes I’ll get a flash of inspiration and jump to the end to code up the solution in my head while I have it there, but then I’ll go back and do the previous steps to make sure I cover all the possibilities I have.


## 2.Bottom Up
Of course, there's another way to sovle problem that starts with code and goes ”up” to the abstract concepts. Here are the general steps you follow to do this:  
1. Take a small piece of the problem; hack on some code and get it to run barely.  
2. Refine the code into something more formal with classes and automated tests.  
3. Extract the key concepts you’re using and try to find research for them.
4. Write a description of what’s really going on.  
5. Go back and refine the code, possibly throwing it out and starting over.  
6. Repeat, moving on to some other piece of the problem.  

----
## Reference
[1] Zed A. Shaw (2017). _Learn Python3 the Hard Way_ (3nd ed.). Boston:Addison-Wesley.
