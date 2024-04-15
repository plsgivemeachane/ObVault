# 1. Chuỗi con xuất hiện K lần

## - Task:

![[Pasted image 20240412220738.png]]

## - Example:

![[Pasted image 20240412220802.png]]

---

- Nah i coded with 100+ bugs lol
- Also this is the code :DD
```cpp
#include <bits/stdc++.h>
#define int long long
#define main signed main
#define fast ios_base::sync_with_stdio(0); cin.tie(0); cout.tie(0);
#define fileinp ".inp"
#define fileout ".out"
#define io freopen(fileinp, "r", stdin); freopen(fileout, "w", stdout);
#define solveinput input(); solve();
#define set1(mask, i) mask | (1 << i)
#define set0(mask, i) mask & ~ ( 1 << i )
#define fill(i) (1 << i) - 1
#define is1(mask, i) mask & (1 << i)
#define oo 1e18
using namespace std;
const int N = 1e5 + 5;
const int mod = 1e6 + 9; // (Array maximum sized)
const int P = 27; // Why not :DD

int cnt[mod];
int Hashes[N];
int bases[N];

int n, k;
string s;

void build() {

    bases[0] = 1;
    for(int i = 1;i <= n;i++) {
        bases[i] = (bases[i - 1] * P) % mod;
    }

    Hashes[0] = s[0] - 'a' + 1;
    for(int i = 1;i < n;i++) { // Forward hashes (Backward or foward does matter??)
        Hashes[i] = (Hashes[i - 1] * P + s[i] - 'a' + 1) % mod;
    }
}

int getHashes(int i, int j) {
    if (i == 0) return Hashes[j];
    int ans = (Hashes[j] - (Hashes[i - 1] * bases[j - i + 1]) % mod) % mod;
    while (ans < 0)
        ans += mod;
    return ans;
}

bool ok(int length) {
    // Reset memorize count
    memset(cnt, 0, sizeof(cnt));
    // cnt.clear();
    // cout << length << endl;

    for(int i = 0;i <= n - length;i++) {
        // cout << i << endl;
        int CurrentStringHash = getHashes(i, i + length - 1);
        cnt[CurrentStringHash]++;
        if(cnt[CurrentStringHash] >= k) return true;
    }

    // for(int i = 0;i < mod;i++) {
    //     if(cnt[i] != 0) {
    //         cout << i << " " << cnt[i] << endl; 
    //     }
    // }

    return false;
}

void input() {
    cin >> n >> k;
    cin >> s;
}

void solve() {
    build();

    int l = 1, r = n;
    int ans = 0;
    while(l <= r) {
        int mid = (l + r) / 2; //* mid == length of the longest dub that match k times
        // cout << "Checked " << mid << endl;
        if(ok(mid)) {
            // It that accept then we can take further position
            l = mid + 1;
            ans = mid;
        } else r = mid - 1;
    }

    cout << ans;
}


main() {
    fast
    solveinput
    return 0;
}
```
