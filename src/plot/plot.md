# Plotting Guide

Use `PLOT` to plot each vertex of the graph using its layout coordinates (see `layout.md`) along with its edges. Plotting options are specified in `Ans` as a list of up to five numerical arguments. These arguments are parsed in a set order, with default values assumed if they are not provided. They are given as follows:

1. `scale`: A nonzero real number specifying the size of the plot within the graphing window
  * If `scale >= 1`, vertices may be plotted outside the graphing window
  * If `scale = 0`, no plotting will occur
  * If `scale < 0`, coordinates will be reflected about both axes
2. `vertex_shape`: An integer between 1 and 4 specifying the shape of each vertex (default = `2`)
  * If `vertex_shape = 0`, vertices are not plotted
  * If `vertex_shape = 1`, vertices are plotted as large dots
  * If `vertex_shape = 2`, vertices are plotted as open boxes
  * If `vertex_shape = 3`, vertices are plotted as crosses
  * If `vertex_shape = 4`, vertices are plotted as single pixels
3. `vertex_color`: A boolean value or BASIC color specifying how vertices are to be colored (default = `0`)
  * If `vertex_color = 0`, all vertices will be colored `BLACK`
  * If `vertex_color = 1`, vertices will be colored using the `|LC` palette indexed by vertex labels in `|LV`
  * If `vertex_color >= 10`, all vertices will be colored using the corresponding BASIC color
4. `edge_color`: A boolean value or BASIC color specifying how edges are to be colored (default = `0`)
  * If `edge_color = 0`, all edges will be colored `BLACK`
  * If `edge_color >= 10`, all edges will be colored using the corresponding BASIC color
5. `arrow_scale`: A real number specifying the relative size of arrows drawn on directed edges (default = `1`)
  * If `scale = 0`, no arrows will be drawn
