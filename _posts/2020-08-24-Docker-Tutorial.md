---
layout: post
title: Docker
published: true
---
Docker is a platform for developers and sysadmins to build, run and share applicantions with containers.

[Get Started with Docker](https://docker.com/get-started).

This page contains step-by-step instructions on how to get started with Docker.
<!--more-->

## Docker overview
Docker provides the ability to package and run an application in a loosely isolated environment called a container. The isolation and security allow you to run many containers simultaneously on a give host.

build: images

pull: ship images from registry to host 

run: containers

### IMAGES
An image is a read-only template with instructions for creating a Docker container. To build your own image, you create a Dockerfile with a simple syntax for defining the steps needed to create the image and run it. Each instruction in a Dockerfile creates a layer in the image.

### CONTAINERS
A container is a runnable instance of an image. You can create, start, stop, move or delete a container using Docker API or CLI.

#### Example
The following command runs an _ubuntu_ container, attaches interactively to your local command-line session, and runs _/bin/bash_.

{% highlight ruby %}
$ docker run -i -t ubuntu /bin/bash
{% endhighlight %}

### REGISTRIES
A Docker registry stores Docker images. Docker Hub is a public registry that anyone can use, and Docker is configured to look for images on Docker Hub. You can also run your own private registry.

#### Command
{% highlight ruby linenos %}
 /* pull required images from your configured registry */
    docker pull
    docker run
 /* push image to your configured registry */
    docker push
{% endhighlight %}
