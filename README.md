# TIGHT Package v0.5
`TIGHT`, or TI GrapH Theory, is a package of lists and programs designed for analyzing and plotting discrete graphs on the TI-83+ series of calculators. These programs are intended to be used as subprograms for larger projects, and are implemented to minimize variable use and overall memory footprint. `TIGHT` can support both directed and undirected graphs with up to 999 edges and 999 vertices, with a diverse array of graph algorithms and plotting options at your disposal.

## Design Philosophy

`TIGHT` is designed to be the closest TI-BASIC imitation possible of a library or package you might use with Java, Python, C++, or any other mainstream computer language to analyze discrete graphs. While severely limiting in its capabilities, TI-BASIC is an easy-to-learn and easy-to-use language that is often the first language younger students ever encounter. Many who discover TI-BASIC often use it write some very simple programs to trick their friends or solve some math problems and leave it at that, but a decent proportion develop a greater interest in the language and programming in general. An even smaller proportion stick with BASIC even after they've learned a proper computer language, perhaps enamored with its quirks or challenged by its inherent limits.

At any rate, the community of BASIC users often push the limits of what is possible within the bounds of their language, even if the products are frankly unreasonable or flat-out useless. I am no different; `TIGHT` _cannot_ and _will not_ be used to accomplish academic research, analyze massive transport networks, or find a [non-5-colorable unit distance graph](https://en.wikipedia.org/wiki/Hadwiger%E2%80%93Nelson_problem). But, hopefully, it _will_ be used by casual programmers, TI-BASIC enthusiasts, and even budding mathematicians to learn more about graph theory first-hand. It doesn't take much to create graphs, analyze their basic properties, and write graph algorithms using `TIGHT`; with BASIC being a pretty simple language in its own right, and the TI-83+ series of calculators being a near necessity for every high school student in the United States and (portions of) Europe, `TIGHT` is arguably one of the most accessible graph theory libraries in existence.

But enough philosophical flaunting. As to how `TIGHT` is actually _written_ as a package, there are a few core principles
* Emulate a functional paradigm within programs by using `Ans` and other temporary variables
	* TI-BASIC does _not_ support return values nor function parameters (or really functions at all), so `Ans` has to make do
	* It isn't too challenging to write code that _behaves_ like functions, and provides a nice imperative structure for the user
* Emulate an object-oriented paradigm overall by treating graphs as objects with attributes
	* There are only two real data structures in TI-BASIC: the list and the matrix
	* In this vein, graphs are stored as their edge lists, with attributes maintained via global variables
	* This requires the user to assume the global variables are not tampered with, but beyond that the paradigm is quite useful
* Encourage user design principles by example in each and every program
	* Basically, practice what you preach, notably the importance of _modular_ program design
	* Programs in `TIGHT` call each other regularly to avoid redundancy and allow for easy adjustments to algorithms and code flow
	* Check out the `callgraph` to see how the programs interact
* Provide as many different tools for effective problem-solving as possible
	* Being a package, `TIGHT` contains mostly low-level subprograms that the user can chain together (with some exceptions)
	* You can't include every algorithm known to man, so `TIGHT` provides a variety of methods for the user to make what they need

as well as some general guidelines for producing useful code
* Preserve as many global variables as possible within a given program
	* There are only 27 real vars to go around, so don't hog them all!
* Avoid variable shuffling whenever possible
	* Saves times, saves bytes, and saves mental struggles to trace the code
* Hold program speed and size at near-equal importance
	* `TIGHT` has three limits: the size of graphs, the size of RAM, and the speed of TI-BASIC; none of these are very great

which all serve to create a simple, efficient, and easy-to-use TI-BASIC package. So, if you want to contribute to `TIGHT`, keep these principles in mind when writing your code. As far as I can tell, they're for the better.

# How to Use

To use `TIGHT` in your programs, simply call the desired subprogram, with the specified input preceding it by a single `:`. Multiple subprograms can be chained together, often not requiring any user-made code to properly pipe inputs and outputs from one another. The user can, of course, manipulate these inputs and outputs however they wish for their task.

For example, here is a simple snippet that plots the uncolored [Petersen graph](https://en.wikipedia.org/wiki/Petersen_graph) on the graphscreen
```
"PETER":prgmθGTLOAD		// Load the Petersen graph from the premade database (see graphs.md)
"C5,5":prgmθGTLAY		// Layout the vertices in two concentric circles (see layout.md)
{.9:prgmθGTPLOT			// Plot the graph at 90% scaling (see plot.md)
```
which produces the following image:

![The Petersen Graph](https://cdn.discordapp.com/attachments/519366929065050130/783408005168234526/unknown.png)

## Installation

To install, simply download and open the group `TIGHT`, or you may download/copy individual programs directly. All TIGHT programs are denoted by `θGT` followed by 2 or more characters. The current graph's edges are stored in `|LE`; most programs require this list to exist (even if it is empty) to function properly. Plotting and layout functions additionally require `|LC`, `|LX`, and `|LY` to exist; `|LV` is required for graph search algorithms and plotting. All of these basic lists are included with the `TIGHT` group, initially empty.

## Wiki

A wiki for this repository is coming soon.

# Vars
The following real variables and lists are defined for the graph upon creation and change as components of the graph are added and removed via the specified subprograms. Thus, they generally should _not_ be changed directly by the user during normal use, though modifying them in the course of user-designed algorithms may prove more efficient if done properly.

## Graph Characteristics
* `D`: Directedness
	* `-1`: Graph is directed
	* `1`: Graph is undirected
* `E`: # of edges
* `V`: # of vertices
* `W`: Weightedness
	* `0`: Graph is unweighted (or has all zero weights)
	* `1`: Graph is weighted (has at least one nonzero weight)

## Internal Vars
* `X,Y,Z,θ`: Real vars
* `L6`: Argument list
* `L1` - `L5`: Temporary lists

## Graph Lists
*	`C`: Color palette
	* Entries are TI colors (`BLUE` to `DARKGRAY`)
	* Plotting functions index the palette as specified (see `plot.md`)
* `E`: Edges
	* Entries are `±(I + T|E~3) + W[i]`
		* `I`: Initial vertex (`001` to `999`)
		* `T`: Terminal vertex (`001` to `999`)
		* `W`: Edge weight (any real number strictly between `~|E48` and `|E48`)
	* Sign is negative if directed, positive if undirected
		* All edges have the same sign (i.e. directed and undirected edges are not mixed)
	* Contains no duplicate edges
		* For undirected graphs, the initial vertex is always the minimum of the two vertices
* `M`: Marks
	* Entries are `M`
		* `M`: Vertex or edge mark (usually an integer)
	* Set during any graph traversal call to denote visited vertices
	* Not guarnateed to exist
* `V`: Vertices
	* Entries are `L + W[i]`
		* `L`: Vertex label (usually an integer)
		* `W`: Vertex weight (any real number strictly between `~|E48` and `|E48`)
	* Sign and fractional part of real part can be set arbitrarily by the user
		* All subprograms ignore, but do not necessarily respect, these components of vertex entries
	* Not guaranteed to exist
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
	* Ex: `KRUS`, which performs [Kruskal's algorithm](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm) on the graph
* `base`: Programs that are rarely executed by themselves, being mostly used instead as succinct subprograms
	* Ex: `A`, which parses the string `Ans` into a list of arguments
* `calc`: Programs which calculate relatively simple graph characteristics, metrics, or outputs
	* Ex: `COMP`, which returns the complement of the graph
* `graphs`: Programs involved with generating or importing existing graphs
	* Ex: `LOAD`, which loads an existing graph by name in `Ans`
* `label`: Graph algorithms which label the edges or vertices in some manner, most often as a coloring
	* Ex: `DEGL`, which labels each vertex based on its degree
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

Copyright © Kevin Gomez 2022. All rights reserved.
