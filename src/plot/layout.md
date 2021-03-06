# Layout Guide

Use `LAY` to assign xy-coordinates to each vertex in the graph so that it can be plotted (see `plot.md`). Layout options are specified in `Ans`, and are of the form `"[char][args]"`, where `char` is a single character (`A` to `Z`, `θ`, `pi`, `~`, or `0` to `9`) and `args` is a string of _n_ numeric arguments separated by commas. Several layout options are available for plotting graphs, roughly divided into two categories: static and dynamic.

The generated layouts always fall into the window `[~1,1] x [~1,1]`; subprograms such as `PLOT` then adjust the coordinates to the current graphing window dimensions.

# Static Layouts
Static layouts are fixed vertex locations that are calculated without taking edge density, clique size, planarity, or other factors into account. These layouts can be computed very quickly, but often require advanced knowledge of the graph's general shape to be useful.

## `C`: Circular Layout
A _circular layout_ is composed of _n_ equally-spaced concentric circles centered at the origin. Each argument specifies the number of vertices placed on each circle, with the sign and fractional part dictating the radial ordering (outward or inward) and relative scaling (`~0` to `1`) of the circle.

The arguments for a circular layout are parsed as `±(iPart + fPart)`:

* `iPart`: Number of vertices to place on the circle
  * Vertices increase consecutively from the top of the y-axis, proceeding counterclockwise
  * If `iPart = 1`, the vertex is mapped to the origin
* `1 - fPart`: Relative scaling of the circle
  * If `fPart = 0`, the circle's size is unchanged
  * If `fPart ~ 1`, the circle's size is arbitrarily small
* `sign`: Radial order of the circle relative to the previous
  * If `sign = 1`, the circle is appended to list of layers (so it appears outward from the previous)
  * If `sign = ~1`, the circle is prepended to the list of layers (so it appears inward from the previous)

## `L`: Linear Layout
A _linear layout_ is composed of _n_ equally-spaced horizontal lines aligned to the x-axis. Each argument specifies the number of vertices placed on each line, with the sign dictating the direction of the vertices along the line (left or right).

The arguments for a linear layout are parsed as `±(iPart + fPart)`:

* `iPart`: Number of vertices to place on the line
* `fPart`: Relative inward offset on the line
  * If `fPart = 0`, the vertices are placed exactly evenly on the line
  * If `fPart ~ 1`, the vertices are placed halfway toward the center of the line
* `sign`: Direction of the vertices along the line
  * If `sign = 1`, the vertices increase from left to right
  * If `sign = ~1`, the vertices increase from right to left
* Each line is placed below the previous, so that vertices increase from top to bottom

## `O`: Orbital Layout
An _orbital layout_ is composed of _n_ circles of varying sizes arranged around a central circle. Each argument specifies the number of vertices in each orbiting circle, with the sign and fractional part dictating the ordering (clockwise or counterclockwise) and relative scaling (`~0` to `1`) of each circle. A singular first argument, a real number, sets the scale of the central circle.

The remaining arguments for an orbital layout are parsed as `±(iPart + fPart)`:

* `iPart`: Number of vertices in the orbiting circle
* `1 - fPart`: Relative scaling of the orbiting circle
  * If `fPart = 0`, the circle's size is unchanged
  * If `fPart ~ 1`, the circle's size is arbitrarily small
* `sign`: Radial order of the orbiting circle relative to the previous
* If `sign = 1`, the circle is appended to list of orbits (so it appears counterclockwise from the previous)
* If `sign = ~1`, the circle is prepended to the list of orbits (so it appears clockwise from the previous)

## `T`: Binary Tree Layout
A _binary tree layout_ is composed of equally-spaced horizontal tiers aligned to the x-axis, each corresponding to a different vertex depth within a binary tree. The single argument specifies the number of vertices in the tree, with the sign dictating the direction of the tree (growing downward or upward).

The argument for a binary tree layout is parsed as `±iPart`:

* `iPart`: Number of vertices in the entire tree
* `sign`: Direction of the tree
  * If `sign = 1`, vertex depth increases downward
  * If `sign = ~1`, vertex depth increases upward

# Dynamic Layouts
Dynamic layouts are calculated in a manner dependent on the current graph, most often the graph's edge density, clustering of vertices, or overall composition as a combination of many simpler graphs; additional input parameters allow the user to tweak how these elements are considered when creating the layout. These layouts are much more intensive to compute than static layouts, but are adaptable to many types of graphs and do not require as much advanced knowledge of the graph's shape and structure.
