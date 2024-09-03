# Graph

## Cycle Detection In Undiected Graph

### Using DFS

```cpp
class Solution {
  public:
    bool dfs(vector<int>adj[],vector<bool>&vis,int parent,int u){
        
        vis[u] = true;
        for(int &v: adj[u]){
            if( v == parent )continue; //  don't visit the parent
            if( vis[v] )return true; //cycle detected
            bool flag = dfs(adj,vis,u,v);
            if(flag){
                return true;
            }
        }
        return false;
    }
    // Function to detect cycle in an undirected graph.
    bool isCycle(int V, vector<int> adj[]) {
        // Code here
        // V is the number of vertices
        vector<bool>vis(V,false);
        for(int i = 0; i < V; i++){
            if(!vis[i] && dfs(adj,vis,-1,i)){
                return true;
            }
        }
        return false;
    }
};
```

### Using BFS

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

## Cycle Detection in a directed graph Using DFS

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

## Topological Sort

Topological sort is implemented only in `Directed Acyclic Graph`.

### Using DFS and stack

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

### Using BFS (KAHN's algorithm)

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


## Cycle Detection in a directed graph Using BFS (Kahn's algorithm)
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

## Is Graph bipartite
### Using the DFS

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

### Using BFS

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