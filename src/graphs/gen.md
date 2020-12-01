# Generation Guide

Use `GEN` to generate instances of certain graph families based on input parameters. Generations options are specified in `Ans`, and are of the form `"[char][args]"`, where `char` is a single character (`A` to `Z`, `θ`, or `π`) and `args` is a string of numeric arguments separated by commas. Many different families are available, with varying degrees of complexity; the instances of graph families are limited only by the 999 vertex and edge limit imposed by TI-BASIC lists.

The vertex ordering used for generation are implemented with some convenient plotting layout or graph traversal method in mind, which can be investigated more closely be examining the generated output. Each family described below contains a short description and justification of the chosen vertex ordering. If the generated ordering is undesirable for a given application, it can be reordered using `MAP`.

# Simple Families

## `C[n]`: Cycle Graphs
The _cycle graph_ on _n_ vertices is (up to isomorphism) the graph composed of precisely one cycle of length _n_ and nothing else.
The vertex ordering is the natural one: sequential vertices arranged to be best plotted with a single-layer circular layout.

## `F[n]`: Friendship Graphs
The _friendship graph_ on _n_ vertices is the graph (up to isomorphism) such that every two vertices have exactly one neighbor in common.
The vertex ordering is such that the first vertex is adjacent to every other; this ordering befits a double-layer circular layout with the first vertex at the origin and the remaining vertices placed on the outer circle.

## `K[n]`: Complete Graphs
The _complete graph_ on _n_ vertices is (up to isomorphism) the graph with every possible edge. A complete graph is also called a _clique_.
The vertex ordering is the natural one: sequential vertices arranged to be best plotted with a single-layer circular layout.

## `S[n]:` Star Graphs
The _star graph_ on _n_ vertices is (up to isomorphism) the graph with one vertex that is the sole neighbor of every other vertex.
The vertex ordering is such that the first vertex is adjacent to all others; this ordering befits a double-layer circular layout with the first vertex at the origin and the remaining vertices placed on the outer circle.

# Complex Families

## `K[n1,n2,...]`: Multipartite Graphs
A _multipartite graph_ is a graph which can be partitioned into sets of size _n1,n2,..._ such that no vertices in the same set are adjacent (these are called _independent sets_ or _anticliques_).
The vertex ordering is such that the first _n1_ vertices are independent, then the next _n2_, and so on; this ordering befits a linear layout where each layer corresponds to an independent set (in particular avoiding overlapping edges since no layer contains adjacent vertices).

## `W[n,k]`: Windmill Graphs
A _windmill graph_ is a graph in which _n_ copies of the complete graph on _k_ vertices are connected so that they all share the same vertex in common; this vertex is called the _universal_ vertex.
The vertex ordering is such that the first vertex is the universal vertex; the vertices then proceed in groups of size _k-1_ corresponding to each of the connected complete graphs. This ordering befits a modified circular layout largely dependent on the choice of _n_ and _k_.
