# Graph


## Table of Contents


- [Table of Contents](#table-of-contents)
- [Cycle Detection In Undiected Graph](#cycle-detection-in-undiected-graph)
- [Cycle Detection in Undirected graphs Using DFS](#using-dfs)
- [Cycle Detection in Undirected graphs using BFS](#using-bfs)
- [Cycle Detection in Undirected graphs Using DSU](#using-dsu)
- [Cycle Detection in Directed Graph Using DFS](#cycle-detection-in-a-directed-graph-using-dfs)
- [Topological Sort](#topological-sort)
- [Topological Sort Using DFS and stack](#using-dfs-and-stack)
- [Topological Sort Using BFS (KAHN's algorithm)](#using-bfs-kahns-algorithm)
- [Cycle Detection in a directed graph Using BFS (Kahn's algorithm)](#cycle-detection-in-a-directed-graph-using-bfs-kahns-algorithm)
- [Is Graph bipartite](#is-graph-bipartite)
- [Is Graph Bipartite Using DFS](#using-dfs-1)
- [Is Graph Bipartite Using BFS](#using-bfs-1)
- [Disjoint Set Union (DSU)](#disjoint-set-union-dsu)
- [Normal (DSU)](#normal-dsu)
- [Rank and Path Compression (DSU)](#rank-and-path-compression-dsu)
- [Size and path Compression (DSU)](#size-and-path-compression-dsu)
- [Dijkstra Algorithm](#dijkstra-algorithm)
- [Dijkstra Algorithm Using Priority Queue (Min Heap)](#using-priority-queue-min-heap)
- [Dijkstra Algorithm Using Set](#using-set)
- [Bellman Ford Algorithm](#bellman-ford-algorithm)
- [Floyd Warshall Algorithm](#floyd-warshall-algorithm)
- [Minimum Spanning Tree](#minimum-spannig-tree-mst--minimum-weight-spanning-tree)
- [Minimum Spanning Tree Using Prim's Algorithm](#prims-algorithm)
- [Minimum Spanning Tree Using Kruskal's Algorithm](#kruskal-algorithm)
- [KosaRaju's Algorithm](#kosarajus-algorithm)
- [Euler Path and Circuit](#euler-path-and-circuit)






## Cycle Detection In Undiected Graph

### Using DFS


-  **Intution :-**

The code detects cycles in an undirected graph using Depth-First Search (DFS). It traverses each node and its neighbors, marking nodes as visited to track traversal. The `dfs` function checks if a node's neighbor is already visited and not the direct parent, indicating a cycle. The cycle detection is propagated up the call stack if found. The `isCycle` function ensures all components are checked, returning `true` if any cycle is detected, and `false` otherwise.


```cpp
class Solution {
public:
    bool dfs(vector<int> adj[], vector<bool>& visited, int parent, int node) {
        visited[node] = true; // Mark the current node as visited
        for (int neighbor : adj[node]) {
            if (neighbor == parent) continue; // Skip the edge back to the parent
            if (visited[neighbor]) return true; // Cycle detected
            bool hasCycle = dfs(adj, visited, node, neighbor);
            if (hasCycle) return true; // Propagate cycle detection up the call stack
        }
        return false; // No cycle detected from this node
    }
    
    bool isCycle(int V, vector<int> adj[]) {
        vector<bool> visited(V, false); // Initialize visited array for all nodes
        
        for (int i = 0; i < V; i++) {
            if (!visited[i]) {
                if (dfs(adj, visited, -1, i)) {
                    return true; // If a cycle is detected, return true
                }
            }
        }
        return false; // No cycle detected in any component
    }
};

```
- [Table of Contents](#table-of-contents)

### Using BFS


-  **Intution :-**

The code detects cycles in an undirected graph using Breadth-First Search (BFS). It processes each node with BFS, tracking the parent of each node to distinguish back edges. If a visited node is encountered that isn't the parent of the current node, a cycle is detected. The `isCycleBFS` function performs BFS from each unvisited node, while `isCycle` ensures all components of the graph are checked. If any component contains a cycle, the function returns `true`; otherwise, it returns `false`.


``` Cpp
class Solution {
  public:
    bool isCycleBFS(vector<int> g[], int V, int start, vector<bool>& visited) {
        queue<pair<int, int>> que;
        que.push({start, -1});
        visited[start] = true;
        while(!que.empty()) {
            int curr   = que.front().first;
            int parent = que.front().second;
            que.pop();
            
            for(auto x : g[curr]) {
                if(visited[x] == false) {
                    que.push({x, curr});
                    visited[x] = true;
                }
                else if(x != parent)
                    return true;
            }
        }
        
        return false;
    }

  
    // Function to detect cycle in an undirected graph.
    bool isCycle(int V, vector<int> adj[]) {
        
        vector<bool> visited(V, false);
        
        for(int i = 0; i<V; i++) {
            if(!visited[i] && isCycleBFS(adj, V, i, visited)) {
                return true;
            }
        }
        
        return false;
        
    }
};
```
- [Table of Contents](#table-of-contents)

### Using DSU

-  **Intution :-**

The code detects cycles in an undirected graph using the Disjoint Set Union (DSU) data structure. It employs path compression in the `find` function to keep the tree flat and improve efficiency. The `unionSets` function merges two sets, using union by rank to attach smaller trees under larger ones, minimizing tree height. As it processes each edge, it checks if both vertices belong to the same set (indicating a cycle). If any edge connects nodes already in the same set, a cycle is detected; otherwise, no cycle is present.



```cpp
class Solution {
public:
    vector<int> parent; // `parent` array where each node points to its parent
    vector<int> rank;   // `rank` array to keep track of the tree depth for union by rank

    // Find function with path compression
    int find(int node) {
        if (parent[node] == node) 
            return node;
        
        // Path compression: flatten the structure by making every node point directly to the root
        return parent[node] = find(parent[node]);
    }

    // Union function with union by rank
    void unionSets(int setA, int setB) {
        int rootA = find(setA);
        int rootB = find(setB);
    
        if (rootA == rootB) 
            return; // They are already in the same set
        
        // Union by rank: attach the smaller tree under the root of the larger tree
        if (rank[rootA] > rank[rootB]) {
            parent[rootB] = rootA;
        } else if (rank[rootA] < rank[rootB]) {
            parent[rootA] = rootB;
        } else {
            parent[rootB] = rootA;
            rank[rootA]++; // Increase rank only when two trees of the same rank are merged
        }
    }

    // Function to detect a cycle in an undirected graph using DSU
    bool detectCycle(int vertexCount, vector<int> adj[]) {
        parent.resize(vertexCount);
        rank.resize(vertexCount, 0);
        
        // Initialize parent array: each node is its own parent initially
        for (int i = 0; i < vertexCount; i++) 
            parent[i] = i;
        
        // Iterate over each vertex
        for (int u = 0; u < vertexCount; u++) {
            // Check all adjacent vertices of `u`
            for (int v : adj[u]) {
                // Ensure each edge is processed only once
                if (u < v) {
                    if (find(u) == find(v)) 
                        return true; // A cycle is detected
                    else 
                        unionSets(u, v);
                }
            }
        }
        
        return false; // No cycle detected
    }
};
```
- [Table of Contents](#table-of-contents)


## Cycle Detection in a directed graph Using DFS
-  **Intution :-**
To detect cycles in a directed graph using DFS, we track nodes with two states: those that are fully processed (visited) and those currently in the recursion stack (inRecursion). During DFS traversal, if we encounter a node that is already in the recursion stack, a cycle is present. Nodes are marked as in the recursion stack when explored and unmarked when fully processed. This approach ensures that we detect back edges, which signify cycles in the directed graph. Each node is checked to ensure all graph components are covered.

```cpp
class Solution {
  public:
    
    bool isCycleDFS(vector<int> adj[], int u, vector<bool>& visited, vector<bool>& inRecursion) {

        visited[u] = true;
        inRecursion[u] = true;
        
        
        for(int &v : adj[u]) {
            //if not visited, then we check for cycle in DFS
            if(visited[v] == false && isCycleDFS(adj, v, visited, inRecursion))
                return true;
            else if(inRecursion[v] == true)
                return true;
        }
        
        inRecursion[u] = false;
        return false;
        
    }
    
    // Function to detect cycle in a directed graph.
    bool isCyclic(int V, vector<int> adj[]) {
        vector<bool> visited(V, false);
        vector<bool> inRecursion(V, false);
        
        for(int i = 0; i<V; i++) {
            if(!visited[i] && isCycleDFS(adj, i, visited, inRecursion))
                return true;
        }
        
        return false;
    }
};
```
- [Table of Contents](#table-of-contents)

## Topological Sort

Topological sort is implemented only in `Directed Acyclic Graph`.

### Using DFS and stack


- **Intution:-**

To perform topological sorting using DFS, we recursively explore each vertex and its neighbors, marking nodes as visited. As we finish processing all neighbors of a node, we push the node onto a stack. This stack captures nodes in reverse topological order because nodes are added after all their descendants are processed. After completing the DFS for all vertices, the stack is emptied to produce the topologically sorted order. This ensures that each vertex appears before all vertices it directs to in the final order.

```cpp
class Solution
{
	public:
	
	void DFS(vector<int> adj[], int u, vector<bool>& visited, stack<int>& st) {
	    visited[u] = true;
	    
	    
	    //pehle mere ('u' ke node ke ) bachho ko daalo
	    for(int &v : adj[u]) {
	        if(!visited[v])
	            DFS(adj, v, visited, st);
	    }
	    
	    
	    //ab mujhe daalo stack me
	    st.push(u);
	    
	}
	
	//Function to return list containing vertices in Topological order. 
	vector<int> topoSort(int V, vector<int> adj[]) 
	{
	    vector<bool> visited(V, false);
	    stack<int> st;
	    
	    for(int i = 0; i<V; i++) {
	        if(!visited[i])
	            DFS(adj, i, visited, st);
	    }
	    
	    vector<int> result;
	    
	    while(!st.empty()) {
	        result.push_back(st.top());
	        st.pop();
	    }
	    
	    return result;
	}
};
```
- [Table of Contents](#table-of-contents)

### Using BFS (KAHN's algorithm)

- **Intution:-**

To perform topological sorting using Kahn's algorithm (BFS), we first compute the in-degree of each vertex, representing the number of incoming edges. Nodes with zero in-degrees (no incoming edges) are added to a queue. We then process each node from the queue, adding it to the result list and decrementing the in-degree of its neighbors. If any neighbor’s in-degree drops to zero, it is added to the queue. This process continues until all nodes are processed, yielding the topologically sorted order.
```cpp
class Solution {
	public:
	//Function to return list containing vertices in Topological order. 
	vector<int> topoSort(int N, vector<int> adj[])  {
	    queue<int> que;
	    vector<int> indegree(N, 0);
	    
	    //1
	    for(int u = 0; u<N; u++) {
	        for(int &v : adj[u]) {
	            indegree[v]++;
	        }
	    }
	    
	    //2. Fill que, indegree with 0
	    for(int i = 0; i<N; i++) {
	        if(indegree[i] == 0) {
	            que.push(i);
	        }
	    }
	    
	    //3. Simple BFS
	    vector<int> result;
	    while(!que.empty()) {
	        int u = que.front();
	        result.push_back(u);
	        que.pop();
	        
	        for(int &v : adj[u]) {
	            indegree[v]--;
	            
	            if(indegree[v] == 0) {
	                que.push(v);
	            }
	            
	        }
	    }
	    
	    return result;
	}
};
```
- [Table of Contents](#table-of-contents)


## Cycle Detection in a directed graph Using BFS (Kahn's algorithm)

- **Intution:-**

This code detects cycles in a directed graph using Kahn's algorithm. It first calculates the in-degrees of all nodes. Nodes with zero in-degrees are enqueued for processing. As nodes are processed, their neighbors' in-degrees are decremented, and if any neighbor's in-degree reaches zero, it's enqueued. If the total number of processed nodes equals the number of nodes in the graph, there are no cycles; otherwise, a cycle exists.
```cpp
class Solution {
  public:
    // Function to detect cycle in a directed graph.
    bool isCyclic(int N, vector<int> adj[]) {
        queue<int> que;
	    vector<int> indegree(N, 0);
	    int count = 0;
	    //1
	    for(int u = 0; u<N; u++) {
	        for(int &v : adj[u]) {
	            indegree[v]++;
	        }
	    }
	    
	    //2. Fill que, indegree with 0
	    for(int i = 0; i<N; i++) {
	        if(indegree[i] == 0) {
	            que.push(i);
	            count++;
	        }
	    }
	    
	    //3. Simple BFS
	    while(!que.empty()) {
	        int u = que.front();
	        que.pop();
	        
	        for(int &v : adj[u]) {
	            indegree[v]--;
	            
	            if(indegree[v] == 0) {
	                que.push(v);
	                count++;
	            }
	            
	        }
	    }
	    
	    return count != N;
    }
};
```
- [Table of Contents](#table-of-contents)

## Is Graph bipartite
### Using DFS

- **intution:-**

The code checks if a graph is bipartite using Depth-First Search (DFS). It colors each node with one of two colors while ensuring that no two adjacent nodes share the same color. Starting from uncolored nodes, it recursively colors adjacent nodes with the opposite color. If at any point adjacent nodes end up with the same color, the graph is not bipartite. If all nodes can be successfully colored without conflicts, the graph is bipartite.
```cpp []
class Solution {
public:

    bool dfsCheckBipartite(vector<int> adjacencyList[], int currentNode, vector<int>& colors, int currentColor) {
        colors[currentNode] = currentColor; // Color the current node

        // Traverse all adjacent nodes
        for(int &neighbor : adjacencyList[currentNode]) {

            // If the adjacent node has the same color, graph is not bipartite
            if(colors[neighbor] == colors[currentNode])
                return false;

            // If the adjacent node hasn't been colored yet
            if(colors[neighbor] == -1) {

                int newColor = 1 - currentColor;

                // Recursively check if the graph can be bipartite
                if(!dfsCheckBipartite(adjacencyList, neighbor, colors, newColor))
                    return false;
            }
        }

        return true;
    }

	bool isBipartite(int numberOfVertices, vector<int> adjacencyList[]) {

	    vector<int> colors(numberOfVertices, -1); // No node is colored at the start

	    // 1 represents one color (e.g., red)
	    // 0 represents the other color (e.g., green)

	    for(int i = 0; i < numberOfVertices; i++) {
	        // If the node hasn't been colored, start a DFS from it
	        if(colors[i] == -1) {
	            if(!dfsCheckBipartite(adjacencyList, i, colors, 1))
	                return false;
	        }
	    }

	    return true;
	}
};
```
- [Table of Contents](#table-of-contents)

### Using BFS

- **Intution:-**

The code checks if a graph is bipartite using Breadth-First Search (BFS). It colors nodes with two colors, ensuring adjacent nodes have different colors. Starting from uncolored nodes, BFS explores each node's neighbors, coloring them with the opposite color and checking for conflicts. If any adjacent nodes end up with the same color, the graph is not bipartite. If all nodes are successfully colored without conflicts, the graph is bipartite.

```cpp []
class Solution {
public:

    bool bfsCheckBipartite(vector<int> adjacencyList[], int startNode, vector<int>& colors, int initialColor) {
        colors[startNode] = initialColor; // Color the start node
        
        queue<int> nodeQueue;
        nodeQueue.push(startNode);
        
        while(!nodeQueue.empty()) {
            int currentNode = nodeQueue.front();
            nodeQueue.pop();
            
            // Traverse all adjacent nodes
            for(int &neighbor : adjacencyList[currentNode]) {
                if(colors[neighbor] == colors[currentNode]) {
                    return false; // If an adjacent node has the same color, the graph is not bipartite
                } else if(colors[neighbor] == -1) { // If the adjacent node hasn't been colored yet
                    colors[neighbor] = 1 - colors[currentNode]; // Assign the opposite color to the neighbor
                    nodeQueue.push(neighbor);
                }
            }
        }
        
        return true;
    }

	bool isBipartite(int numberOfVertices, vector<int> adjacencyList[]){
	    
	    vector<int> colors(numberOfVertices, -1); // No node is colored at the start
	    
	    // 1 represents one color (e.g., red)
	    // 0 represents the other color (e.g., green)
	    
	    for(int i = 0; i < numberOfVertices; i++) {
	        // If the node hasn't been colored, start a BFS from it
	        if(colors[i] == -1) {
	            if(!bfsCheckBipartite(adjacencyList, i, colors, 1))
	                return false;
	        }
	    }
	    
	    return true;
	}
};
```
- [Table of Contents](#table-of-contents)


## Disjoint Set Union (DSU)

### Normal (DSU)

- **Intution:-**

This code implements the Disjoint Set Union (DSU) data structure with path compression and union by rank. The `findSet` function locates the root of the set containing a given element and optimizes future queries by flattening the structure. The `unionSets` function merges two sets by linking one root to another, effectively combining the sets. Path compression in `findSet` helps keep the tree flat, improving efficiency. The overall goal is to efficiently manage and query disjoint sets.

```cpp []
// Function to find the representative (root) of the set containing 'element'
// with path compression optimization.
int findSet(int parent[], int element) {
    // If 'element' is the root of the set, return it
    if (parent[element] == element) {
        return element;
    }
    
    
    return  findSet(parent, parent[element]);
}

// Function to unify (merge) the sets containing 'element1' and 'element2'
void unionSets(int parent[], int element1, int element2) {
    // Find the root of the sets containing 'element1' and 'element2'
    int root1 = findSet(parent, element1);
    int root2 = findSet(parent, element2);
    
    // If they are already in the same set, no need to unify
    if (root1 == root2) {
        return;
    }
    
    // Merge the set containing 'root1' into the set containing 'root2'
    // (or vice versa)
    parent[root1] = root2;
}
```
- [Table of Contents](#table-of-contents)

### Rank and Path Compression (DSU)


- **Intution:-**

The code implements the Disjoint Set Union (DSU) with path compression and union by rank. The `findSet` function efficiently locates the root of the set containing an element while applying path compression to flatten the tree for faster future queries. The `unionSets` function merges two sets by attaching the tree with the smaller rank under the tree with the larger rank, maintaining a balanced tree structure. This combination of techniques ensures that both union and find operations are nearly constant time. The primary goal is to efficiently manage and unify disjoint sets while minimizing tree height.

``` cpp
// `parent` stores the parent of each node. Initially, each node is its own parent.
vector<int> parent;
// `rank` stores the rank (or depth) of each set's tree. Used for union by rank.
vector<int> rank;

// Find function with path compression
int find(int node) {
    // If the node is its own parent, return it
    if (node == parent[node]) 
        return node;

    // Path compression: make the node's parent the root of the set
    return parent[node] = find(parent[node]);
}

// Union function with union by rank
void unionSets(int setA, int setB) {
    // Find the roots of the sets containing `setA` and `setB`
    int rootA = find(setA);
    int rootB = find(setB);

    // If both nodes are already in the same set, no need to union
    if (rootA == rootB) 
        return;

    // Union by rank: attach the smaller tree under the root of the larger tree
    if (rank[rootA] > rank[rootB]) {
        parent[rootB] = rootA;
    } else if (rank[rootA] < rank[rootB]) {
        parent[rootA] = rootB;
    } else {
        // If ranks are the same, make one root the parent of the other
        parent[rootB] = rootA;
        // Increase the rank of the new root
        rank[rootA]++;
    }
}
```
- [Table of Contents](#table-of-contents)


### Size and path Compression (DSU)

<a href = "DSU By Size.pdf">Pdf Notes</a>

**Intution:-**

The Disjoint Set Union (DSU) data structure efficiently manages a collection of non-overlapping sets. It employs **path compression** during the `find` operation to flatten the structure, reducing the time complexity for future queries. This ensures that each element points directly to the root, leading to nearly constant-time performance. Additionally, **union by size** merges smaller sets into larger ones, optimizing the overall tree height and maintaining efficiency. Together, these techniques make DSU highly effective for dynamic connectivity problems.

```cpp
class DSU {
public:
    DSU(int size) {
        parent.resize(size);
        setSize.resize(size, 1); // Initialize size of each set to 1
        for (int i = 0; i < size; ++i) {
            parent[i] = i; // Each element is its own parent initially
        }
    }

    // Find with path compression
    int find(int x) {
        if (parent[x] != x) {
            parent[x] = find(parent[x]); // Path compression
        }
        return parent[x];
    }

    // Union by size
    void unionBySize(int x, int y) {
        int rootX = find(x);
        int rootY = find(y);

        if (rootX != rootY) {
            // Union by size: attach the smaller tree under the larger tree
            if (setSize[rootX] < setSize[rootY]) {
                parent[rootX] = rootY;
                setSize[rootY] += setSize[rootX]; // Update size
            } else {
                parent[rootY] = rootX;
                setSize[rootX] += setSize[rootY]; // Update size
            }
        }
    }

private:
    std::vector<int> parent;
    std::vector<int> setSize; // To keep track of the size of each set
};
```

- [Table of Contents](#table-of-contents)

## Dijkstra Algorithm

Dijkstra's algorithm is used to find the shortest path from a single source vertex to all other vertices in a graph with non-negative edge weights. It's commonly applied in network routing protocols to determine the most efficient path for data packets. The algorithm is ideal for applications such as GPS navigation systems to calculate the shortest route, as well as in various optimization problems like project scheduling and resource allocation. It efficiently handles sparse graphs and is well-suited for scenarios where real-time pathfinding is required.

### Using Priority Queue (Min Heap)

- **intution:-**

Dijkstra's algorithm begins by initializing the distance to the source vertex as 0 and all other vertices as infinity, then it places the source vertex into a min-heap with its distance. As it processes the vertices, it always selects the vertex with the smallest known distance. For each vertex, the algorithm updates the distances to its neighboring vertices if a shorter path is found through the current vertex. This process repeats until all vertices are processed or the priority queue is empty. At the end, the algorithm provides the shortest distances from the source to all other vertices in the graph.


```cpp
class Solution {
public:
    // Function to find the shortest distance of all vertices from the source vertex S
    vector<int> dijkstra(int numVertices, vector<vector<int>> adj[], int source) {
        // Priority queue to store the vertex and its current shortest distance
        priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> minHeap;

        // Vector to store the shortest distance from the source to each vertex
        vector<int> shortestDistances(numVertices, INT_MAX);

        // Initialize the source vertex distance to 0 and push it into the priority queue
        shortestDistances[source] = 0;
        minHeap.push({0, source});

        // Process the priority queue
        while (!minHeap.empty()) {
            // Get the vertex with the smallest distance
            int currentDistance = minHeap.top().first;
            int currentNode = minHeap.top().second;
            minHeap.pop();

            // Iterate through all adjacent vertices
            for (auto &neighbor : adj[currentNode]) {
                int edgeWeight = neighbor[1];
                int adjacentNode = neighbor[0];

                // If a shorter path to the adjacent node is found
                if (currentDistance + edgeWeight < shortestDistances[adjacentNode]) {
                    // Update the shortest distance
                    shortestDistances[adjacentNode] = currentDistance + edgeWeight;
                    // Push the updated distance into the priority queue
                    minHeap.push({shortestDistances[adjacentNode], adjacentNode});
                }
            }
        }

        return shortestDistances;
    }
};
```

- [Table of Contents](#table-of-contents)


### Using Set

- **Intution:-**

In this implementation of Dijkstra's algorithm, a `set` is used to keep track of vertices and their current shortest distances. The algorithm starts by initializing the distance to the source vertex as 0 and all others as infinity, then it adds the source vertex to the set. As it processes vertices, it always selects the one with the smallest distance from the set. For each vertex, the algorithm updates the distances to its neighboring vertices if a shorter path is found. If the distance to a neighbor is updated, the old distance is removed from the set and the new distance is added. This process continues until all vertices are processed, resulting in the shortest paths from the source vertex to all other vertices.


```cpp
class Solution {
public:
    // Function to find the shortest distance of all vertices from the source vertex S
    vector<int> dijkstra(int numVertices, vector<vector<int>> adj[], int source) {
        // Set to keep track of vertices and their current shortest distance
        set<pair<int, int>> minHeap;
        
        // Vector to store the shortest distance from the source to each vertex
        vector<int> shortestDistances(numVertices, INT_MAX);

        // Initialize the source vertex distance to 0 and add it to the set
        shortestDistances[source] = 0;
        minHeap.insert({0, source});

        // Process the set
        while (!minHeap.empty()) {
            // Get the vertex with the smallest distance
            auto current = *minHeap.begin();
            int currentDistance = current.first;
            int currentNode = current.second;
            minHeap.erase(current);

            // Explore all adjacent vertices
            for (const auto& neighbor : adj[currentNode]) {
                int edgeWeight = neighbor[1];
                int adjacentNode = neighbor[0];

                // Check if a shorter path to the adjacent node is found
                if (currentDistance + edgeWeight < shortestDistances[adjacentNode]) {
                    // Remove the old distance from the set, if it exists
                    if (shortestDistances[adjacentNode] != INT_MAX) {
                        minHeap.erase({shortestDistances[adjacentNode], adjacentNode});
                    }
                    // Update the shortest distance
                    shortestDistances[adjacentNode] = currentDistance + edgeWeight;
                    // Add the updated distance to the set
                    minHeap.insert({shortestDistances[adjacentNode], adjacentNode});
                }
            }
        }

        return shortestDistances;
    }
};

```
- [Table of Contents](#table-of-contents)




## Bellman Ford Algorithm

Bellman-Ford algorithm is used to find the shortest paths from a single source vertex to all other vertices in a graph, even when the graph contains negative edge weights. It's particularly useful for detecting negative weight cycles, which can be critical for applications like financial arbitrage detection and route optimization in environments where costs can decrease. Unlike Dijkstra's algorithm, Bellman-Ford can handle graphs with negative weights but is slower in practice. It’s also used in network routing to handle scenarios where edge weights might not be positive, ensuring accurate path calculations in various financial and logistics applications.

![alt text](image.png)

**Intution:-**

This C++ code implements the Bellman-Ford algorithm to find the shortest paths from a source vertex to all other vertices in a weighted graph. It initializes distances from the source to all vertices as infinity, except for the source itself, which is set to zero. The algorithm relaxes all edges up to `numVertices - 1` times to update the shortest paths. Afterward, it checks for negative weight cycles by attempting one more relaxation; if any distance can still be reduced, a negative cycle is detected and `-1` is returned. Otherwise, it returns the vector of shortest distances from the source.

```cpp
class Solution {
public:
    vector<int> bellman_ford(int numVertices, vector<vector<int>>& edges, int source) {
        // Initialize distances from source to all vertices as infinity
        vector<int> distances(numVertices, 1e8);
        distances[source] = 0; // Distance from source to itself is zero
        
        // Relax all edges numVertices - 1 times
        for(int i = 1; i <= numVertices - 1; ++i) {
            for(const auto& edge : edges) {
                int startVertex = edge[0];
                int endVertex = edge[1];
                int weight = edge[2];
                
                // Update the distance if a shorter path is found
                if(distances[startVertex] != 1e8 && distances[startVertex] + weight < distances[endVertex]) {
                    distances[endVertex] = distances[startVertex] + weight;
                }
            }
        }
        
        // Check for negative weight cycles
        for(const auto& edge : edges) {
            int startVertex = edge[0];
            int endVertex = edge[1];
            int weight = edge[2];
            
            if(distances[startVertex] != 1e8 && distances[startVertex] + weight < distances[endVertex]) {
                return {-1}; // Negative cycle detected
            }
        }
        
        return distances;
    }
};
```
- [Table of Contents](#table-of-contents)

## Floyd Warshall Algorithm

The Floyd-Warshall algorithm is used to find the shortest paths between all pairs of vertices in a weighted graph, including those with negative edge weights. It’s useful for applications requiring comprehensive distance information between every pair of nodes, such as in transportation networks and urban planning for route optimization. This algorithm is commonly applied in scenarios involving network analysis, like in traffic management systems and communication networks. It’s also beneficial for problems where shortest paths need to be recalculated frequently. Although less efficient for very large graphs compared to other algorithms, its ability to handle negative weights makes it versatile.

**Intution:-**

This code implements the Floyd-Warshall algorithm to compute the shortest paths between all pairs of vertices in a graph. Initially, it replaces any `-1` entries in the `distanceMatrix` with `INT_MAX` to represent infinity for non-existent edges, except for self-loops. It then uses three nested loops to update the matrix with the shortest paths, considering each vertex as an intermediate point and ensuring that paths are updated if a shorter route is found through this intermediate. After computing the shortest paths, it converts `INT_MAX` values back to `-1` to indicate no path exists. This approach efficiently handles graphs with missing edges and potentially negative weights.

```cpp
class Solution {
public:
    void shortest_distance(vector<vector<int>>& distanceMatrix) {
        int numVertices = distanceMatrix.size();
        
        // Replace -1 with a large value to represent infinity
        for(int i = 0; i < numVertices; i++) {
            for(int j = 0; j < numVertices; j++) {
                if(distanceMatrix[i][j] == -1 && i != j) {
                    distanceMatrix[i][j] = INT_MAX;
                }
            }
        }
        
        // Floyd-Warshall algorithm to find shortest paths
        for(int k = 0; k < numVertices; k++) {
            for(int i = 0; i < numVertices; i++) {
                for(int j = 0; j < numVertices; j++) {
                    if(distanceMatrix[i][k] != INT_MAX && distanceMatrix[k][j] != INT_MAX) {
                        distanceMatrix[i][j] = min(distanceMatrix[i][j], distanceMatrix[i][k] + distanceMatrix[k][j]);
                    }
                }
            }
        }
        
        // Replace large values back to -1 to represent no path
        for(int i = 0; i < numVertices; i++) {
            for(int j = 0; j < numVertices; j++) {
                if(distanceMatrix[i][j] == INT_MAX) {
                    distanceMatrix[i][j] = -1;
                }
            }
        }
    }
};
```

- [Table of Contents](#table-of-contents)

## Minimum Spannig Tree (MST) || (Minimum weight spanning tree)

A Minimum Spanning Tree (MST) is a subset of the edges in a connected, undirected graph that connects all vertices together `without any cycles`, and with the minimal possible total edge weight. The MST is used to ensure that all points in a network are connected with the least total cost, making it fundamental in network design, such as designing the layout of electrical grids, telecommunications, or computer networks. It also finds applications in clustering algorithms, where it helps in organizing data into clusters with minimal inter-cluster distances. Additionally, MST algorithms are utilized in optimizing road and transportation networks, creating efficient routing systems, and solving various optimization problems in operations research. The most common algorithms to find MSTs include Kruskal's and Prim's algorithms, both of which are designed to handle various types of graphs efficiently.


### Prim's Algorithm

**Intution:-**

The Prim's algorithm begins by initializing a priority queue (min-heap) to store edges and a boolean array to track which vertices have been included in the Minimum Spanning Tree (MST). The algorithm repeatedly extracts the edge with the smallest weight from the heap, connecting a vertex that hasn't yet been added to the MST. When an edge is selected, its weight is added to the total weight, and the corresponding vertex is marked as included in the MST. The algorithm then explores all adjacent vertices of the newly added vertex, pushing those not already in the MST into the heap along with their edge weights. This process continues until all vertices are included in the MST, resulting in the total weight representing the sum of the edges in the MST.

Prim's algorithm is a greedy algorithm used to find the Minimum Spanning Tree (MST) of a connected, undirected graph. The algorithm starts with a single vertex and grows the MST by repeatedly adding the smallest edge that connects a vertex in the tree to a vertex outside the tree. It initializes the MST with one vertex and progressively adds edges, ensuring that no cycles are formed. This process continues until all vertices are included in the MST. The result is a tree that connects all vertices with the minimum total edge weight.

```cpp
class Solution
{
    typedef pair<int, int> Edge; // Using Edge to represent weight and vertex
public:
    // Function to find the sum of weights of edges of the Minimum Spanning Tree
    int spanningTree(int numVertices, vector<vector<int>> adjacencyList[]) {
        priority_queue<Edge, vector<Edge>, greater<Edge>> minHeap; // Min-heap to store edges
        minHeap.push({0, 0}); // Start from vertex 0 with weight 0
        vector<bool> inMST(numVertices, false); // Track vertices included in MST
        int totalWeight = 0; // Sum of weights of the edges in the MST
        
        while (!minHeap.empty()) {
            auto currentEdge = minHeap.top(); // Get the edge with the smallest weight
            minHeap.pop();
            
            int edgeWeight = currentEdge.first; // Weight of the edge
            int currentNode = currentEdge.second; // Current vertex
            
            if (inMST[currentNode]) // If the vertex is already in MST, skip it
                continue;
            
            inMST[currentNode] = true; // Include this vertex in the MST
            totalWeight += edgeWeight; // Add edge weight to the total
            
            // Explore adjacent vertices
            for (auto &neighbor : adjacencyList[currentNode]) {
                int adjacentVertex = neighbor[0]; // Neighbor vertex
                int neighborWeight = neighbor[1]; // Weight of the edge to the neighbor
                
                if (!inMST[adjacentVertex]) { // If neighbor is not yet in MST
                    minHeap.push({neighborWeight, adjacentVertex}); // Push to the min-heap
                }
            }
        }
        
        return totalWeight; // Return the total weight of the MST
    }
};
```
- [Table of Contents](#table-of-contents)


### Kruskal Algorithm

**Intution:-**

This code implements Kruskal's algorithm to find the Minimum Spanning Tree (MST) of a graph using a Disjoint Set Union (DSU) structure. It initializes parent and rank arrays to manage the connected components of the graph. The `find` function uses path compression to efficiently locate the root of a node, while the `unionSets` function merges two sets based on their ranks. The edges are extracted from the adjacency list, sorted by weight, and processed to build the MST. Finally, the total weight of the edges in the MST is returned.

Kruskal's algorithm is a greedy algorithm used to find the Minimum Spanning Tree (MST) of a connected, undirected graph. The algorithm operates by sorting all the edges of the graph in non-decreasing order of their weights. It then iteratively adds the smallest edge to the MST, provided that it does not form a cycle with the edges already included in the MST. This process continues until there are ( V - 1 ) edges in the MST, where ( V ) is the number of vertices in the graph. The result is a tree that connects all vertices with the minimum possible total edge weight.

```cpp
class Solution {
public:
    // Disjoint Set Union (DSU) members
    vector<int> parent; // Parent array for union-find
    vector<int> rank;   // Rank array for union optimization

    // Find the root of the node with path compression
    int find(int node) {
        if (node == parent[node])
            return node;
        return parent[node] = find(parent[node]);
    }

    // Union the two sets
    void unionSets(int node1, int node2) {
        int root1 = find(node1);
        int root2 = find(node2);

        if (root1 == root2) 
            return;

        if (rank[root1] > rank[root2]) {
            parent[root2] = root1;
        } else if (rank[root1] < rank[root2]) {
            parent[root1] = root2;
        } else {
            parent[root1] = root2;
            rank[root2]++;
        }
    }

    // Kruskal's algorithm to find the Minimum Spanning Tree (MST)
    int kruskalMST(vector<vector<int>>& edges) {
        int totalWeight = 0; // Total weight of the MST

        for (auto& edge : edges) {
            int vertex1 = edge[0];
            int vertex2 = edge[1];
            int weight = edge[2];

            int root1 = find(vertex1);
            int root2 = find(vertex2);

            if (root1 != root2) {
                unionSets(vertex1, vertex2);
                totalWeight += weight; // Add weight to the total
            }
        }

        return totalWeight; // Return the total weight of the MST
    }

    // Function to find the sum of weights of edges of the Minimum Spanning Tree
    int spanningTree(int numVertices, vector<vector<int>> adj[]) {
        // Initialize parent and rank arrays
        parent.resize(numVertices);
        rank.resize(numVertices, 0);

        for (int i = 0; i < numVertices; i++)
            parent[i] = i; // Each vertex is its own parent initially

        vector<vector<int>> edges; // Store all edges

        // Build the edges list from adjacency list
        for (int i = 0; i < numVertices; i++) {
            for (auto& neighbor : adj[i]) {
                int vertex = i;
                int adjacentVertex = neighbor[0];
                int weight = neighbor[1];

                edges.push_back({vertex, adjacentVertex, weight});
            }
        }

        // Sort edges by weight
        sort(edges.begin(), edges.end(), [](const auto& edge1, const auto& edge2) {
            return edge1[2] < edge2[2];
        });

        // Apply Kruskal's algorithm
        return kruskalMST(edges);
    }
};

```
- [Table of Contents](#table-of-contents)


### KosaRaju's Algorithm

**Intution:-**

Kosaraju's algorithm identifies strongly connected components in a directed graph by leveraging depth-first search (DFS) in two main passes. The first pass involves performing DFS on the original graph to determine the finishing order of nodes, which are then pushed onto a stack. In the second pass, the graph is transposed, reversing all edges, and DFS is performed again, but this time in the order defined by the stack. Each time a new DFS is initiated from a node, it marks all reachable nodes as part of the same strongly connected component. The algorithm's efficiency stems from its systematic exploration of nodes and their relationships, ensuring that all nodes in a strongly connected component are identified together. This two-phase approach efficiently captures the interconnected nature of nodes within the graph.

```cpp
class Solution
{
public:
    void fillOrder(int node, vector<vector<int>>& adjacencyList, vector<bool>& visited, stack<int>& nodeStack) {
        visited[node] = true;

        for (int& neighbor : adjacencyList[node]) {
            if (!visited[neighbor]) {
                fillOrder(neighbor, adjacencyList, visited, nodeStack);
            }
        }

        nodeStack.push(node);
    }

    void dfsOnReversedGraph(int node, vector<vector<int>>& reversedAdjacencyList, vector<bool>& visited) {
        visited[node] = true;

        for (int& neighbor : reversedAdjacencyList[node]) {
            if (!visited[neighbor]) {
                dfsOnReversedGraph(neighbor, reversedAdjacencyList, visited);
            }
        }
    }

    // Function to find number of strongly connected components in the graph.
    int kosaraju(int vertexCount, vector<vector<int>>& adjacencyList) {
        stack<int> nodeStack;
        vector<bool> visited(vertexCount, false);

        // Step 1: Fill nodes in stack according to their finishing times
        for (int i = 0; i < vertexCount; i++) {
            if (!visited[i]) {
                fillOrder(i, adjacencyList, visited, nodeStack);
            }
        }

        // Step 2: Create the reversed graph
        vector<vector<int>> reversedAdjacencyList(vertexCount);
        for (int u = 0; u < vertexCount; u++) {
            for (int& v : adjacencyList[u]) {
                reversedAdjacencyList[v].push_back(u);
            }
        }

        int stronglyConnectedComponentsCount = 0;

        // Step 3: Process all vertices in order defined by stack
        visited = vector<bool>(vertexCount, false);
        while (!nodeStack.empty()) {
            int node = nodeStack.top();
            nodeStack.pop();
            if (!visited[node]) {
                dfsOnReversedGraph(node, reversedAdjacencyList, visited);
                stronglyConnectedComponentsCount++;
            }
        }

        return stronglyConnectedComponentsCount;
    }
};

```

- [Table of Contents](#table-of-contents)

## Euler Path and Circuit

Euler paths and Euler circuits have distinct properties that define their existence within a graph:

**Euler Path Properties:**
1. An Euler path traverses every edge of a graph exactly once but does not necessarily return to the starting vertex.
2. It exists if and only if exactly zero or two vertices have an odd degree. If there are zero odd-degree vertices, the path can start and end at the same vertex; if there are two, it will start at one and end at the other.

**Euler Circuit Properties:**
1. An Euler circuit is a specific type of Euler path that starts and ends at the same vertex, covering every edge exactly once.
2. It exists if and only if all vertices in the graph have an even degree, ensuring that every time a vertex is entered, it can also be exited.

These properties help in determining the feasibility of traversing the graph in an Eulerian manner.

<a href = "EulerianGraphs-Part-1.pdf">Pdf Notes</a>

**Intution:-**

The approach in the code involves determining the Eulerian properties of a graph. First, it checks if all vertices with non-zero degrees are connected using a depth-first search (DFS) starting from a vertex with a non-zero degree. If not all such vertices are connected, the graph is classified as non-Eulerian. Next, it counts the number of vertices with odd degrees. If more than two vertices have odd degrees, the graph is again deemed non-Eulerian. If exactly two vertices have odd degrees, the graph is classified as semi-Eulerian, indicating it has an Euler path. Finally, if all vertices have even degrees, the graph is identified as having an Euler circuit.

```cpp
class Solution {
public:

    void depthFirstSearch(vector<int> adjacencyList[], int vertex, vector<bool>& visited) {
        visited[vertex] = true;
        
        for(auto neighbor = adjacencyList[vertex].begin(); neighbor != adjacencyList[vertex].end(); neighbor++) {
            if(!visited[*neighbor]) {
                depthFirstSearch(adjacencyList, *neighbor, visited);
            }
        }
    }

    bool areAllNonZeroDegreeVerticesConnected(int totalVertices, vector<int> adjacencyList[]) {
        vector<bool> visited(totalVertices, false);
        
        // Find a vertex with a non-zero degree
        int startingVertex = -1;
        for(int i = 0; i < totalVertices; i++) {
            if(adjacencyList[i].size() != 0) {
                startingVertex = i;
                break;
            }
        }
        
        // Start DFS traversal from a vertex with a non-zero degree
        depthFirstSearch(adjacencyList, startingVertex, visited);
        
        // Check if all non-zero degree vertices were visited
        for(int i = 0; i < totalVertices; i++) {
            if(!visited[i] && adjacencyList[i].size() > 0)
                return false;
        }
        return true;
    }

	int checkEulerianProperties(int totalVertices, vector<int> adjacencyList[]) {
	    
	    // Check if all non-zero degree vertices are connected
	    if(!areAllNonZeroDegreeVerticesConnected(totalVertices, adjacencyList)) {
	        return 0; // Non-Eulerian
	    }
	    
	    // Count vertices with odd degrees
	    int oddDegreeCount = 0;
	    for(int i = 0; i < totalVertices; i++) {
	        if(adjacencyList[i].size() % 2 != 0) {
	            oddDegreeCount++;
	        }
	    }
	    
	    // If the count of odd degree vertices is more than 2, then the graph is not Eulerian
        if (oddDegreeCount > 2)
            return 0; // Non-Eulerian
        
        if(oddDegreeCount == 2) {
            return 1; // Semi-Eulerian (It has only an Euler Path)
        }
        
        return 2; // (Euler Circuit)
	}
};

```
- [Table of Contents](#table-of-contents)