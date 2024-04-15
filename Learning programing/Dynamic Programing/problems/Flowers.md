_first time trying to think about it_

- Chiều cao của các bông hoa còn lại tăng dần từ trái sang phải.
- Largest sum of hoa
- `N <= 2*10^5` so cannot using the normal 2 for dps

`dp[i]` is the sum of all smallest flowers that able to be wokup

There are 2 state that we can use
- Pick up the flower and add the sum to the nearest `dp[i]`
- Remain the flower to be increasing

`dp[i]` must somehow make the thing flowable or in the correct state
like 3 1 4 2
we only have 2 options:
- remove 3 and 4
- remove 1 and 2
`dp[i] = min(dp[i], `

---
3 1 4 2

haiz

--- 
`dp[i]` is the largest flowers can get into i