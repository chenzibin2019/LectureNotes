## Breadth-first Search

> Some equations are not supported, PDF version [here](https://people.umass.edu/zibinchen/pdf/dfs.pdf)

1. Algorithm:

   ```java
   Algorithm BFS(G)
       Input graph G
       Output labeling of the edges and partition of the vertices of G
       for all u in G.vertices()
           setLabel(u,UNEXPLORED)
       for all e in G.edges()
           setLabel(e,UNEXPLORED)
       for all v in G.vertices()
           if v.getLabel() == UNEXPLORED
               BFS(G,v)
   
   Algorithm BFS(G,s)
       L0 = new empty sequence();
       L0.insertLast(s);
       setLabel(s,VISITED);
       i = 0;
       while not Li.isEmpty()
           L(i + 1) = new empty sequence();
           for all v in Li.elements()
               for all e in G.incidentEdges(v)
                   if e.getLable() == UNEXPLORED
                       w = opposite(v,e)
                       if w.getLabel() == UNEXPLORED
                           setLabel(e, DISCOVERY)
                           setLabel(w, VISITED)
                           L(i+1).inesrtLast(w)
                       else
                           setLabel(e, CROSS)
           i = i + 1
   ```

2. Properities

   > Notation: $G_s$ : connected component of s

   - BFS(G, s) visits all the vertices and edges of $G_s$

   - The discovery edges labeled by BFS(G, s) form a spanning tree $T_s$ of $G_s$

   - For all vertex v in $L_i$: the path of $T_s$ from s to v has i edges, every parth from s to v in $G_s$ has at lease i edges.

3. Analysis

   1. Setting/getting a vertex/edge label takes $O(1)$ time

   2. Each vertex is labeled twice. (See [DFS](https://github.com/chenzibin2019/LectureNotes/tree/master/665Finals/dfs.md))

   3. Each edge is labeled twice. (See [DFS](https://github.com/chenzibin2019/LectureNotes/tree/master/665Finals/dfs.md))

   4. Each vertex is inserted once into a sequence $L_i$

   5. BFS runs in $O(n+m)$ time provided the graph is represented by the adjacency list structure.

4. Applications

   > using the template method partition, we can specialize the BFS traversal of a graph G to solve the following problems in $O(n+m)$ time

   - Computer the connected components of G

   - Compute a spanning forest of G

   - Find a simple cycle in G, or report that G is forest

   - Given two vertices of G, find a path in G between them with the minimum number of edges, or report that no such path exist.

     | Applications                                         | DFS | BFS |
     | ---------------------------------------------------- | --- | --- |
     | Spanning forest, Connected components, paths, Cycles | Y   | Y   |
     | Shortest paths                                       |     | Y   |
     | Biconnected components                               | Y   |     |

5. Back edge vs. Cross edge  ==>(v, w)

   - Back edge: w is an ancestor of v in  the tree of discovery edges

   - Cross edge: w is in the same level with v or in the next level in the tree of discovery edges.
