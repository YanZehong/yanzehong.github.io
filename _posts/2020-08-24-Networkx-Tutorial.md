---
published: true
---
NetworkX is a Python package for the creation, manipulation, and study of the structure, dynamics, and functions of complex networks.

- Website: [NetworkX 2.5, including documentation](https://networkx.github.io).

- Source: [GitHub](http://github.com/networkx/networkx)

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
    # difference
    G.add_node("spam")        # adds node "spam"
    G.add_nodes_from("spam")  # adds 4 nodes: 's', 'p', 'a', 'm'
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

## Examining elements of a graph
There are four basic graph properties facilitate reporting, which are set-like views of the nodes, edges, neighbors (adjacencies), and degrees of nodes in a graph.
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
    list(G.nodes)
    list(G.edges)
    list(G.adj[1]) # adjacent nodes of 1
    G.degree[1] # the number of edges incident to 1
    G.number_of_nodes()
    G.number_of_edges()
    {% endhighlight %}
</body>

Another way to access to edges and neighbors.
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
    >>> G = nx.Graph([(1, 2, {"color": "yellow"})])
    >>> G[1]
    AtlasView({2: {'color': 'yellow'}})
    >>> G[1][2]
    {'color': 'yellow'}
    >>> G.edges[1, 2]
    {'color': 'yellow'}
    # get/set the attributes of an edge using subscript notation
    >>> G.[1][2]['color'] = 'blue'
    {'color': 'blue'}
    >>> G.edges[1, 2]['color'] = "red"
    >>> G.edges[1, 2]
    {'color': 'red'}
    {% endhighlight %}
</body>

Fast examination of all (node, adjacency) pairs
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
    FG = nx.Graph()
    FG.add_weighted_edges_from([(1, 2, 0.125), (1, 3, 0.75), (2, 4, 1.2), (3, 4, 0.375)])
    for n, nbrs in FG.adj.items():
        for nbr, eattr in nbrs.items():
          wt = eattr['weight']
          if wt < 0.5: print(f"({n}, {nbr}, {wt:.3})")
    # Convenient access to all edges
    for (u, v, wt) in FG.edges.data('weight'):
        if wt < 0.5:
          print(f"({u}, {v}, {wt:.3})")
    {% endhighlight %}
</body>

## Removing elements from a graph
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
    G.remove_node(2)
    G.remove_nodes_from("spam")
    G.remove_edge(1, 3)
    {% endhighlight %}
</body>

## Adding attributes to graphs, nodes, and edges
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
    # graph
    >>> G = nx.Graph(day="Friday")
    >>> G.graph['day'] = "Monday"
    >>> G.graph
    {'day': 'Monday'}
  
    # node
    >>> G.add_node(1, time='5pm')
    >>> G.add_nodes_from([3], time='2pm')
    >>> G.nodes[1]
    {'time': '5pm'}
    >>> G.nodes[1]['room'] = 714
    >>> G.nodes.data()
    NodeDataView({1: {'time': '5pm', 'room': 714}, 3: {'time': '2pm'}})
  
    # edge
    G.add_edge(1, 2, weight=4.7 )
    G.add_edges_from([(3, 4), (4, 5)], color='red')
    G.add_edges_from([(1, 2, {'color': 'blue'}), (2, 3, {'weight': 8})])
    G[4][5]['weight'] = 4.7
    G.edges[3, 4]['weight'] = 4.2
    {% endhighlight %}
</body>

## Directed graphs
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
    >>> DG = nx.DiGraph() 
    >>> DG.add_weighted_edges_from([(1, 2, 0.5), (3, 1, 0.75)])
    >>> DG.out_degree(1, weight='weight')
    0.5
    >>> DG.degree(1, weight='weight')
    1.25
    >>> list(DG.neighbors(1))
    [2]
    {% endhighlight %}
</body>

### Convert directed graph to an undirected one
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
    DG = nx.DiGraph() 
    DG.to_undirected()
    # Another way
    H = nx.Graph(DG)
    {% endhighlight %}
</body>

## Multigraphs
Following classes for graphs allow multiple edges between any pair of nodes. This can be powerful for some applications, but many algorithms are not well defined on such graphs.

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
    >>> MG = nx.MultiGraph() 
    >>> MG.add_weighted_edges_from([(1, 2, 0.5), (1, 2, 0.75), (2, 3, 0.5)])
    >>> dict(MG.degree(weight='weight'))
    {1: 1.25, 2: 1.75, 3: 0.5}
    {% endhighlight %}
</body>

## Analyzing graphs
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
    >>> G = nx.Graph()
    >>> G.add_edges_from([(1, 2), (1, 3)])
    >>> G.add_node("spam")
    >>> list(nx.connected_components(G))
    [{1, 2, 3}, {'spam'}]
    >>> sorted(d for n, d in G.degree())
    [0, 1, 1, 2]
    >>> nx.clustering(G)
    {1: 0, 2: 0, 3: 0, 'spam': 0}
    {% endhighlight %}
</body>

Some functions with large output iterate over (node, value) 2-tuples.
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
    >>> sp = dict(nx.all_pairs_shortest_path(G))
    >>> sp[3]
    {3: [3], 1: [3, 1], 2: [3, 1, 2]}
    {% endhighlight %}
</body>

## Drawing graphs
NetworkX is not primarily a graph drawing package but basic drawing with Matplotlib as well as an interface to use the open source Graphviz software package are included.
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
    import matplotlib.pyplot as plt
    G = nx.petersen_graph()
    plt.subplot(121)
    nx.draw(G, with_labels=True, font_weight='bold')
    plt.subplot(122)
    nx.draw_shell(G, nlist=[range(5, 10), range(5)], with_labels=True, font_weight='bold')
    plt.show()
    {% endhighlight %}
</body>

### Output
![an image alt text]({{ site.baseurl }}/images/path1.png "an image title")

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
    options = {
        'node_color': 'black',
        'node_size': 100,
        'width': 3,
    }
    plt.subplot(221)
    nx.draw_random(G, **options)
    plt.subplot(222)
    nx.draw_circular(G, **options)
    plt.subplot(223)
    nx.draw_spectral(G, **options)
    plt.subplot(224)
    nx.draw_shell(G, nlist=[range(5,10), range(5)], **options)
    plt.savefig("path2.png")
    {% endhighlight %}
</body>

### Output
![an image alt text]({{ site.baseurl }}/images/path2.png "an image title")

writes to the file in the local directory.
<body>
    {% highlight ruby %}
    from networkx.drawing.nx_pydot import write_dot
    pos = nx.nx_agraph.graphviz_layout(G) # nx_pydot.graphviz_layout(G)
    nx.draw(G, pos=pos)
    write_dot(G, 'file.dot')
    {% endhighlight %}
</body>

See [Drawing](http://github.com/networkx/networkx) for additional details.

----
#### Reference
<https://networkx.github.io/documentation/stable/tutorial.html/>
