## Directed Graph

> Some equations are not supported, PDF version [here](https://people.umass.edu/zibinchen/pdf/graph_dir.pdf)

1. A digraph is a graph whose edges are all directed.

2. Diagraph properties: 

   1. each edge goes from one direction to another direction; 

   2. if G is simple, $m \le n*(n-1)$

3. DFS:

   > We can specialize the traversal algorithms to digraph by traversing edges only along their direction

   In the directed DFS, we have four types of edge *{discovery edge, back edge, forward edge, cross edge}*

4. Reachability: Strong Connectivity: Each vertex can reach all other vertices.

5. Strong Connectivity Algorithm: 

   - pick a vertex v in G, 

   - perform DFS from v in G, if there is a w that is unreachable, print "no",

   - let G' to be G with edge reversed,

   - perform DFS from v in G', if theres a w that is not reachable, print "no", else print "yes"

     Running time $O(m+n)$

6. Transitive closure

   Given a digraph G, the transitive closure of G is a graph G* such that 

   - G* hs the same vertices as G

   - if G has a directed path from u to v, ($u \neq v$), G* has a directed edge from u to v

   The transitive closeure provide a  reachability information about a graph.

7. Floyd-Warshall's Algorithm to find Transitive closure.

   > For each node, find out which nodes are connected not directly by them, connect directly.

   ```java
   Algorithm FloydWarshall(G)
       Input gigraph G
       Output transitive closure G* of G
       i = 1;
       for all v in G.vertices()
           denote v as vi
           i = i + 1;
       G0 = G
       for k = 1 to n do
           Gk = G(k-1)
           for i = 1 to n (i != k) do
               for j = 1 to n (j != i,k) do
                   if G(k-1).areAdjacent(vi,vk) && G(k-1).areAdjacent(vk,vj)
                       if !Gk.areAdjacent(vi,vj)
                           Gk.insertDirectedEdge(vi,vj,k)
       return Gn
   ```

8. DAG (Directed acyclic graph) is a digraph that has no directed cycles. A topological ordering of a diaph is a numbering $v_1, v_2,  ..., v_n$ of the vertices such that for every edge (vi, vj), we have i < j. 

   *A digraph admits a topological ordering iff it is a DAG*

9. Algorithm for Topological Sorting: Goodrich-Tamassia

   ```java
   Algorithm TopologicalSort(G)
       H = G;
       n = G.numVertices();
       while !H.isEmpty() do
           Let v be a vertex with no outgoing edges
           label v = n
           n = n - 1
           Remove v from H
   ```

        Running time $O(n+m)$

10. Topological Sort using DFS

    ```java
    Algorithm topologicalSortDFS(G)
        Input DAG G
        Output topological ordering of G
        n = G.numVertices()
        for all u in G.vertices()
            setLabel(u, UNEXPLORED)
        for all e in G.edges()
            setLabel(e, UNEXPLORED)
        for all v in G.vertices()
            if v.getLabel() == UNEXPLORED
                topologicalSortDFS(G, v)
    
    Algorithm topologicalSortDFS(G, v)
        Input DAG G & start vertex v
        Output labeling of the verticces of G in the connected component of v
        setLabel(v, VISITED)
        for all e in G.incidentEdges(v)
            if e.getLabel == UNEXPLORED
                w = opposite(v,e)
                if w.getLabel() == UNEXPLORED
                    setLabel(e, DISCOVERY)
                    topologicalSortDFS(G,w)
                else
                    {e is a forward or cross edge}
        Label v with topological number n;
        n = n - 1
    ```

11. Topological Sort using BFS

    ```java
    Algorithm topologicalSortBFS(G)
        H = G;
        i = 0;
        while H is not empty do {
            let v be a vertex with no incoming edges
            label v with topological number i;
            i = i + 1;
            remove v form H
        }
    ```

    Run time $O(m+n)$
