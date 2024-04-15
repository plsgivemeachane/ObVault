
Given n coins. each coin has `p[i]` chances 3of rolling heads.
find chances to state that has more than half of coins are heads

`dp[i][j]` is the current i coin has at least j heads

`state`:
	- if ith coin is heads then it need j - 1 heads at i - 1 so the state is `dp[i - 1][j - 1]`
	- if ith coin is tail then it need j heads at i - 1 so the state is `dp[i - 1][j]`
base cases:
	-