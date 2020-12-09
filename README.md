# TIGHT Package v1.0
TIGHT, or TI GrapH Theory, is a package of lists and programs designed for analyzing and plotting discrete graphs on the TI-83+ series of calculators. These programs are intended to be used as subprograms for larger projects, and are implemented to minimize variable use and overall memory footprint. TIGHT can support both directed and undirected graphs with up to 999 edges and 999 vertices, with a diverse array of graph algorithms and plotting options at your disposal.

# How to Use

To install, simply download and open the group `TIGHT`, or you may download/copy individual programs directly. All TIGHT programs are denoted by `θGT` followed by 2 or more characters. The current graph's edges are stored in `|LE`; most programs require this list to exist (even if it is empty) to function properly. Plotting and layout functions additionally require `|LX` and `|LY` to exist; `|LV` is required for graph search algorithms and plotting. All of these basic lists are included with the `TIGHT` group, initially empty.

# Vars
The following real variables and lists are defined for the current graph upon creation and change as components of the graph are added and removed via the specified subprograms. Thus, they generally should _not_ be changed directly by the user during normal use, though modifying them in the course of user-designed algorithms may prove more efficient if done properly.

## Graph Characteristics
* `D`: Directedness
	* `-1`: Graph is directed
	* `0`: Graph is empty
	* `1`: Graph is undirected
* `E`: # of edges
* `V`: # of vertices

## Internal Vars
* `X,Y,Z,θ`: Real vars
* `|LθGT`: Argument list
* `|LθGT1`: Temporary list
* `|LθGT2`: Temporary list

## Graph Lists
*	`C`: Color palette
	* Entries are BASIC colors (`BLUE` to `DARKGRAY`)
	* Plotting function indexes the palette using vertex labels
* `E`: Edges
	* Entries are `±(I + T|E~3) + W[i]`
		* `I`: Initial vertex (`001` to `999`)
		* `T`: Terminal vertex (`001` to `999`)
		* `W`: Edge weight (any real number)
	* Sign is negative if directed, positive if undirected
		* All edges have the same sign (i.e. directed and undirected edges are not mixed)
	* Contains no duplicate edges
		* For undirected graphs, the initial vertex is always the minimum of the two vertices
* `V`: Vertices
	* Entries are `L + D[i]`
		* `L`: Vertex label
		* `D`: Vertex data (any real number)
	* Sign and fractional part of real part can be set arbitrarily by the user
		* All subprograms ignore these components of vertex entries
	* If a vertex contains no entry, it is assumed to be uncolored and have no associated data
* `X`: Vertex X coordinates
	* Entries are within the range `[~1,1]`
* `Y`: Vertex Y coordinates
	* Entries are within the range `[~1,1]`

## Premade Graphs
Premade graphs are stored as their edge lists; use `LOAD` to extract the graph by name and set its graph characteristics.
A list of premade graphs is given in `graphs.md`; all premade graphs are saved in the group `TIGHTGDB`.

# Programs
Most programs modify the current graph in-place; any returns stored in `Ans` upon completion are detailed below.
* `ADD`: Adds the edge `Ans` to the graph; sets the weight of the edge to `imag(Ans)` if the edge already exists
	* Returns `E` in all cases
* `ADJ`: Computes the adjacency matrix of the graph in `[A]`
* `ARG`: Parses the input string `Ans` into separate arguments in `|LθGT`
	* Returns `|LθGT` in all cases
* `BFS`: Performs a breadth-first search of the graph for vertex label `Ans(1)` beginning at the vertex `Ans(2)`
	* If not provided, the search will begin at the first vertex
	* Labels the vertices in `|LV` based on whether they have been visited
	* Returns the vertex with `Ans(1)` as its label
* `CLR`: Clears the graph
* `CLRW`: Clears all weights from the graph; does nothing if the graph is empty
* `COMP`: Computes the complement of the graph
	* Returns the complement edges in all cases
* `DEG`: Calculates the degree of the vertex `Ans`
	* Returns the out-degree if the graph is directed and the total degree otherwise
* `DEL`: Deletes the edge `Ans` from the graph; does nothing if the edge does not exist
	* Returns `E` if the edge exists and zero otherwise
* `DFS`: Performs a depth-first search of the graph vertex label `Ans(1)` beginning at the vertex `Ans(2)`
	* If not provided, the search will begin at the first vertex
	* Labels the vertices in `|LV` based on whether they have been visited
	* Returns the vertex with `Ans(1)` as its label
* `E`: Computes the edge that would connect vertices `X` and `Y` given the directedness of the graph
	* Returns the desired edge in all cases
* `ES`: Lists the edges adjacent to the vertex `Ans` ordered by the current edge ordering
	* Returns the adjacent edges (may be none)
* `GEN`: Generates the graph family member named in `Ans`
	* Generation options are given in `gen.md`
* `HAS`: Checks if the edge `Ans` is in the graph
	* Returns the index of the edge if it exists and zero otherwise
* `KREG`: Checks if the graph is regular
	* Returns the valency of the graph if it is regular and zero otherwise
* `LAY`: Sets the `|LX` and `|LY` vertex coordinate lists for plotting using the specified layout method
	* Layout options are given in `layout.md`
* `LOAD`: Extracts the saved graph named in `Ans` to `|LE` and sets the graphs characteristics
	* Truncates `Ans` to at most five characters
	* Returns `V` in all cases
* `MAP`: Maps the vertices of the graph to the vertex ordering `Ans`
	* May preserve duplicate edges for non-injective mappings
* `PLOT`: Plots the graph using the `|LX` and `|LY` vertex coordinate lists, scaled by `Ans`; does nothing if `|LX` or `|LY` is empty
	* Colors vertices using `|LV` if possible; defaults to `BLACK` otherwise
	* Coordinate lists are mapped to the range `Ans * [Ymin,Ymax]` for plotting
* `RMV`: Identifies the largest vertex with the empty vertex `Ans`
	* May preserve duplicate edges if the vertex is not empty
	* Returns `V` in all cases
* `SORT`: Sorts the edges of the graph by edge weight
* `SPAN`: Computes a spanning forest for the graph based on the current edge ordering
	* Labels the vertices in `|LV` based on their tree within the forest
	* Returns the edges of the spanning forest
* `STO`: Stores the edge list `Ans` into `|LE` and sets the graph characteristics
* `SUB`: Creates the induced subgraph on the vertices in `Ans`
	* Returns the edges of the subgraph if it is non-empty
* `TO`: Checks if the vertices `X` and `Y` are adjacent
	* Returns the index of the connecting edge if it exists and zero otherwise
* `V`: Computes the number of vertices in the graph
	* Returns `V` in all cases
* `VS`: Lists the vertices adjacent to the vertex `Ans` ordered by the current edge ordering
	* Returns the adjacent vertices (may be none)

# Contact
Have any questions? Found a bug?
Raise an issue on this repository or contact kg583 on TI-Basic Developer or Cemetech.

Copyright © Kevin Gomez 2020. All rights reserved.
