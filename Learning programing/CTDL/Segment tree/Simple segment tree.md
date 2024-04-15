```cpp
long long get(long long id, long long l, long long r, long long u, long long v) {
    if(r < u or l > v) return -1000000000000000000;
    if(l >= u and r <= v){
        return t[id];
    }

    long long mid = (l + r) / 2;
    long long t1 = get(id * 2, l, mid, u, v);
    long long t2 = get(id * 2 + 1, mid + 1, r, u , v);
    return max(t1, t2);
}

void update(long long id, long long l, long long r, long long u, long long v) {
    if(u < l or u > r) return;
    if(l == r)
    {
        a[l] = v;
        t[id] = v;
        return;
    }
    long long mid = (l + r) / 2;
    update(id * 2, l, mid, u, v);
    update(id * 2 + 1, mid + 1, r, u, v);
    t[id] = max(t[id * 2], t[id * 2 + 1]);
}
```