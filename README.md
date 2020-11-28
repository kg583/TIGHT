# TIGHT Package v1.0
TIGHT, or TI GrapH Theory, is a package of lists and programs designed for analyzing and plotting discrete graphs on the TI-83+ series of calculators. These programs are intended to be used as subprograms for larger projects, and are implemented to minimize variable use and overall memory footprint. TIGHT can support both directed and undirected graphs with up to 999 edges and 999 vertices, with a diverse array of graph algorithms and plotting options at your disposal.

To install, simply download and open the group `TIGHT`, or you may download/copy individuals programs directly. All TIGHT programs are denoted by `θGT` followed by 2 or more characters. The current graph's edges are stored in `|LE` respectively; most programs require this list to exist (even if it ise empty) to function properly. Plotting and layout functions additionally require `|LX` and `|LY` to exist; `|LC` is required for graph coloring algorithms and plotting. All of these basic lists are included with the `TIGHT` group, initially empty.

# Vars
The following real variables and lists are defined for the current graph upon creation and change as components of the graph are added and removed via the specified subprograms. Thus, they generally should *not* be changed directly by the user during normal use, though modifying them in the course of user-designed algorithms may prove beneficial if done properly.

## Graph Characteristics
* `D`: Directedness
	* `-1`: Graph is directed
	* `0`: Graph is empty
	* `1`: Graph is undirected
* `E`: # of edges
* `V`: # of vertices

## Internal Vars
* `X`: Initial vertex or counter
* `Y`: Terminal vertex or loop var
* `Z`: Input vertex or edge

## Graph Lists
* `C`: Colors
	* Entries are BASIC colors (`BLUE` to `DARKGRAY`)
* `E`: Edges
	* Entries are `±(I + T|E~3) + W[i]`
		* `I`: Initial vertex (`001` to `999`)
		* `T`: Terminal vertex (`001` to `999`)
		* `W`: Edge weight (any real number)
	* Sign is negative if directed, positive if undirected
		* All edges have the same sign (i.e. directed and undirected edges are not mixed)
	* Contains no duplicate edges
		* For undirected graphs, the initial vertex is always the minimum of the two vertices
* `X`: Vertex X coordinates
	* Entries are relative to graphing window (see `LAY`)
* `Y`: Vertex Y coordinates
	* Entries are relative to graphing window (see `LAY`)

## Premade Graphs
Premade graphs are stored as their edge lists; use `EXT` to extract the graph by name and set the graph characteristics.
* `PETER`: The Petersen graph

# Programs
Most programs modify the current graph in-place; any returns stored in `Ans` upon completion are detailed below.
* `ADD`: Adds the edge `Ans` to the graph; sets the weight of the edge to `imag(Ans)` if the edge already exists
	* Returns `E` in all cases
* `CLR`: Clears the graph
* `CLRW`: Clears all weights from the graph
* `CONT`: Contracts the edge `Ans` in the graph; does nothing if the edge does not exist or the graph is directed
	* Returns `V` in all cases
* `DEG`: Calculates the degree of the vertex `Ans`
	* Returns the out-degree if the graph is directed and the total degree otherwise
* `DEL`: Deletes the edge `Ans` from the graph; does nothing if the edge does not exist
  * Returns `E` if the edge exists and zero otherwise
* `EXT`: Extracts the imported graph named in `Ans` to `|LE` and sets the graphs characteristics
* `GEN`: Generates the specified graph family
* `HAS`: Checks if the edge `Ans` is in the graph
	* Returns the index of the edge if it exists and zero otherwise
* `ID`: Identifies the largest vertex with the vertex `Ans`
	* Returns `V` in all cases
* `LAY`: Sets the `|LX` and `|LY` vertex coordinate lists for plotting using the specified layout method
* `PLOT`: Plots the graph using the `|LX` and `|LY` vertex coordinate lists and the `|LC` vertex color list (if it exists); does nothing if `|LX` or `|LY` is empty

Have any questions? Found a bug?
Contact kg583 on TI-Basic Developer or Cemetech.

Copyright © Kevin Gomez 2020. All rights reserved.
