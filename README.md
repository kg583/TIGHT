# TIGHT Package v1.0
TIGHT, or TI GrapH Theory, is a package of lists and programs designed for analyzing and plotting discrete graphs on the TI-83+ series of calculators. These programs are intended to be used as subprograms for larger projects, and are implemented to minimize variable use and overall memory footprint. TIGHT can support both directed and undirected graphs with up to 999 edges and 999 vertices, with a diverse array of graph algorithms and plotting options at your disposal.

To install, simply download and open the group `TIGHT`, or you may download/copy individuals programs directly. All TIGHT programs are denoted by `θGT` followed by 2 or more characters. The current graph's edges are stored in `|LE` respectively; most programs require this list to exist (even if it ise empty) to function properly. Plotting and layout functions additionally require `|LX` and `|LY` to exist; `|LC` is required for graph coloring algorithms and plotting. All of these basic lists are included with the `TIGHT` group, initially empty.

# Vars
The following real variables and lists are defined for the current graph upon creation and change as components of the graph are added and removed via the specified subprograms. Thus, they generally should *not* be changed directly by the user during normal use, though modifying them in the course of user-designed algorithms may prove more efficient if done properly.

## Graph Characteristics
* `D`: Directedness
	* `-1`: Graph is directed
	* `0`: Graph is empty
	* `1`: Graph is undirected
* `E`: # of edges
* `V`: # of vertices

## Internal Vars
* `X,Y,Z,θ`: Real vars
* `|LGT`: Argument list
* `|LGT1`: Temporary list
* `|LGT2`: Temporary list

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
	* Entries are within the range `[-1,1]`
* `Y`: Vertex Y coordinates
	* Entries are within the range `[-1,1]`

## Premade Graphs
Premade graphs are stored as their edge lists; use `EXT` to extract the graph by name and set its graph characteristics.
* `BFLY`: The butterfly graph
* `BULL`: The bull graph
* `DIAM`: The diamond graph
* `DURER`: The Dürer graph
* `GOLOM`: The Golomb graph
* `PETER`: The Petersen graph

# Programs
Most programs modify the current graph in-place; any returns stored in `Ans` upon completion are detailed below.
* `ADD`: Adds the edge `Ans` to the graph; sets the weight of the edge to `imag(Ans)` if the edge already exists
	* Returns `E` in all cases
* `ARG`: Parses the input string `Ans` into separate arguments in `|LθGT`
	* Returns `|LθGT` in all cases
* `CLR`: Clears the graph
* `CLRW`: Clears all weights from the graph; does nothing if the graph is empty
* `CONT`: Contracts the edge `Ans` in the graph; does nothing if the edge does not exist or the graph is directed
	* Returns `V` in all cases
* `DEG`: Calculates the degree of the vertex `Ans`
	* Returns the out-degree if the graph is directed and the total degree otherwise
* `DEL`: Deletes the edge `Ans` from the graph; does nothing if the edge does not exist
  	* Returns `E` if the edge exists and zero otherwise
* `EXT`: Extracts the imported graph named in `Ans` to `|LE` and sets the graphs characteristics
	* Truncates `Ans` to at most five characters
	* Returns `V` in all cases
* `GEN`: Generates the graph family member named in `Ans`
* `HAS`: Checks if the edge `Ans` is in the graph
	* Returns the index of the edge if it exists and zero otherwise
* `MAP`: Maps the vertices of the graph to the vertex ordering `Ans`
	* May preserve duplicate edges for non-injective mappings
* `LAY`: Sets the `|LX` and `|LY` vertex coordinate lists for plotting using the specified layout method
* `PLOT`: Plots the graph using the `|LX` and `|LY` vertex coordinate lists, scaled by `Ans`; does nothing if `|LX` or `|LY` is empty
	* Colors vertices using `|LV` if possible; defaults to `BLACK` otherwise
	* Coordinate lists are mapped to the range `Ans * [Ymin,Ymax]` for plotting
* `RMV`: Identifies the largest vertex with the empty vertex `Ans`
	* May preserve duplicate edges if the vertex is not empty
	* Returns `V` in all cases
* `SUB`: Creates the induced subgraph on the vertices in `Ans`
	* Returns the edges of the subgraph in all cases

Have any questions? Found a bug?
Contact kg583 on TI-Basic Developer or Cemetech.

Copyright © Kevin Gomez 2020. All rights reserved.
