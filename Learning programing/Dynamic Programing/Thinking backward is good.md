#hard 
# 1. Some programing problems
### [Rearrang stick problems link](https://leetcode.com/problems/number-of-ways-to-rearrange-sticks-with-k-sticks-visible/)
### 1. [[Rearrang stick]] problems
- This problems provided n stick with k visible
- The subproblems isn't "What if we do the nth stick go first". but really it is "What if that stick is at last".
```c++
// Sample code
class Solution {

public:

    long f[1001][1001];

    int rearrangeSticks(int n, int k) {

        f[1][1] = 1;

        for(int i = 1;i <= n;i++) f[i][1] = 1;

        for(int i = 2;i <= n;i++) {

            for(int j = 1;j <= k;j++) {

                f[i][j] = (f[i - 1][j - 1] % 1000000007 + (i - 1) * f[i - 1][j] % 1000000007) % 1000000007;

            }

        }

        return f[n][k];

    }

};
```

## Solution
#normal 
	The solution is absolutely easy when we has the formula:
	 `f[i][j] = f[i - 1][j - 1] + (i - 1) * f[i - 1][j]`
	 The current canles is calculated with 
