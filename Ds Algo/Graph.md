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

## Cycle Detection in a directed graph
//TODO: