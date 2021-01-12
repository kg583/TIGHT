# Premade Graphs

The following graphs are saved in the group `TIGHTGDB`. These graphs are notable for special properties they satisfy or results they support or deny, and are unlikely to be spotted in the wild or find much use in more computational applications. Nevertheless, you may find them interesting ways to verify algorithms, test out conjectures, or show off how cool graphs can be (because many of these graphs look very pretty). The suggested layout method for each graph is included, along with a few facts about each one.

Extract the graph by name via `LOAD` to load its edge list and set its graph characteristics. If there's a famous graph you can't find here, see if you can generate it using `GEN`; if it's still out of reach, raise an issue on this repository to request the graph's addition to the database, or make a pull request to add it yourself.

## Cage Graphs
* `C36`: The Heawood graph
  * Layout: `C[14]`
  * A symmetric graph used in the construction of a regular tiling of torus into seven mutually-adjacent regions
* `C37`: The McGee graph
  * Layout: `C[24]`
  * The smallest cubic graph that requires at least eight crossings when drawn in the plane
* `C45`: The Robertson graph
  * Layout: `C[19]`
  * A Hamiltonian graph with 5,376 distinct Hamiltonian cycles

## Small Named Graphs
* `BULL`: The bull graph
  * Layout: `C[3,2]`
  * A small self-complementary graph with relevance to the strong perfect graph theorem and the Erdős-Hajnal conjecture
* `CHVAT`: The Chvátal graph
  * Layout: `C[8,4]`
  * A triangle-free quartic graph with relevance to many conjectures concerning graph coloring and Hamiltonian cycles
* `DYCK`: The Dyck graph
  * Layout: `C[8,8,8,8]`
  * The only cubic symmetric graph on 32 vertices
* `FRANK`: The Franklin graph
  * Layout: `C[12]`
  * A triangle-free cubic graph which disproves Heawood's conjecture on the coloring of cells on an orientable surface
* `HOLT`: The Holt Graph
  * Layout: `C[18,9]`
  * A Hamiltonian graph that is edge-transitive and vertex-transitive but not symmetric
* `MOSER`: The Moser spindle
  * Layout: `L[1,4,2.5]`
  * The smallest unit-distance graph requiring at least four colors in any coloring
* `PAPPU`: The Pappus graph
  * Layout: `C[6,6,6]`
  * The only cubic symmetric graph on 18 vertices
* `SOUSS`: The Sousselier graph
  * Layout: `C[1,15]`
  * The first hypohamiltonian graph to be studied, which gave rise to an infinite family of such graphs

## Large Named Graphs

## Snarks
* `BLAN1`: The first Blanuša snark
  * Layout: `C[1,17]`
  * A cubic graph that was also the second snark ever discovered
* `BLAN2`: The second Blanuša snark
  * Layout: `C[2.9,3.5,2.9,4,2.9,3.5,2.9]`
  * The close successor to the first Blanuša snark, having the same number of vertices and edges

## Strongly Regular Graphs
* `CLEBS`: The Clebsch graph
  * Layout: `C[8,8]`
  * A quintic graph used to compute the Ramsey number `R(3,3,3)` by partitioning the complete graph `K[16]`
* `SHRIK`: The Shrikhande graph
  * Layout: `C[8,8]`
  * A sextic graph that describes the Whitney triangulation of the torus



## Polyhedral Graphs
* `BIDIA`: The Bidiakis cube
  * Layout: `C[12]`
  * A cubic Hamiltonian graph that forms the skeleton of a cube
* `GOLOM`: The Golomb graph
  * Layout: `C[1,6,3]`
  * A graph that demonstrates that at least four colors are required to color points in the plane at unit distance
* `HERSC`: The Herschel graph
  * Layout: `L[1,2.9,5,2.9,1]`
  * The skeleton of a enneahedron which is the smallest convex polyhedron without a Hamiltonian cycle
* `ICOSA`: Skeleton of the icosahedron
  * Layout: `C[3,6,3]`
  * A graph that also forms the skeleton of other polyhedra such as the great dodecahedron
