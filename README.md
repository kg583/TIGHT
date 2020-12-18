# TIGHT Package v1.0
TIGHT, or TI GrapH Theory, is a package of lists and programs designed for analyzing and plotting discrete graphs on the TI-83+ series of calculators. These programs are intended to be used as subprograms for larger projects, and are implemented to minimize variable use and overall memory footprint. TIGHT can support both directed and undirected graphs with up to 999 edges and 999 vertices, with a diverse array of graph algorithms and plotting options at your disposal.

# How to Use

To install, simply download and open the group `TIGHT`, or you may download/copy individual programs directly. All TIGHT programs are denoted by `θGT` followed by 2 or more characters. The current graph's edges are stored in `|LE`; most programs require this list to exist (even if it is empty) to function properly. Plotting and layout functions additionally require `|LX` and `|LY` to exist; `|LV` is required for graph search algorithms and plotting. All of these basic lists are included with the `TIGHT` group, initially empty.

# Vars
The following real variables and lists are defined for the graph upon creation and change as components of the graph are added and removed via the specified subprograms. Thus, they generally should _not_ be changed directly by the user during normal use, though modifying them in the course of user-designed algorithms may prove more efficient if done properly.

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
* `|LθGT1` - `|LθGT4`: Temporary lists

## Graph Lists
*	`C`: Color palette
	* Entries are BASIC colors (`BLUE` to `DARKGRAY`)
	* Plotting functions indexes the palette as specified (see `plot.md`)
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
		* `L`: Vertex label (usually an integer)
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
Most programs modify the graph in-place; any programs that return some graph without modifying the graph return only the edges.
Any returns stored in `Ans` upon completion are detailed in the corresponding program file.

Programs are divided into the following subdirectories, grouped according to general use cases and functions.
* `algos`: Graph algorithms that modify the graph, search for some desired vertex or edge, or compute some challenging characteristic
	* Ex: `KRUS`, which performs Kruskal's algorithm on the graph
* `base`: Programs that are rarely executed by themselves, being mostly used instead as succinct subprograms
	* Ex: `ARG`, which parses the string `Ans` into a list of arguments
* `calc`: Programs which calculate relatively simple graph characteristics, metrics, or outputs
	* Ex: `COMP`, which returns the complement of the graph if it is directed
* `graphs`: Programs involved with generating or importing existing graphs
	* Ex: `LOAD`, which loads an existing graph by name in `Ans`
* `label`: Graph algorithms which label the edges or vertices in some manner, most often as a coloring
	* Ex: `DEGS`, which labels each vertex based on its degree
* `matrix`: Programs which operate on or return matrices related to the graph
	* Ex: `ADJM`, which computes the adjacency matrix of the graph
* `ops`: Operations which modify the graph in-place
	* Ex: `ADD`, which adds the edge `Ans` to the graph
* `plot`: Programs involved with plotting the graph on the graphscreen
	* Ex: `LAY`, which lays out the vertices of the graph for plotting
* `test`: Tests which determine if the graph satisfies some desired property
	* Ex: `TREE`, which checks if the graph is a tree

# Contact
Have any questions? Found a bug?
Raise an issue on this repository or contact kg583 on TI-Basic Developer or Cemetech.

Copyright © Kevin Gomez 2020. All rights reserved.
