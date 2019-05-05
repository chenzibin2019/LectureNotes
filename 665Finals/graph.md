## Graph

> Some equations are not supported, PDF version [here](https://people.umass.edu/zibinchen/pdf/graph.pdf)

1. A graph is a pair of (V, E), where V is a set of nodes, called vertices, E is a collection of pairs of vertices called edges. Vertices and edges are positions and store elements.

2. Edge Types:

   1. Directed edge: Ordered pair of vertices (u,v), first vertix u is the origin and second vertix v is destination.

   2. Undirected edge: unorderd pair of vertices (u,v).

   3. Directed graph: all the edges are directed. Undirected graph: all the edges are ungirected.

3. Terminology:

   1. End vertices (or endpoints) of a edge: edges on two ends of a edge.

   2. Edges incident on a vertex: all the edges that connected to a vertix.

   3. Adjacent vertices: vertices that are connected with one edge.

   4. Degree of a vertex: numbers of edges connected to the vertex.

   5. Parallel edges: have same end vertices.

   6. Self-loop: start = end.

   7. Path: sequence of alternating vertices and edges.

   8. Simple path: path that all its vertices and edges are distinct.

   9. Cycle: circular sequence of alternating vertices and edges.

   10. Simple cycle: cycle such that all its vertices and edges are distinct.

4. Properities

   > Notation: n => number of vertices, m => number of edges, deg(v) => degree of vertex v

   1. $\sum(v)=2m$

   2. In an undirected graph with no self-loops and no multiple edges:

$$
m \le \frac{n(n-1)}{2}
$$

5. ADT

   1. Adjacency List: pointers...

   2. Adjacency Matrix: Matrix...

6. Performance

   | n verties, m edges | Edge List | Adjacency List     | Adjacency Martix |
   | ------------------ | --------- | ------------------ | ---------------- |
   | Space              | n+m       | n+m                | $n^2$            |
   | invidentEdge(v)    | m         | deg(v)             | n                |
   | areAdjacent(v,w)   | m         | min(deg(v),deg(w)) | 1                |
   | insertVertex(o)    | 1         | 1                  | $n^2$            |
   | insertEdge(v,w,o)  | 1         | 1                  | 1                |
   | removeVertix(v)    | m         | deg(v)             | $n^2$            |
   | removeEdge(e)      | 1         | 1                  | 1                |

7. 
