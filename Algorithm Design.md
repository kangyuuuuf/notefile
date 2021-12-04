# Algorithm Design

## Chapter 1: Representative Problem

### 1.1 Stable Matching

#### The $G-S$ algorithm

Consider a set $M =\{m_1,\dots,m_n\}$  of $n$ men, and a set $W=\{w_1,\dots,w_n\}$ of n women. $M \times N$ denotes the set of all possible combinations of $(m,w)$ where $m \in M$ and $w\in W$.  A **perfect matching** S is a set of pairs that each element in $M$ and $W$ appears in exactly one pair in $S$. A matching $S$ is **stable** if it is perfect, and there is no **instability** with respect to $S$. There exists a stable matching for every set of preference lists.

**Theorem 1.3**	The $G-S$ algorithm terminates after at most $n^2$ iterations of the While loop.

**Theorem 1.5**	The $G-S$ algorithm returns a set of pair $S$ where $S$ is stable matching.

The $G-S$ algorithm will only return one of the stable matchings for a given set, which means it is unfair. In the book, the code of the example is favoring man, which gives the man the right to choose one of the women to propose. This will lead to the outcome of stable matching is the worse case for women. However, **all executions yield the same matching**.

**Theorem 1.7**	Every execution of The $G-S$ algorithm results in the set $S^*$, where $S^* = \{(m,best(m)):m\in M\}$ .

### 1.2 Five Representative Problem

#### Interval Scheduling

There are $n$ requests labeled $1,\dots,n$, and each time interval starts $s_i$ and ends $f_i$ where $s_i >f_i$ for all $i$. Two requests are **compatible** if there is no overlap. The goal is to find the max number of requests in a given time, related by **greedy algorithms**. 

#### Weighted Interval Scheduling

Now, each interval has a value, **weight**. In this question, it means the money we can get to accept given requests. And the goal is changed to find the max money we can get. Instead of using a greedy algorithm to find the intervals one at a time, **dynamic programming** is an efficient algorithm to solve this question.

#### Bipartite Matching

A graph $G = (V,E)$ is **bipartite** if its node-set $V$ can be partitioned into sets $X$ and $Y$ in such a way that every edge has one end in $X$ and the other end in $Y$. A **Bipartite Matching Problem** is, given an arbitrary bipartite graph $G$, to find a matching of maximum size.

#### Independent Set

Given a graph $G = (V,E)$, a set of node $S\sube V$ is **independent** if two nodes in $S$ are joined by an edge. According to the problem, the **Independent Set problem** is finding the independent set that is as large as possible.

#### Competitive Facility Location

Given a graph $G = (V,E)$, two players can choose the node in turns with the following rule: the graph the players choose can not be adjacent to the node that owns. At the same time, each node has a weight that represents the value of each node. The **Competitive Facility Location Problem** is finding out $P_2$ will be able to select a set of nodes with a total value of at least $B$ no matter how $P_1$ plays. If the graph is big, it would even be hard for us to convince you that $P_2$ have a winning strategy. This problem is in the class of **PSPACE-complete problems.** 

## Chapter 2: Basics of Algorithm Analysis

### 2.2 Asymptotic Order of Growth



#### $O$, $\Omega$, and $\Theta$

Define $O$ as **Asymptotic Upper Bounds**, $\Omega$ as **Asymptotic Lower Bounds**, and $\Theta$ as **Asymptotic Tight Bounds**

### 2.5 Implementing the Heap Operation

Just in case, the description of implement heap is in chapter 2.5

## Chapter 3: Graph

### 3.1 Basic Definition and Application

Edges in a graph indicate a symmetric relationship between their ends. The graph we consider is not directed, called an **undirected graph**.

#### Paths and Connectivity

A path is **simple** if all nodes are distinct from one another. A path $v_1,v_2,\dots, v_k-1, v_k$ in where $k>2$ is called **cycle** if the first $k-1$ nodes are all distinct, and $v_1 = v_k$. A graph is **connected** if, for every path of two nodes, there exists a path from one node to another. The **distance** between two nodes is the minimum number of edges in a path. 

