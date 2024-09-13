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
- [Dijkstra Algorithm](#dijkstra-algorithm)
- [Dijkstra Algorithm Using Priority Queue (Min Heap)](#using-priority-queue-min-heap)






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


## Dijkstra Algorithm

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