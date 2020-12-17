# Plotting Guide

Use `PLOT` to plot each vertex of the graph using its layout coordinates (see `layout.md`) along with its edges. Plotting options are specified in `Ans` as a list of up to five numerical arguments. These arguments are parsed in a set order, with default values assumed if they are not provided. They are parsed as follows:

1. `scale`: A nonzero real number specifying the size of the plot within the graphing window
	* If `scale >= 1`, vertices may be plotted outside the graphing window
	* If `scale = 0`, no plotting occurs
	* If `scale < 0`, coordinates are reflected about both axes
2. `vertex_shape`: An integer between 0 and 4 specifying the shape of each vertex (default = `2`)
	* If `vertex_shape = 0`, vertices are not plotted
	* If `vertex_shape = 1`, vertices are plotted as large dots
	* If `vertex_shape = 2`, vertices are plotted as open boxes
	* If `vertex_shape = 3`, vertices are plotted as crosses
	* If `vertex_shape = 4`, vertices are plotted as single pixels
3. `vertex_color`: An option or BASIC color specifying how vertices are to be colored (default = `0`)
	* If `vertex_color = 0`, all vertices are colored `BLACK`
	* If `vertex_color = 1`, vertices are colored using the palette indexed by vertex labels
	* If `vertex_color = 2`, vertices are colored using the palette indexed by vertex data
	* If `vertex_color >= 10`, all vertices are colored using the corresponding BASIC color
4. `edge_style`: An integer between 0 and 4 specifying the style of each edge (default = `2`)
	* If `edge_style = 0`, edges are not drawn
	* If `edge_style = 1`, edges have thin width
	* If `edge_style = 2`, edges have thick width
	* If `edge_style = 3`, edges are shaded above
	* If `edge_style = 4`, edges are shaded below
5. `edge_color`: An option or BASIC color specifying how edges are to be colored (default = `0`)
	* If `edge_color = 0`, all edges are colored `BLACK`
	* If `edge_color = 1`, edges are colored using the palette indexed by edge data
	* If `edge_color = 2`, edges are colored using the palette indexed by the incident vertex
	* If `edge_color = 3`, edges are colored using the palette indexed by the terminal vertex
	* If `edge_color = 4`, edges are colored using the palette indexed by the incident vertex label
	* If `edge_color = 5`, edges are colored using the palette indexed by the terminal vertex label
	* If `edge_color >= 10`, all edges will be colored using the corresponding BASIC color
6. `arrow_scale`: A real number specifying the relative size of arrows drawn on directed edges (default = `1`)
	* If `scale = 0`, no arrows are drawn

Note that any plotting options which index the palette do not necessarily check that such indices are valid.
