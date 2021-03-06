# graph-theory
[![Build Status](https://travis-ci.org/root-11/graph-theory.svg?branch=master)](https://travis-ci.org/root-11/graph-theory)
[![Code coverage](https://codecov.io/gh/root-11/graph-theory/branch/master/graph/badge.svg)](https://codecov.io/gh/root-11/graph-theory)

A simple graph library...<br>
*... A bit like networkx, just without the overhead...*<br> 
*... similar to graph-tool, without the Python 2.7 legacy...*<br>
*... with code that you can explain to your boss...*<br>

---------------------------
Install:

    pip install graph-theory

---------------------------
Import:

    import Graph
    g = Graph()  

    import Graph3d
    g3d = Graph3D()

---------------------------

Modules:

| module | description |
|:---|:---|
| `from graph import Graph, Graph3D` | Elementary methods (see basic methods below) for Graph and Graph3D.|
| `from graph import ...` | All methods available on Graph (see table below) |
| `from graph.assignment_problem import ...` | solvers for assignment problem, the Weapons-Target Assignment Problem, ... |
| `from graph.hash import ...` | graph hash functions: graph hash, merkle tree, flow graph hash | 
| `from graph.random import ...` | graph generators for random, 2D and 3D graphs. |
| `from graph.transshipment_problem import ...` | solvers for the transshipment problem |
| `from graph.visuals import ...` | methods for creating matplotlib plots |
| `from graph.finite_state_machine import ...` | finite state machine |


All module functions are available from Graph and Graph3D (where applicable).

| Graph | Graph3D | methods | returns |
|:---:|:---:|:---|:---|
| + | + | `a in g` | assert if g contains node a |
| + | + | `g.add_node(n, [obj])` | adds a node (with a pointer to object `obj` if given) |
| + | + | `g.copy()` | returns a shallow copy of `g` |
| + | + | `g.node(node1)` | returns object attached to node 1 |
| + | + | `g.del_node(node1)` | deletes node1 and all it's edges |
| + | + | `g.nodes()` | returns a list of nodes |
| + | + | `len(g.nodes())` | returns the number of nodes |
| + | + | `g.nodes(from_node=1)` | returns nodes with edges from node 1 |
| + | + | `g.nodes(to_node=2)` | returns nodes with edges to node 2 |
| + | + | `g.nodes(in_degree=2)` | returns nodes with 2 incoming edges |
| + | + | `g.nodes(out_degree=2)` | returns nodes with 2 outgoing edges |
| + | + | `g.add_edge(1,2,3)` | adds edge to g for vector `(1,2)` with value `3` |
| + | + | `g.edge(1,2)` | returns value of edge between nodes 1 and 2 |
| + | + | `g.edge(1,2,default=3)` | returns `default=3` if `edge(1,2)` doesn't exist. <br>similar to `d.get(key, 3)`|
| + | + | `g.del_edge(1,2)` | removes edge between nodes 1 and 2 |
| + | + | `g.edges()` | returns a list of edges |
| + | + | `len(g.edges())` | returns the number of edges |
| + | + | `g.edges(path=[path])` | returns a list of edges (along a path if given). |
| + | + | `same_path(p1,p2)` | compares two paths to determine if they contain same sequences <br>ex.: `[1,2,3] == [2,3,1]`  |
| + | + | `g.edges(from_node=1)` | returns edges outgoing from node 1 |
| + | + | `g.edges(to_node=2)` | returns edges incoming to node 2 |
| + | + | `g.from_dict(d)` | updates the graph from a dictionary |
| + | + | `g.to_dict()` | returns the graph as a dictionary |
| + | + | `g.from_list(L)` | updates the graph from a list |
| + | + | `g.to_list()` | return the graph as a list of edges |
| + | + | `g.shortest_path(start,end)` | returns the distance and path for path with smallest edge sum |
| + | + | `g.is_connected(start,end)` | determines if there is a path from start to end |
| + | + | `g.breadth_first_search(start,end)` | returns the number of edges and path with fewest edges |
| + | + | `g.degree_of_separation(n1,n2)` | returns the distance between two nodes using BFS |
| + | + | `g.network_size(n1, degree_of_separation)` | returns the nodes within the range given by `degree_of_separation` |
| + | + | `g.phase_lines()` | returns a dictionary with the phase_lines for a non-cyclic graph. |
| + | + | `g.sources(n)` | returns the source_tree of node `n` |
| + | + | `g.depth_first_search(start,end)` | returns path using DFS and backtracking  |
| + | + | `g.depth_scan(start, criteria)` | returns set of nodes where criteria is True |
| + | + | `g.distance_from_path(path)` | returns the distance for path. |
| + | + | `g.maximum_flow(source,sink)` | finds the maximum flow between a source and a sink |
| + | + | `g.solve_tsp()` | solves the traveling salesman problem for the graph |
| + | + | `g.subgraph_from_nodes(nodes)` | returns the subgraph of `g` involving `nodes` |
| + | + | `g.is_subgraph(g2)` | determines if graph `g2` is a subgraph in g |
| + | + | `g.is_partite(n)` | determines if graph is n-partite |
| + | + | `g.has_cycles()` | determines if there are any cycles in the graph |
| + | + | `g.components()` | returns set of nodes in each component in `g` |
| + | + | `g.same_path(p1,p2)` | compares two paths, returns True if they're the same |
| + | + | `g.adjacency_matrix()` | returns the adjacency matrix for the graph |
| + | + | `g.all_pairs_shortest_paths()` | finds the shortest path between all nodes |
| + | + | `g.shortest_tree_all_pairs()` | finds the shortest tree for all pairs |
| + | + | `g.has_path(p)` | asserts whether a path `p` exists in g |
| + | + | `g.all_paths(start,end)` | finds all combinations of paths between 2 nodes|
| - | + | `g3d.distance(n1,n2)` | returns the spatial distance between `n1` and `n2` |
| - | + | `g3d.n_nearest_neighbour(n1, [n])` | returns the `n` nearest neighbours to node `n1` |
| - | + | `g3d.plot()` | returns matplotlib plot of the graph. |


## FAQ

| want to... | doesn't work... | do instead... | ...but why? |
|:---|:---|:---|:---|
| have multiple edges between two nodes | `Graph(from_list=[(1,2,3), (1,2,4)]` | Add dummy nodes<br>`[(1,a,3), (a,2,0),`<br>` (1,b,4),(b,2,0)]` | Explicit is better than implicit. |
| multiple values on an edge | `g.add_edge(1,2,{'a':3, 'b':4})` | Have two graphs<br>`g_a.add_edge(1,2,3)`<br>`g_b.add_edge(1,2,4)` | Most graph algorithms don't work with multiple values |   

## Credits:

- Arturo Soucase for packaging and testing. 
- Peter Norvig for inspiration on TSP from [pytudes](https://github.com/norvig/pytudes/blob/master/ipynb/TSP.ipynb).
- Harry Darby for the mountain river map.
- Kyle Downey for depth_scan algorithm.

