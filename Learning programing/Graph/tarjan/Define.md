```cpp
void dfs(long u, long p) {

    id[u] = low[u] = ++cnt;

    long node = (p != 0); // If it not the root then surely will be a parent node connect to this node

    for(auto v : g[u]) if(v != p) {

        if(id[v]) low[u] = min(low[u], id[v]);

        else {

            dfs(v, u);

            low[u] = min(low[u], low[v]);

            if(low[v] == id[v]) {

                bridge++; // Id[v] with the current pos of v. Cause the lowest pos can v get is just v so v cannot get lower;

            }

  

            if(low[v] >= id[u]) {

                node++; // All the node bellow v cannot get up higher than their parent with is u but the same time the max height it get is v:>>

            }

        }

    }

  

    if(node >= 2) {

        // More than 2 connected component are lying in 2 separated way toward this node mean that this fuking node if he lose then he will deconnected all of them

        ap++;

    }

}
```