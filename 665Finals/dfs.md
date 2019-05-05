## Depth-first Search

> Some equations are not supported, PDF version [here](https://people.umass.edu/zibinchen/pdf/dfs.pdf)

1. Subgraph. A subgraph of a graph is a graph such that 

   1. The vertices of S are a subset of vertices of G

   2. The edges of S are a subset of edges of G

2. Spanning subgraph is a graph that contains all the vertices of G

3. A graph is connected if there is a path between every pair of vertices. A connected component of a graph G is a maximal connected subgraph of G.

4. Trees and forest.

   - A (free) tree is an undirected graph T that T is connected and has no cycles.

   - A forest is an undirected graph without cycles.

   - The connected components of a forest are trees.

5. Spanning tree. 

   - A spnning tree of a connected graph is a spanning subgraph that is a tree.

   - A spanning tree is not unique.

   - A spanning forest of a graph is a spanning subgraph that is a forest.

6. DFS.

   1. Depth-first search is a general technique for traversig a graph.

   2. DFS:

      - Visit all the vertices and edges of G

      - Determin whether G is connected.

      - Computes the connected components of G

      - Computes a spanning forest of G

   3. DFS on a graph with n vertices and m edges takes $O(n+m)$ time.

   4. DFS Algorithm 

      ```java
      Algorithm DFS(G) 
          Input Graph G;
          Output labeling of the edges of G as discovery edges and back edges.
          for all u in G.vertices():
              setLabel(u, UNEXPLORED);
          for all e in G.edges():
              setLabel(e, UNEXPLORED);
          for all v in G.vertices():
              if v.getlabel() == UNEXPLORED:
                  DFS(G,v)        // in case Graph is not connected.
      
      Algorithm DFS(G, v)
          Input graph G and a start vertex v of G
          Output labeling of the edges of G in connected component of v as discovey edge and back edges.
          setLabel(v, VISITED);
          for all e in G.incidentEnge(v)
              if e.getLabel() == UNEXPLORED:
                  w = opposite(v, e);
                  if w.getLabel() == UNEXPLORED
                      setLabel(e, DISCOVERY)
                      DFS(G, w)
                  else
                      setLabel(e,BACK)
      ```

   5. Properities of DFS

      - DFS(G,v) visits all the vertices snf edges in the connected componement of v

      - The discovery edges labeled by DFS(G,v) form a spanning tree of the connected component of v

   6. Analysis of DFS

      - setting/getting a vertex/edge label takes $O(1)$ time

      - each vertex is labeled twice: 1) labeled as UNEXPLORED => 2) labeled as VISITED

      - each edge is labeled twice: 1) labeled as UNEXPLORED => 2) labeled as DISCOVERY/BACK

      - DFS runs in $O(n+m)$ time 

7. Path finding 

   ```java
   Algorithm pathDFS(G,v,z)
       setLabel(v,VISITED)
       S.push(v)
       if v == z: return S
       for all e in G.incidentEdges(v):
           if(e.getLabel() == UNEXPLORED)
               w = opposite(v,e);
               if w.getLabel() == UNEXPLORED:
                   setLabel(e,DISCOVERY);
                   S.push(e)
                   pathDFS(G,w,z)
                   S.pop()
               else
                   setLabel(e,BACK)
       S.pop()
   ```

8. Cycle finding:

   ```java
   Algorithm cycleDFS(G,v,z)
       setLabel(v,VISITED);
       S.push(v) 
       for all e in G.incidentEdges(v)
           if e.getLabel() == UNEXPLORED
               w = opposite(v,e)
               S.push(e)
               if w.getLabel() == UNEXPLORED
                   setLabel(e,DISCOVERY)
                   pathDFS(G,w,z)
                   S.pop();
               else
                   T = new empty stack();
                   do
                       o = S.pop()
                       T.push(o)
                   while o == w
                   return T
       S.pop();
   ```
