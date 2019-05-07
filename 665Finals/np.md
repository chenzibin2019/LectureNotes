## NP-Completeness

1. All the polynomial-time algorithms studied so far in this course run in polynomial time using the definition of input size.

2. Polynomial-Time Decision Problems

   - To simplify the notion of "hardness", we will focus on the following:
     - Polynomial-time as the cut-off for the efficiency 

3. Complexity Class P

   - A complexity class is a collection of languages

   - P is the complexity class consisting of all languages that are accepted by polynomial-time algorithms

   - For each language L in P, there is a polynomial-time decision algorithm A got L

     - If n = |x|, for x in L, then A runs in p(n) time on input x.

     - The function p(n) is some polynomial.

4. NP is the complexity class consisting of all languages accepted by polynomial-time and non-deterministic algorithms

   ![5cd0fae0b34d0](https://i.loli.net/2019/05/07/5cd0fae0b34d0.png)

5. P problem can be solved in polynomial time, NP problem can be verified in polynomial time, NPC is NP can be converted to polynomial time, NP-hard can be converted to polynomial time.
