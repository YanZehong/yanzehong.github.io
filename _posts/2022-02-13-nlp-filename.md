---
layout: post
title: NLP
published: true
---
Docker is a platform for developers and sysadmins to build, run and share applicantions with containers.


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
