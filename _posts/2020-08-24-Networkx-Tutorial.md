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
  	import networkx as nx
  	G = nx.Graph()
    {% endhighlight %}
</body>

## Nodes
Several ways to add nodes by NetworkX

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
    # add one node at a time
    G.add_node(1)
    # add nodes from any iterable container
    G.add_nodes_from([2, 3])
    # add nodes along with node attributes
    G.add_nodes_from([
        (4, {"color": "red"}),
        (5, {"color": "green"}),
    ])
  	# add nodes from another graph
	H = nx.path_graph(10)
	G.add_nodes_from(H)
    {% endhighlight %}
</body>

## Edges

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
    # add one edge at a time
    G.add_edge(1, 2)
	e = (2, 3)
	G.add_edge(*e) # unpack edge typle*
    # add a list of edges
    G.add_edges_from([(1, 2), (1, 3)])
    # add edges from edge-tuples
    G.add_edges_from(H.edges)
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