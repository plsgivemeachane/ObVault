Task: 
**
Đề bài cho một ma trận gồm n hàng m cột, chúng ta có thể thực hiện thao tác sau đây bao nhiêu lần cũng được: đổi chỗ 2 hàng với nhau(lưu ý là thứ tự các ở trong hàng không đổi

sau khi đã thực hiện thao tác đó thì mình sẽ bắt đầu đánh số các ô: Xét cột thứ nhất rồi đi từ trên xuống, xét cột thứ 2 rồi đi từ trên xuống, … xét cột thứ m và đi từ trên xuống.

Thì giá trị của bảng số là giá trị nhỏ nhất của độ chệnh lệch giữa 2 phần tử liên tiếp
**

Code:
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

int n, m;
int a[17][100001];
int cost1[17][17]; // For the normal row
int cost2[17][17]; // For last row :D
int dp[(1 << 17)][17]; // Mask | prev row

void input() {
    cin >> n >> m;
    for(int i = 0;i < n;i++) {
        for(int j = 0;j < m;j++) {
            cin >> a[i][j];
        }
    }

    // Precalculate cost1 and cost2
    for(int i = 0;i < n;i++) {
        for(int j = 0;j < n;j++) {
            cost1[i][j] = oo;
            cost2[i][j] = oo;

            for(int col = 0; col < m; col++) {
                int normal_cost = abs(a[i][col] - a[j][col]); // 2 row that are same
                cost1[i][j] = min(normal_cost, cost1[i][j]);
                if(col > 0) {
                    // special case
                    int last_row_cost = abs(a[i][col] - a[j][col - 1]);
                    cost2[i][j] = min(last_row_cost, cost2[i][j]);
                }
            }
        }
    }
}

void solve() {
    
    int result = 0;

    // For each pair of value || Where to start.
    for(int start = 0;start < n;start++) {
        
        // Reset the dp
        for(int current_mask = 0; current_mask <= fill(n); current_mask++) {
            for(int i = 0;i < n;i++) {
                dp[current_mask][i] = -oo; // For min finding
            }
        }

        dp[(1 << start)][start] = oo; // The starting point lol :DD

        for(int current_mask = 0; current_mask <= fill(n); current_mask++) {
            for(int current = 0;current < n;current++) {
                if(is1(current_mask, current)) {
                    // Can be use for calculate
                    for(int nxt = 0; nxt < n;nxt++) {
                        if(!(is1(current_mask, nxt))) {
                            int next_mask = set1(current_mask, nxt);
                            dp[next_mask][nxt] = max(dp[next_mask][nxt], min(
                                dp[current_mask][current],
                                cost1[current][nxt]
                            ));
                        }
                    }
                }
            }
        }


        // Last row calculation
        for(int i = 0;i < n;i++) {
            int mask = dp[fill(n)][i]; // If i is the last list that are inserted (answer)
            mask = min(mask, cost2[start][i]); // Cost from the last ith col and the starting point :DDD
            result = max(result, mask);
        }
    }

    cout << result << endl;
}


main() {
    fast
    solveinput
    return 0;
}
```
