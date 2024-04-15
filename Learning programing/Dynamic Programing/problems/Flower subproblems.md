
Given an array from n element:
`[3, 1, 4, 2]` -> `3`

Showing how much increasing `subsequence` in that array
like there is this subsequence:
	`[3, 4], [1,2], [1, 4]`
`dp[i]` stand for how much increasing subsequence it has at the position i

if we had the array 1, 2, 3
the `dp[1]` must be 1 which when come to `dp[2]` has 3 because
3 > 1 and 3 > 2
