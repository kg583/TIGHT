# Sorting Guide

Use `SORT` to sort the edges of the graph based on some desired ordering. Sorting options are specified in `Ans` as a single numeric argument; the argument is parsed as `±iPart`:

* `iPart`: The type of sort to perform
  * If `iPart = 0`, edges are ordered randomly
  * If `iPart = 1`, edges are sorted by weight
  * If `iPart = 2`, edges are sorted by initial then terminal vertex
  * If `iPart = 3`, edges are sorted by terminal then initial vertex
  * If `iPart = 4`, edges are sorted by initial vertex label (assumed to exist)
  * If `iPart = 5`, edges are sorted by terminal vertex label (assumed to exist)
* `sign`: The directionality of the sort
  * If `sign = 1`, edges are sorted in ascending order
  * If `sign = ~1`, edges are sorted in descending order
