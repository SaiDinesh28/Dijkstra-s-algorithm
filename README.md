//# Dijkstra-s-algorithm
#include<bits/stdc++.h>
using namespace std;

int main(){
	int t ;
	cin>>t;
	while(t--){
		int n,m;
		cin>>n>>m;
		vector<pair<int,int>>adj[n];
		for(int i=0;i<m;i++){
			int a,b,c;
			cin>>a>>b>>c;
			adj[a].push_back({b,c});
			adj[b].push_back({a,c});
		}
		int x; cin>>x;
		priority_queue<pair<int,int>>pq;
		pq.push(make_pair(0,x));
		vector<int>dist(n,INT_MAX);
		dist[x]=0;
		while(!pq.empty()){
                 int a=pq.top().first;
				 int b=pq.top().second;
				 pq.pop();
				 for(auto it:adj[b]){
                     if(a+it.second<dist[it.first]){
						 dist[it.first]=a+it.second;
						 pq.push(make_pair(dist[it.first],it.first));
					 }
				 }
		}
		for(auto it:dist) cout<<it<<" ";
	}
}
