---
published: true
---
NetworkX is a Python package for the creation, manipulation, and study of the structure, dynamics, and functions of complex networks.

-Website: [NetworkX 2.5, including documentation](https://networkx.github.io).
-Source: [GitHub](http://github.com/networkx/networkx)

This guide can help you start working with NetworkX.

## Creating a graph
Create an empty graph with no nodes and no edges.

<head>
    <title>Rouge</title>
    <link media="all" rel="stylesheet" type="text/css" href="../assets/rouge/rouge.css" />
    <style>
        pre{
            background: rgba(0, 0, 0, 0.95);
        }
    </style>
</head>

<body>
    {% highlight ruby %}
    def show
  	import networkx as nx
  	G = nx.Graph()
    {% endhighlight %}
</body>

### Header 3

#### Header 4

A link to [Jekyll Now](http://github.com/networkx/networkx). A big ass literal link <http://github.com/barryclark/jekyll-now/>

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