---
layout: post
section-type: post
has-comments: true
title: "The Shortest Path"
category: algorithm
---

## **Dijkstra**

> The shortest path from one vertex to the rest.
> 

**Steps**:

1. Initially, S only contains the source point, `S={v}`, and the distance from vertex v to itself is 0. U contains vertices other than v, and the distance from v to vertices i in U is the weight on the edge.
2. Choose a vertex u from U, the distance from vertex v to u is the smallest, and then add vertex u to S.
3. Take vertex u as the newly considered middle point and modify the distance from v to each point in U.
4. Repeat the above steps to know that S contains all vertices.

## **Floyd**

> Di,j,k is the shortest path from i to j only passing verticles (1..k).
> 

```
for each vertex v
    dist[v][v] ← 0
 for each edge (u,v)
    dist[u][v] ← w(u,v)  // the weight of the edge (u,v)
 for k from 1 to |V|
    for i from 1 to |V|
       for j from 1 to |V|
          if dist[i][j] > dist[i][k] + dist[k][j]
             dist[i][j] ← dist[i][k] + dist[k][j]
         end if
```