---
layout: post
title: First Blog Post
published: true
---
---
layout: post
title: Docker Tutorial
---

Docker is a platform for developers and sysadmins to build, run and share applicantions with containers.

[Get Started with Docker](https://docker.com/get-started).

This page contains step-by-step instructions on how to get started with Docker.

## Docker overview
Docker provides the ability to package and run an application in a loosely isolated environment called a container. The isolation and security allow you to run many containers simultaneously on a give host.
build: images
pull: registry -> host 
`ship images from registry to host by docker daemon`
run: containers
### IMAGES
An image is a read-only template with instructions for creating a Docker container. To build your own image, you create a Dockerfile with a simple syntax for defining the steps needed to create the image and run it. Each instruction in a Dockerfile creates a layer in the image.
### CONTAINERS
A container is a runnable instance of an image. You can create, start, stop, move or delete a container using Docker API or CLI.

### REGISTRIES

#### Header 4

A link to [Jekyll Now](http://github.com/barryclark/jekyll-now/). A big ass literal link <http://github.com/barryclark/jekyll-now/>

An image, located within /images

![an image alt text]({{ site.baseurl }}/images/jekyll-logo.png "an image title")

* A bulletted list
- alternative syntax 1
+ alternative syntax 2
  - an indented list item

1. An
2. ordered
3. list

Inline markup styles:

- _italics_
- **bold**
- `code()`

> Blockquote
>> Nested Blockquote

Syntax highlighting can be used with triple backticks, like so:

```javascript
/* Some pointless Javascript */
var rawr = ["r", "a", "w", "r"];
```

Use two trailing spaces  
on the right  
to create linebreak tags  

Finally, horizontal lines

----
****