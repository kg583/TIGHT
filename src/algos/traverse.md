# Traversal Guide

Use `T` to traverse the graph using some specified heuristic and/or vertex ordering. The direct input to `T` is a single vertex in `Ans`, from which to start traversal; the traversal method is then specified by the function variable `|u`, called the _heuristic_. Choices of `|u` corresponding to common traversal methods are given here, as well as the general guidelines for designing custom heuristics. The return from `T` is a list of vertices accessible from the start in the order they were visited; ties in visit order are always broken numerically, with smaller vertices first.

### Greedy Search

Greedy search is a traversal algorithm which always favors the least-costly edge incident to a visited vertex, no matter how far from the start vertex it has traveled. Edge weights are used as the sole component of the heuristic.

To perform greedy search on the graph, use `|u = "imag(L1"`.

### Uniform-Cost Search

Uniform-cost search is a traversal algorithm which seeks to minimize total distance traveled along a path. Edge weights are used as the sole component of the heuristic.

To perform uniform-cost search on the graph, use `|u = "θ+imag(L1"`.

### A* Search

A\* search is a traversal algorithms which seeks to balance total distance traveled along a path and remaining distance to some goal vertex. Edge weights and vertex weights are combined for this heuristic.

To perform A\* search on the graph, use `|u = "θ+imag(L1)+seq(imag(|LV(Ans(Z))),Z,1,dim(Ans"`.
