# Graphs: Assignment 1

## Task 1


**1. Create a theoretical graph using a pen and paper OR electronically. (2 points)**



![image](https://github.com/user-attachments/assets/3842fd19-a325-404f-8830-e6dd3471aacf)



## Task 2


**2. Implement the graph created in step 1 and apply breadth and depth-first search algorithms using C++. (6 points)**



```C++
#include <iostream>
#include <unordered_map>
#include <vector>
#include <queue>
#include <stack>
using namespace std;

class Graph {
public:
    unordered_map<char, vector<char>> adjList;

    void addEdge(char u, char v) {
        adjList[u].push_back(v);
        adjList[v].push_back(u); // because it's undirected
    }

    void BFS(char start) {
        unordered_map<char, bool> visited;
        queue<char> q;

        visited[start] = true;
        q.push(start);

        cout << "BFS Traversal: ";
        while (!q.empty()) {
            char current = q.front();
            q.pop();
            cout << current << " ";

            for (auto neighbor : adjList[current]) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    q.push(neighbor);
                }
            }
        }
        cout << endl;
    }

    void DFS(char start) {
        unordered_map<char, bool> visited;
        stack<char> s;

        s.push(start);

        cout << "DFS Traversal: ";
        while (!s.empty()) {
            char current = s.top();
            s.pop();

            if (!visited[current]) {
                visited[current] = true;
                cout << current << " ";

                for (auto neighbor : adjList[current]) {
                    if (!visited[neighbor]) {
                        s.push(neighbor);
                    }
                }
            }
        }
        cout << endl;
    }
};

int main() {
    Graph g;

    g.addEdge('A', 'B');
    g.addEdge('A', 'C');
    g.addEdge('B', 'D');
    g.addEdge('C', 'E');

    g.BFS('A');
    g.DFS('A');

    return 0;
}
```



## Task 3


**Compare both search algorithms in the context of Big O notations. (2 points)**



Comparatively speaking, under the context of Big O notations, both the BFS (breadth first search) and DFS (depth first search) algorithms had the same time complexity of O(V + E). In this case, V stands for the number of vertices, and E stands for the number of edges in the running of the code, as they visit each edge and verticy once.
