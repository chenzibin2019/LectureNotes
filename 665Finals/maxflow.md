## Maximum Flow

> Some equations are not supported, PDF version [here](https://people.umass.edu/zibinchen/pdf/maxflow.pdf)

1. Flow network: A weighted digraph G with nonnegative integer edge weights, where the weight of an edge e is called the capacity c(e) of e. Two distinguished vertices, s and t of G, called the source and sink, respectively, such that s has no incoming edges and t has no outgoing edges.

   A flow f for network N is an assignment of an integer value f(e) to each edge e that satisfies the following properties:

   Capacity Rule: For each edge e, 
   $$
   0<f(e)<c(e) 
   $$
   Conservation Rule: For each vertex, 
   $$
   v \ne s,t: \sum \limits{e \in E^-(v)} f(e) = \sum \limits{e \in E^+(v)} f(e)
   $$
    where 
   $$
   E^+(v)\ and\ E^-(v)
   $$
   are incoming and outgoing edges of v.

2. Maximum Flow

   - A flow for a network N is said to be maximum if its value is the largest for N

   - The maximum flow problem consists of finding a maximum flow for a given network.

3. Cut.

   - A cut for a network N with source s and sink t is a partition that makes s and t in different partition.

     - Forward edge of cut: origin in Vs and destiation in Vt

     - Backward edge of cut: origin in Vt and destinanation in Vs

   - Flow of a cut: total flow of forward edges - total flow od backward edge.

4. Augmenting Path

   - Consider a flow f for a Network N

   - Let e to be an edge from u to v:

     - Residual capacity of forward edge e from u to v: $\Delta (u,v)  =c(e) - f(e)$,

     - Residual capacity of backword edge e  from v to u:$\Delta (v,u) = f(e)$

   - Let $\pi$ to be a path from s to t

     - The residual capacity 
       $$
       \Delta _f (\pi )
       $$
        of pi is the smallest of the residual capacities of the edge pi.

   - A path pi from s to t is and augmenting path if 
     $$
     \Delta _f (\pi ) > 0
     $$

   - Let pi be an augmenting path for flow f in network N. There exists a flow f' for N of value

$$
|f'| = |f| + \Delta _f (\pi)
$$

5. Fork-Fulkerson's Algorithm

   ```java
   Algorithm ForkFulkersonMaxFlow(N)
       for all e in G.edge()
           setFlow(e,0)
       while G has an augmenting path pi
           {compute residual capacity Delta of pi}
           Delta = infinite
           for all edges e in pi
               {compute residual capacity delta of e}
               if e is a forword edge of pi
                   delta = getCapacity(e) - getFlow(e)
               else
                   delta = getFlow(e)
               if delta < Delta
                   Delta = delta
           {augument flow along pi}
           for all edges e in pi
               if e is a forward edge of pi
                   setFlow(e, getFlow(e) + Delta)
               else
                   setFlow(e, getFlow(e) - Delta)
   ```

   Analyse: 

   - In worst case, Fork-Fulkerson's Algorithm performs |f\*| flow augumentations, where f* is a maximum flow 

   - Finding an augmenting path and the augmenting the flow takes O(n+m) times.

   - The ForkFulkerson's Algorithm takes 
     $$
     O(|f^*|(n+m))
     $$
     times.

6. Edmonds-Karp Algorithm 

   - Variation of Ford-Fulkerson's Algorithm

   - Use a simple technique for finding good augmenting path in faster running time

     - It's more greedy in choice of path,

     - Choose an augmenting path $\pi$ with the smallest number of edges

     - This can be done in $O(m)$ by a modified BFS

   - Complexity 
     $$
     O(nm^2)
     $$

   - The number of flow augmentations in Edmonds-Karp Algorithm for a network with n vertices and m edges is no more than mn

7. Maximum Bipartite Matching

   - Graph G(V,E) is bipartite (denoted G(V1, V2, E)) if 

     - The vertices V of G can be partitioned into to disjoint sets V1 and V2

     - Every edge G has one endpoint in V1 and the other in V2

   - A matching in G is a set of edges (subset of E) that have no endpoints in common. A matching in bipartite graph is called bipartite matching

   - Reduction to Max Flow Problem. Add a source and sink...( 
     $$
     f(e) = 1 \Longrightarrow e \in M
     $$
     )

     - The flow through e is o or 1 (cap == 1)

     - Each vertex in V1 has exactly 1 incoming edge: by flow conservation rule

     - Each vertex in V2 has exactly 1 outcoming edge

8. Min Cost Flow Problem

   - A variant of the max flow problem, applicable to networks where there is a cost w(e) associated with sending a unit flow through an edge
     - Associate code w(e) with each edge e in the network N

     - Compute flow f with minimum total cost:

$$
min\ w(f) = \sum \limits_{e \in E} w(e)f(e)
$$

    - That is, find a minimum-cost flow among all the flows of maximum f

9. 
