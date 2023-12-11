# CMPS 2200 Assignment 5
## Answers

**Name:** Simon Yung






- **1a.**
Because the new nodes in a heap are created exponentially by a factor of d, to find the depth, you need to take the log base d of Edges and round it up to account for any hangover.

    depth = $\lceil log_d(E) \rceil$  

- **1b.**
The delete min operation has the worst case of removing the root and then making $d - 1$ comparison every time you need to replace a node to make the new root recursively. Therefore, the work is the depth times the number of nodes in each level. 

    $O(d*\lceil log_d(E) \rceil)$    

- **1c.**
In the original Dijkstra's algorithim which is based on a binary tree, the work is $O(|E|\log |E|)$. if we then upgrade the heap to d-ary the log will also increase to that standard:   
        $O(|E|\log_d |E|)$  
    <br/>
- **1d.**
Becuase the work found with addition of d-ary heap is $O(|E|\log_d |E|)$ according to log rules to make $log_d |E|$ equal to one is to make $d = |E|$
  
  <br/>
*** 

- **2a.**
APSP(0,1,2) = -2  
APSP(1,2,2) = 0  
APSP(0,2,2) = -1  
APSP(0,1,1) = -2  
APSP(1,2,1) = 0  
APSP(0,2,1) = -1  
APSP(0,1,0) = -2   
APSP(1,2,0) = 1  
APSP(0,2,0) = 2


- **2b.**
Yes, because there are only three nodes, k == 1 and k == 2, each node can be visited once, so the extra node provided by 2 is not needed, making 1 and 2 the same. Yes, you can. Since k ==1 and k == 2 are the same, you can upscale one into 2. 


- **2c.**

        APSP(i, j, k) = min(APSP(i, j, k-1), APSP(i, k, k-1) + APSP(k, j, k-1))

- **2d.**
The number of distinct subproblems is that there are n possibilites for i,j, and k leading to the total being $n^ 3$

    - Based on the Optimal substructure we implemented in 2c() each call comes with 3 other call to APSP plus the original call makes 4. This means that the work of naively implemeting the algorithim's work grows according to $O(n^4)$    

- **2e.**
The work of Johnson's algorithim is $O(|V|⋅|E|log|E|)$. this meams our dynamic programming algorithims is not ever better by a factor of |V|^3. 

---
- **3a.**
Because MMET is a shortsighted version of MST, it may miss a potentially shorter in the long run path. This means that MST is not guaranteed to be a solution to MMET. Ie. MST will go 4-2-1, but MMET will go 1- 1- 100. 

- **3b.**
1. Find the MST
2. Find a critical edge that can be removed; this can be done by brute forcing every edge in the MST that is able to be replaced and make a tree
3. Replace the critical edge
4. find the minimum tree that accepts above conditions.


- **3c.**

The basic work of prims or Kruskalls algorithims is $O(|E|log|E|)$. This means my algorithim has that time complexity plus the time of checking each possible switch. With n edges in the MST there is a maximum of n other possiblities for the second best. Therefore the Work is $O(n* |E|log|E|)$ 
