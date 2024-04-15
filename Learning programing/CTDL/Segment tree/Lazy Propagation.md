```cpp
void push(int id) {
    st[id * 2] += lazy[id];
    st[id * 2 + 1] += lazy[id];
    lazy[id * 2] += lazy[id];
    lazy[id * 2 + 1] += lazy[id];
    lazy[id] = 0;
}

void update(int id, int l, int r, int u, int v, int val) {
    if(l > v || r < u) {
        return;
    }

    if(u <= l and r <= v) {
        st[id] += val;
        lazy[id] += val;
        return;
    }

    push(id);

    int mid=(l + r) / 2;
    update(id * 2, l, mid, u, v, val);
    update(id * 2 + 1, mid + 1, r, u, v, val);
    st[id] = max(st[id * 2], st[id * 2 + 1]);
}

long long query(int id, int l,int r,int u, int v) {
    if(r < u || l > v) {
        // Out range 
        return -1e17;
    }

    if(u <= l and r <= v) {
        return st[id];
    }

    push(id);

    int mid = (l + r) / 2;
    return max(query(id * 2, l, mid, u, v), query(id * 2 + 1, mid + 1, r, u, v));
}
```