**Theorem 3.2**	Let $G$ be an undirected graph on $n$ nodes. Any two of the following statements imply the third.

- $G$ is connected.

- $G$ does not contain a cycle.
- G has $n-1$ edges.

### 3.2 & 3.3 Graph Traversal and Implement

#### Breadth-First Search

BFS focus on the Layer., implemented by a queue.

**Theorem 3.3**	For each $j \ge 1$, layer $L_j$ produced by BFS consists of all nodes at distance exactly $j$ from $s$. There is a path from $s$ to $t$ $iff$ $t$ appears in some layer.

**Theorem 3.4**	Let $T$ be a BFS tree, let $x$ and $y$ be nodes in $T$ belonging to layers $L_i$ and $L_j$ respectively, and let $(x,y)$ be an edge of $G$. Then $i$ and $j$ differ by at most $1$.

#### Depth-First Search

DFS focus on the depth, implemented by a stack.

**Theorem 3.7**	Let $T$ be a DFS tree, let $x$ and $y$ be nodes in $T$, and let $(x,y)$ be an edge of $G$ that is not an edge of $T$. Then one of $x$ or $y$ is an ancestor of the other.

#### The Set of All Connected Components

**Theorem 3.8**	For any two nodes $s$ and $t$ in a graph, their connected components are either identical or disjoint.

### 3.4 Testing Bipartiteness(BFS)

**Theorem 3.14**	If a graph is bipartite, then it cannot contain an odd cycle.

The Step of testing bipartiteness will just become implement BFS and mark the color for each layer.

### 3.5 Connectivity in Directed Graphs

For a directed graph, the edge $(u,v)$ has a direction, which means the relationship between $u$ and $v$ is asymmetric.

#### Representing Directed Graph

We use a version of the adjacency list representation. This means that each node has two lists associated with it: once list consists of nodes to which it has edges, and a second list consists of nodes from which it has edges. The table below shows the example of a directed graph. The rows represent the start and the columns represent the end. If there is an edge existed, it is $1$. In the table, there is a path from $A$ to $B$, but not $B$ to $A$.

|      | A    | B    | C    |
| ---- | ---- | ---- | ---- |
| A    | 0    | 1    | 1    |
| B    | 0    | 0    | 1    |
| C    | 1    | 0    | 0    |

#### The Graph Search Algorithms

Both BFS and DFS works for directed graphs. Notes that it is possible for a node $s$ to have a path to a node $t$ even though $t$ have no path to $s$.

#### Strong Connectivity

A directed graph is **strongly connected** if, fr every two nodes $u $and $v$, there is a path from $u$ to $v$ and a path from $v$ to $u$. Two nodes $u$ and $v$ in a directed graph are **mutually reachable** if there is a path from $u$ to $v$ and also a path from $v$ to $u$.

**Theorem 3.17**	For ant two nodes $s$ and $t$ in a directed graph, their strong components are either identical or disjoint.

### 3.6 Directed Acyclic Graphs and Topological Ordering

If a directed graph has no cycles, we call it a **directed acyclic graph**, or a DAG for short. For a directed graph $G$, a **topological ordering** of $G$ is an ordering of its nodes as $v_1,v_2,\dots,v_n$ so that every edge $(v_i,v_j)$, we have $i < j$. In other words, all edges point "forward" in the ordering.

**Theorem 3.18**	If $G$ has a topological ordering, then $G$ is a DAG.

#### Computing a Topological Ordering

**Theorem 3.20**	If $G$ is a DAG, then $G$ has a topological ordering.

First, find a node $v_1$ that has no incoming edges. Second, delete $v_1$. Third, do the recursive until there is no node in $G $.

Define a node to be "active" if it has not yet been deleted by the algorithm, and we explicitly maintain two things:

- for each node $w$, the number of incoming edges that $w$ has from active nodes.
- the set $S$ of all active nodes in $G$ that have no incoming edges from other active nodes.

