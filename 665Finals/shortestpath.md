## Shortest Path

> Some equations are not supported, PDF version [here](https://people.umass.edu/zibinchen/pdf/shortestpath.pdf)

1. Shortest path problem : Given a weighted graph and two vertices u and v, we want to find a path of minmum total weight between u and v. (Length of a path is the sum of the weights of its edges)

2. Shortest path properties: 

   - A subpath of a shotest path itself is a shortest path.

   - There is a tree of shortest paths from a start vertex to all the pther vertices.

3. Dijkstra's Algorithm

   - The distance of a vertex v from a vertex s is the length of the shortest path between a and v

   - Dijkstra's Algorithm computes the distances of al the vertices from a given start vertex s

   - Assumptions:

     - The graph is connected

     - The edges are undirected

     - The edge weights are non-negative

   - We grow a "cloud" of vertices, beginning with s and eventually covering all the vertices

   - We store with each vertexv a label d(v) representing the distance of v from s in the subgraph consisting of the cloud and its adjacent vertices.

4. Edge relaxation

   Consider an edge $e=(u,z)$ such that u is the vertex that most recently added to the cloud, z is not in the cloud. The relaxation of edge e updates distance $d(z)$ as follows:

$$
d(z)=min \left \{ d(z), d(u) + weight(e)\right \}
$$

5. Dijkstra's Algorithm  Run $O((n+m) \log n)$ time

   ```java
   Algorithm DijkstraDistance(G,s) 
       Q = new heap-based priority queue
       for all v in G.vertices()
           if v == s
               setDistance(v, 0)
           else 
               setDistance(v. infinity)
           l = Q.insert(getDistance(v), v)
           setLocator(v, l)
       while !Q.isEmpty() 
           u = Q.removeMin()
           for all e in G.incidentEdges(u)
               z = G.opposite(u,e)
               r = getDistance(u) + weight(e)
               if r<getDistance(z)
                   setDistance(z, r)
                   Q.replaceKey(getLocator(z), r)
   ```

6. If you want to get a tree...

   ```java
   Algorithm DijkstraDistance(G,s) 
       Q = new heap-based priority queue
       for all v in G.vertices()
           setParent(v, NULL)
           if v == s
               setDistance(v, 0)
           else 
               setDistance(v. infinity)
           l = Q.insert(getDistance(v), v)
           setLocator(v, l)
       while !Q.isEmpty() 
           u = Q.removeMin()
           for all e in G.incidentEdges(u)
               z = G.opposite(u,e)
               r = getDistance(u) + weight(e)
               if r<getDistance(z)
                   setDistance(z, r)
                   setParent(z, e)
                   Q.replaceKey(getLocator(z), r)
   ```

7. What if has negative weight... (No negative cycles...)

   Bellman-Ford Algorithm

   ```java
   Algorithm BellmanFord(G,s)
       for all v in G.vertices()
           if v == s
               setDistance(v, 0)
           else
               setDistance(v, infinity)
       for i = 1 to n-1 do
           for each e in G.edges()
               {relax edge e}
               u = G.origin(e)
               z = G.opposite(u,e)
               r = getDistance(u) + weight(e)
               if r < getDistance(z)
                   setDistance(z, r)
   ```

8. DAG-based Algorithm

   ```java
   Algorithm DagDistances(G,s)
       for all v in G.vertices()
           if v == s
               setDistance(v, 0)
           else 
               setDistance(v, infinite)
       Perform a topological sort of the vertices
       for u = 1 to n do {in topological order}
           for each e in G.outEdges(u)
               {relax edge e}
               z = G.opposite(u,e)
               r = getDistance(u) + weight(e)
               if r<getDistance(z)
                   setDistance(z, r)
   ```

9. All-Pair Shortest Paths

   ```java
   Algorithms AllPair(G)
       for all vertex pairs (i,j)
           if i == j
               D0[i,j] = 0
           else if (i,j) is an edge in G
               D0[i,j] = weight(i,j)
           else
               D0[i,j] = infinite
       for k = 1 to n do
           for i = 1 to n do
               for j = 1 to n do
                   D[i,j] = min{D(k-1)[i,j], D(k-1)[i,k] + D(k-1)[k,j]}
   ```

   Dynamic programming, running time $O(n^3)$ 
