# Assignment solution 

I tried the code in two different ways 
in fst code I gave user input for one code 
In second code I took the input by default

*******


#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int maximalNetworkRank(int n, vector<vector<int>>& cables) {
    vector<int> degree(n); 
    vector<vector<int>> adjList(n); 
    int maxRank = 0;

    
    for (auto& cable : cables) {
        int u = cable[0], v = cable[1];
        adjList[u].push_back(v);
        adjList[v].push_back(u);
        degree[u]++;
        degree[v]++;
    }

    
    for (int u = 0; u < n; u++) {
        for (int v = u + 1; v < n; v++) {
            int rank = degree[u] + degree[v];
            if (find(adjList[u].begin(), adjList[u].end(), v) != adjList[u].end()) {
                rank--; 
            }
            maxRank = max(maxRank, rank);
        }
    }

    return maxRank;
}

int main() {
    int n = 4;
    vector<vector<int>> cables = {{0,1}, {0,3}, {1,2}, {1,3}};
    cout << maximalNetworkRank(n, cables) << endl; 
    return 0;
}



*******

#include <bits/stdc++.h>
using namespace std;

int ans(map<int, vector<int>>graph)
{
  vector<int> v;
  int maxi = -1;
  for (int i = 0; i < graph.size(); i++)
{
  v.push_back(graph[i].size());
  maxi = max(maxi, (int)graph[i].size());
}
  int cnt = 0;
  for (auto i : v)
{
  if (i == maxi)
  cnt++;
}
  return cnt;
}
int main()
{
  map<int, vector<int> > graph;
  int n,temp = 0;
  cin >> n;
  for(int i=0; i<n; i++)
{

  for(int j=0; j<2; j++)
{
  cin>>temp;
  graph[i].push_back(temp);

}
}
  cout << ans(graph);
  return 0;
}


input given 

n=4

0
1
0
3
1
2
1
3

output received

4.
