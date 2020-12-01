# Layout Guide

Use `LAY` to assign xy-coordinates to each vertex in the graph so that it can be plotted. Layout options are specified in `Ans`, and are of the form `"[char][args]"`, where `char` is a single character (`A` to `Z`, `θ`, or `π`) and `args` is a string of _n_ numeric arguments separated by commas. Several layout options are available for plotting graphs, roughly divided into two categories: static and dynamic.

The generated layouts always fall into the window `[~1,1] x [~1,1]`; subprograms such as `PLOT` then adjust the coordinates to the current graphing window dimensions.

# Static Layouts
Static layouts are fixed vertex locations that are calculated without taking edge density, clique size, planarity, or other factors into account. These layouts can be computed very quickly, but often require advanced knowledge of the graph's general shape to be useful.

## `C`: Circular Layout
A _circular layout_ is composed of _n_ equally-spaced concentric circles centered at the origin. Each argument specifies the number of vertices placed on each circle, with the sign and fractional part dictating the radial ordering (outward or inward) and relative scaling (`|E~14` to `1`) of the circle.

The arguments for a circular layout are parsed as `±(iPart + fPart)`:

* `iPart`: Number of vertices to place on the circle
  * Vertices increase consecutively from the top of the y-axis, proceeding counterclockwise
  * If `iPart = 1`, the vertex is mapped to the origin
* `1 - fPart`: Relative scaling of the circle
  * If `fPart = 0`, the circle's size is unchanged
* `sign`: Radial order of the circle relative to the previous
  * If `sign = 1`, the circle is appended to list of layers (so it appears outward from the previous)
  * If `sign = ~1`, the circle is prepended to the list of layers (so it appears inward from the previous)

## `L`: Linear Layout
A _linear layout_ is composed of _n_ equally-spaced horizontal lines aligned to the x-axis. Each argument specifies the number of vertices placed on each line, with the sign dictating the direction of the vertices along the line (left or right).

The arguments of a linear layout are parsed as `±iPart`:

* `iPart`: Number of vertices to place on the line
* `sign`: Direction of the vertices along the line
  * If `sign = 1`, the vertices increase from left to right
  * If `sign = ~1`, the vertices increase from right to left
* Each line is placed below the previous, so that vertices increase from top to bottom
