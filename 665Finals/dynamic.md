## Dynamic Programming

> Some equations are not supported, PDF version [here](https://people.umass.edu/zibinchen/pdf/dynamic.pdf)

1. A Characterizing Equation 

$$
N_{i,j} = \min \limits_{i\leq k<j} {N_{i,k} + N_{k+1,j}+d_id_{k+1}d_{j+1}}
$$

2. Solve the problems in subproblems overlap.

3. Algorithm: martrixChain

   ```java
   Algorithm matrixChain(s) 
       Input: sequence S of n martices to be multiplied.
       Output: number of operatins in optimal paranethization of S
       for i = 1 to n-1:
           N[i,i] = 0;
       for b = 1 to n-1 do:
           j = i + b;
           N[i,j] = +infinity;
           for k = i to j-1 do:
               N[i,j] = min{ N[i,j], N[i,k] + N[k+1,j] + d[i]d[k+1]d[j+1]};
       return N[0, n-1];
   ```

4. Run time:

$$
Total\ Runtime: O(n^3), Filling\ each\ entry:O(n) 
$$

5. General Dynamic Programming: apply to a problem that sees to require a lot of time (exponential), but we have simple subproblem, and subproblems are overlapped.

6. 0-1 Knapsack problem:

$$
Objective: Maximize \sum{B_i} \\
Constraint: \sum \limits_{i\in T} {w_i\leq W}
$$

7. Assume that items are labeled 1...n, define a new parameter: w, which will represent the exact weight for each subset of items. 

$$
B[k,w] = \begin{cases}
B[k-1,w], & \text{if } w_k>w; \\
max \left\{ B[k-1,w],\ B[k-1,w-w_k]+b_k\right\}, & \text else.
\end{cases}
$$

   It means, that the best subset of S\[k] that has total weight w is one of the two:

1. the best subset of S\[k-1] that has total weight w, or

2. the best subset of S\[k-1] that has total weight w-w\[k] plus the item k.

   The best subset of S\[k] that has total weight wither contains item k or not.

   First case: w\[k]>w. Item k cannot be part of the solution, since it was, the total weight cannot be > w, which is unacceptable.

   Second case: w\[k] < w. Then item k [can] be in the solution, and we choose the case that has the greater value.

8. How to know which items are carried?

$$
Let\ i=n,k=W \\
If\ B_{i,k} \neq B_{i-1,k}, then \\ 
i=i-1, k=k-w_i \\
else \\
i=i-1 \\
$$

9. 0-1 Knapsack problem Running Time: $ O(n^2)$

10. 
