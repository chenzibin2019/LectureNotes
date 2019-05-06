## Minimum Spanning Trees

> Some equations are not supported, PDF version [here](https://people.umass.edu/zibinchen/pdf/mst.pdf)

1. Minimum Spanning Tree

   - Spanning subgraph: Subgraph of G containing all the vertices of G

   - Spanning tree: Spanning subgraph that is itself a (free) tree

   - Minimum Spanning Tree (MST): Spanning tree of a weighted graph with minimum total edge weight.

2. Cycle property

   - Let T be a minimum spanning tree of a weighted graph G

   - Let e to be an edge of G that is not in T and let C be the cycle formed by e with T

   - For every edge f of C, weight(f) <= weight(e)

3. Partition property
   - Consider a partition of the vertices of G into subsets U and V

   - Let e be an edge of minimum weight across the partition

   - There is a minimum spanning tree of G containing edge e
4. Prim-Jarnik's Algorithm: Pick an arbitratory vertex s and we grow the MST as a cloud of vertices.

   ```java
   Algorithm PrimJarnikMST(G)
       Q = new heap-based priority queue;
       s = a vertex of G
       for all v in G.vertices():
           if v == s
               setDistance(v,0)
           else
               setDistance(v, infinate)
           setParent(v,NULL)
           l = Q.insert(getDistance(v), v)
           setLocator(v,l)
       while not Q.isEmpty():
           u = Q.removeMin();
           for all e in G.incidentEdge()
               z = G.opposite(u,e)
               r = weight(e)
               if r<getDistance(z)
                   setDistance(z,r)
                   setParent(z,e)
                   Q.replaceKey(getLocator(z), r)
   ```

   Analysis 
   - Method incidentEdge is called once for each vertex

   - We get/set distance, parent and locator labels vertex z  $O(deg(z))$ times. Setting/getting a label takes $O(1)$ time.

   - Prim-Jarnik's algorithm runs in $O((n+m)\log n)$ time provided the graph is represented by adjacency list. The running time is $O(m \log n)$ since the graph is connected.
5. Kruskal's Algorithm

   ```java
   Algorithm KruskalMST(G) 
       for each vertex V in G do
           define a Cloud(v) of {v}
       let Q be a priority queue.
       Insert all edges into Q using their weights as key.
       T = NULL
       while T has fewer than n-1 edges do
           edge e = T.removeMin()
           Let u,v to be the endpoints of e
           if Cloud(v) != Cloud(u) then
               Add edge e to T
               Merge Cloud(v) and Cloud(u)
       return T;
   ```
6. We need a ADT to store and operate on partitions (Cloud), 
   - find(u) - return the set storing u

   - union(u,v) - replace the sets storing u and v with their union

   - Each is stored in a sequence.

   - find(u) takes $O(1)$ and union(u,v) takes $O(min(n_u,n_v))$ times.
7. Baruvka's Algorithm: Running time $O(m\log n)$

   ```java
   Algorithm BaruvkaMST(G)
       T = V {V is vertices of G}
       while T has fewer than n-1 edges do
           for each connected componoents C in T do
               Let edge e be the smallest-weight edge from C to another component in T
               if e is not in T then
                   add e to T
       return T
   ```
8. Travel Salespersom (TSP):
   1. No polynomial time to solve this problem.
   2. Approximation algorithm
      - Compute a minimum spanning tree.

      - Form an Eulerian circuit around the MST

      - Transform the circuit into a tour.
