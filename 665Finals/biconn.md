## Biconnectivitiy

> Some equations are not supported, PDF version [here](https://people.umass.edu/zibinchen/pdf/biconn.pdf)

1. Separation edges and vertices

   - Definiations: Let G be a connected graph, a seperation edge/vertex of G is an edge/vertex whose removal disconnects G

   - Applications: seperation edges and vertices represent single points of failure in a network and are critical to the operation of the network.

2. Equivalent definitions of a biconnected graph G: In graph G, for any two vertices u and v, there are two disjoint simple paths between u and v or for any two vertices u and v, there is a simple cycle that contains both u and v.

3. Ab equivalence relation R on S satisfies the following properties:

$$
Reflexive:(x,x) \in R \\
Symmetric:(x,y) \in R \Longrightarrow (y,x) \in R \\
Transitive:(x,y) \in R \ \wedge \ (y,z) \in R \Longrightarrow (x,z) \in R
$$

4. Link relations. 

   - Edge e and f of connected graph G are linked if e=f or G has a simple cycle containing e and f.

   - The link relation on the edges of a graph os an equivalence relation

   - A separation edge is a single-element equivalence class of linked edges.

   - A separation vertex has incident edges in at least two distinct equivalence classes of linked edge.

5. Auxiliary Graph

   - Auxiliary graph B for a connected graph F associated witha  DFS trversal of G; The vertices of B are the edges of G

   - For each back edge e of G, B has edges (e,f1), (e,f2), ... (e,fk), where f1, f2, ..., fk are discovery edges of G that form a simple cycle with e.

6. Proxy Graph: Spanning forest of Auxiliary graph.

   ```java
   Algorithm proxyGrpah(G) 
       Input connected graph G;
       Output proxy graph F for G;
       F = empty graph;
       DFS(G, s); //s is any vertex of G
       for all discovery edges e of G:
           F.insertVertex(e);
           setLabel(e, UNLINKED);
       for all vertices v of G in DFS visit order
           for all back edges e = (u,v)
               F.insertVertex(e)
               do
                   d = discovery edge with dest, u
                   F.insertEdge(e,f,NULL);
                   if f.getLabel() == UNLINKED then
                       setLabel(f, LINKED);
                       u = origin of edge f;
                   else
                       u = v
               while u != v;
       return F;
   ```
