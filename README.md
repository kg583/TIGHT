# TIGHT Package v1.0
TIGHT, or TI GrapH Theory, is a package of lists and programs designed for analyzing and plotting discrete graphs on the TI-83+ series of calculators. These programs are designed to be used as subprograms for larger projects, and are implemented to minimize variable use and overall memory footprint. TIGHT can support both directed and undirected graphs with up to 999 edges and 999 vertices, with a diverse array of graph algorithms and plotting options at your disposal.

To install, simply download and open the group TIGHT, or you may download/copy individuals programs directly. All TIGHT programs are denoted by θGT followed by 2 or more characters. The current graph's edges and vertices are stored in |LE and |LV respectively; most programs require both lists to exist (even if they are empty) to function properly. Plotting and layout functions additionally require |LC, |LX, and |LY to exist. All of these basic lists are included with the TIGHT group, initially empty.

# Vars
The following real variables and lists are defined for the current graph upon creation. They generally should *not* be changed directly by the user during normal use.

## Graph Characteristics
* `D`: Directedness
  * `0`: Graph is undirected
  * `1`: Graph has vertices but no edges
  * `2`: Graph is directed
* `E`: # of edges
* `V`: # of vertices

## Graph Lists
* `E`: Edges
* `V`: Vertices

## Program Vars
* `X`: Initial vertex
* `Y`: Terminal vertex or loop var
* `Z`: Edge

## Premade Graphs
* `PETER`: The Petersen Graph

# Programs
Most programs modify the current graph in-place; the value of `Ans` upon completion is detailed below. Any additional returns are denoted in parentheses.
* `ADDE`: Adds the edge `Ans` to the graph; sets the weight of the edge to `imag(Ans)` if it already exists
  * Returns `E` in all cases
* `ADDV`: Adds the vertex `Ans` to the graph; sets the color of the vertex to `imag(Ans)` if it already exists
  * Returns `V` in all cases
* `CLR`: Clears the graph
  * Returns `Ans` unmodified
* `CLRW`: Clears all weights and colors from the graph
  * Returns `|LV` in all cases
* `CONT`: Contracts the edge `Ans` in the graph
  * Returns `E` if the graph has at least one edge
  * Returns `Ans` unmodified otherwise
* `DELE`: Deletes the edge `Ans` from the graph; does nothing if the edge does not exist
  * Returns `E` if the edge exists
  * Returns `Ans` unmodified otherwise
* `DELV`: Deletes the vertex `Ans` and all edges containing it from the graph; does nothing if the vertex does not exist
  * Returns `V` if the vertex exists
  * Returns `Ans` unmodified otherwise
* `GEN`: Generates the specified graph family
* `HASE`: Returns the index of the edge `Ans` if it exists and zero otherwise
* `HASV`: Returns the index of the vertex `Ans` if it exists and zero otherwise

Have any questions? Found a bug?
Contact kg583 on TI-Basic Developer or Cemetech.

Copyright © Kevin Gomez 2020. All rights reserved.
