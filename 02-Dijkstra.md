# Dijkstra

适用于单源最短路且边权非负。

```cpp
using PII = pair<long long, int>;
const long long INF = (1LL << 60);

vector<vector<pair<int,int>>> g(n);
vector<long long> dist(n, INF);
priority_queue<PII, vector<PII>, greater<PII>> pq;

dist[s] = 0;
pq.push({0, s});

while (!pq.empty()) {
    auto [d, u] = pq.top(); pq.pop();
    if (d != dist[u]) continue;

    for (auto [v, w] : g[u]) {
        if (dist[v] > d + w) {
            dist[v] = d + w;
            pq.push({dist[v], v});
        }
    }
}
```

常见优先队列实现复杂度 O((n+m)log n)。
