# Python Data Structures and Algos Cheatsheet

## Table of Contents
- [Data Structures Overview](#data-structures-overview)
  - [Arrays](#arrays)
  - [Dynamic Arrays vs Static Arrays](#dynamic-arrays-vs-static-arrays)
  - [Hash](#hash)
  - [Hash Maps](#hash-maps)
  - [Hash Set](#hash-set)
  - [Hash Table](#hash-table)
  - [Stack](#stack)
  - [Graphs](#graphs)
    - [Graph Types](#graph-types)
    - [Representing a Graph in Code](#representing-a-graph-in-code)
  - [Trees](#trees)
  - [Binary Search Tree](#binary-search-tree)
  - [LinkedLists](#linkedlists)
    - [Singly Linked List](#singly-linked-list)
    - [Doubly Linked List](#doubly-linked-list)
  - [Tries](#tries)
  - [Min-Max Heap / Priority Queue](#min-max-heap--priority-queue)

- [Common Algorithms Overview](#common-algorithms-overview)
  - [Greedy](#greedy)
  - [Array](#array)
  - [Two Pointers](#two-pointers)
  - [Sliding Window](#sliding-window)
  - [Sliding Window vs Kadane’s Algorithm](#sliding-window-vs-kadanes-algorithm)
  - [Binary Search](#binary-search)
  - [LinkedList](#linkedlist)
  - [Floydd’s Rabbit and Hare (Fast and Slow Pointers)](#floydds-rabbit-and-hare-fast-and-slow-pointers)
  - [Graphs](#graphs-1)
    - [Traversal Algorithms](#traversal-algorithms)
    - [Depth-First Search (DFS)](#depth-first-search-dfs)
    - [Breadth-First Search (BFS)](#breadth-first-search-bfs)
    - [Detect a Cycle in a Directed Graph using Depth-First Search (DFS)](#detect-a-cycle-in-a-directed-graph-using-depth-first-search-dfs)
    - [Topological Ordering and Sorting](#topological-ordering-and-sorting)
    - [Vertex Degrees](#vertex-degrees)
    - [Kahn’s Algorithm](#kahns-algorithm)
    - [Shortest Path in Weighted Directed Graph](#shortest-path-in-weighted-directed-graph)
      - [Dijkstra’s Algorithm](#dijkstras-algorithm)
      - [Bellman-Ford Algorithm](#bellman-ford-algorithm)
  - [Backtracking](#backtracking)
  - [Dynamic Programming](#dynamic-programming)

- [Python Tricks](#python-tricks)

## Data Structures Overview

### Arrays
- Collection of elements stored at contiguous memory locations.
- Fixed size.
- Fast access by index.
- Insertion/deletion can be costly (elements need shifting).

### Dynamic Arrays vs Static Arrays
| Feature             | Static Array          | Dynamic Array               |
|---------------------|----------------------|-----------------------------|
| Size                | Fixed at compile-time | Can grow/shrink dynamically  |
| Memory              | Allocated once       | Resizable, may reallocate    |
| Access Time         | O(1)                 | O(1)                        |
| Insertion/Deletion  | Costly (O(n))        | Amortized O(1) for append   |

### Hash
- Data structure that stores key-value pairs.
- Supports fast lookup, insertion, and deletion.
- Uses a hash function to compute index for storing keys.

### Hash Maps
- Also called dictionaries in Python (`dict`).
- Implements an associative array mapping keys to values.
- Average time complexity O(1) for search, insert, delete.

### Hash Set
- Collection of unique elements.
- Supports fast membership testing.
- Implemented with hashing (e.g., Python’s `set`).

### Hash Table
- Array + Hash Function + Collision Resolution.
- Collisions handled via chaining or open addressing.

### Stack
- LIFO (Last In First Out) data structure.
- Operations: `push` (add), `pop` (remove top), `peek` (view top).
- Use cases: expression evaluation, backtracking, undo operations.

## Graphs

### Graph Types
- **Undirected Graph**: Edges have no direction. Connections go both ways.
- **Directed Graph (Digraph)**: Edges have direction from one vertex to another.
- **Weighted Graph**: Edges have weights (costs, distances).
- **Unweighted Graph**: Edges have no weights.
- **Cyclic Graph**: Contains at least one cycle.
- **Acyclic Graph**: Contains no cycles.
- **Connected Graph**: There is a path between any two vertices (for undirected).
- **Disconnected Graph**: Not all vertices are reachable from each other.

### Graph Representations

| Representation | Description                                   | Space Complexity      | Suitable For               |
|----------------|-----------------------------------------------|----------------------|----------------------------|
| **Adjacency Matrix** | 2D matrix where `matrix[i][j]` indicates edge presence or weight between vertex i and j | O(V²) where V = vertices | Dense graphs (many edges) |
| **Adjacency List**   | Array or list of lists, where each list contains neighbors of a vertex | O(V + E) where E = edges | Sparse graphs (few edges)  |
| **Edge List**        | List of all edges (pairs or triples for weighted) | O(E)                  | Simple and easy to iterate |

### Notes
- Adjacency Matrix allows O(1) edge lookup but uses more memory.
- Adjacency List is memory efficient, but edge lookup is O(k) where k is neighbors count.
- Edge List is simple but slow for lookup.

## Graph Traversals

### Depth-First Search (DFS)
- Explores as far as possible along each branch before backtracking.
- Uses a **stack** data structure (can be implemented recursively).
- Steps:
  1. Start at a source vertex.
  2. Mark it visited.
  3. For each unvisited neighbor, recursively perform DFS.
- Useful for:
  - Detecting cycles.
  - Topological sorting.
  - Finding connected components.
- Time Complexity: O(V + E)

### Breadth-First Search (BFS)
- Explores neighbors level by level.
- Uses a **queue** data structure.
- Steps:
  1. Start at a source vertex.
  2. Enqueue it and mark visited.
  3. While queue is not empty:
     - Dequeue vertex.
     - Enqueue all unvisited neighbors.
- Useful for:
  - Finding shortest path in unweighted graphs.
  - Checking bipartiteness.
- Time Complexity: O(V + E)

### Pseudocode

**DFS (recursive):**
```pseudo
DFS(vertex):
    mark vertex as visited
    for each neighbor in adjacency_list[vertex]:
        if neighbor not visited:
            DFS(neighbor)
```

**BFS (iterative):**
```
BFS(start_vertex):
    create a queue Q
    mark start_vertex visited
    enqueue start_vertex into Q
    while Q not empty:
        vertex = dequeue from Q
        for each neighbor in adjacency_list[vertex]:
            if neighbor not visited:
                mark neighbor visited
                enqueue neighbor into Q
```
## Topological Sort and Cycle Detection

### Topological Sort
- Applicable only to **Directed Acyclic Graphs (DAGs)**.
- Provides a linear ordering of vertices such that for every directed edge u → v, u comes before v in the ordering.
- Useful in scheduling tasks, build systems, etc.

### Methods to perform Topological Sort

#### 1. DFS-based approach:
- Perform DFS on the graph.
- After visiting all neighbors of a vertex, add the vertex to a stack.
- Reverse the stack to get the topological order.

#### 2. Kahn’s Algorithm (BFS-based):
- Calculate in-degree (number of incoming edges) for all vertices.
- Enqueue all vertices with in-degree 0.
- While queue is not empty:
  - Dequeue a vertex u and add it to the topological order.
  - For each neighbor v of u:
    - Decrease in-degree of v by 1.
    - If in-degree of v becomes 0, enqueue v.

### Cycle Detection in Directed Graphs
- If a cycle exists, topological sort is not possible.
- Use DFS with recursion stack:
  - Maintain a recursion stack along with visited array.
  - If a vertex is encountered that is already in recursion stack → cycle detected.

### Pseudocode

**DFS-based Topological Sort:**
```pseudo
visited = set()
stack = []

function DFS(vertex):
    mark vertex visited
    for neighbor in adjacency_list[vertex]:
        if neighbor not visited:
            DFS(neighbor)
    stack.push(vertex)

for each vertex v:
    if v not visited:
        DFS(v)

topological_order = reverse(stack)
```

**Kahn's Algorithmn**
```
in_degree = array of zeros for all vertices
for each vertex u:
    for each neighbor v in adjacency_list[u]:
        in_degree[v] += 1

queue = all vertices with in_degree 0
top_order = []

while queue not empty:
    u = dequeue(queue)
    top_order.append(u)
    for neighbor v in adjacency_list[u]:
        in_degree[v] -= 1
        if in_degree[v] == 0:
            enqueue(queue, v)

if length(top_order) != number_of_vertices:
    print("Graph has a cycle")
else:
    print("Topological order:", top_order)
```

**Cycle Detection Using DFS**
```
visited = set()
rec_stack = set()

function DFS(vertex):
    mark vertex visited
    add vertex to rec_stack
    for neighbor in adjacency_list[vertex]:
        if neighbor not visited:
            if DFS(neighbor) == true:
                return true
        else if neighbor in rec_stack:
            return true
    remove vertex from rec_stack
    return false

for each vertex v:
    if v not visited:
        if DFS(v) == true:
            print("Cycle detected")
            break
```

## Shortest Path Algorithms

#### 1. Breadth-First Search (BFS) for Unweighted Graphs
- Finds shortest path in terms of number of edges.
- Works only if all edges have the same weight (or unweighted).
- Uses a queue to explore vertices level by level.

```pseudo
distance = array with infinity for all vertices
distance[start] = 0
queue = [start]

while queue not empty:
    u = dequeue(queue)
    for each neighbor v of u:
        if distance[v] == infinity:
            distance[v] = distance[u] + 1
            enqueue(queue, v)
```

#### 2. Dijkstra’s Algorithm (Weighted Graphs with Non-negative Weights)
- Finds shortest paths from a source vertex to all others.
- Uses a priority queue (min-heap) to pick the closest vertex.

```pseudo
distance = array with infinity for all vertices
distance[source] = 0
min_heap = priority queue with (distance[source], source)

while min_heap is not empty:
    (dist_u, u) = extract_min(min_heap)
    if dist_u > distance[u]:
        continue
    for each neighbor v of u:
        alt = distance[u] + weight(u, v)
        if alt < distance[v]:
            distance[v] = alt
            insert(min_heap, (alt, v))

```

#### 3. Bellman-Ford Algorithm (Handles Negative Weights & Detects Negative Cycles)
- Relaxes all edges |V| - 1 times.
- Checks for negative weight cycles by an additional relaxation.

```pseudo
distance = array with infinity for all vertices
distance[source] = 0

for i in 1 to |V| - 1:
    for each edge (u, v) with weight w:
        if distance[u] + w < distance[v]:
            distance[v] = distance[u] + w

for each edge (u, v) with weight w:
    if distance[u] + w < distance[v]:
        print("Graph contains a negative weight cycle")
```

#### 4. Floyd-Warshall Algorithm (All Pairs Shortest Path)
- Dynamic programming approach.
- Time complexity: O(V³).
- Can handle negative weights but no negative cycles.

```pseudo
dist = 2D array initialized with edge weights, 0 on diagonals

for k in 1 to V:
    for i in 1 to V:
        for j in 1 to V:
            if dist[i][k] + dist[k][j] < dist[i][j]:
                dist[i][j] = dist[i][k] + dist[k][j]

```

### Summary
| Algorithm      | Use Case                             | Handles Negative Weights | Time Complexity       |
|----------------|------------------------------------|-------------------------|----------------------|
| BFS            | Unweighted graphs                  | No                      | O(V + E)             |
| Dijkstra       | Weighted graphs (non-negative)     | No                      | O((V + E) log V)     |
| Bellman-Ford   | Weighted graphs (with negative edges) | Yes                  | O(V * E)             |
| Floyd-Warshall | All pairs shortest paths            | Yes (no negative cycles) | O(V³)                |

