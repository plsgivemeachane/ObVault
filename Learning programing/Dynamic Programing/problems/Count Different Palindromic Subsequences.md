
Given a string s, return _the number of different non-empty palindromic subsequences in_ `s`. Since the answer may be very large, return it **modulo** `109 + 7`.

A subsequence of a string is obtained by deleting zero or more characters from the string.

A sequence is palindromic if it is equal to the sequence reversed.

Two sequences `a1, a2, ...` and `b1, b2, ...` are different if there is some `i` for which `ai != bi`.


---

# Solution

_`dp[i][j]` is the total of palins in the range of i to j - 1_

`dp[i][j]` need to plus in 2 different thing:
- Unique character (Ex: `aabb` has 2 unique char so it has 2 palins)
- The character that form the a_a which form another palins
- The a_a form has 3 different palins
	- aa which is one palins
	- a which is one palins
	- all the palins inside _ is a palins
	- all the palins has form a_a is a palins

So that we can construct the relation for `dp[i][j]` which this:
- if it can form and a_a mean `str[i] == str[j]`. We count 3 different case:
	- the case when there is no more `a` in `a_a` so the answer are all the palins that matches + all the palins that has `a_a` matches that and 2 palins as a and aa
	- the case 2 when there is 1 more `a` in `a_a` is the same at the first but notice when we approuch 2 a we already calculated case that only has `a` so there is only one left: `aaa`
	- The third case is there is 2 or more `a` character in the string
		- So the form will be `a_a_(can have more a)__a_a`
		- We already calculated the middle a so we only need to calculate 2 part lie on 2 side of a precalculated
- If not match then we will remove i, remove j, and remove i and j for finding palins and pass this part.
- All the case relation:
	- case 1: `dp[i][j] = 2 * dp[i + 1][j - 1] + 2`
	- case 2: `dp[i][j] = 2 * dp[i + 1][j - 1] + 1`
	- case 3: `dp[i][j] = ((*) 2 * dp[i + 1][j - 1] - (**)dp[next[i] + 1][prev[j] - 1]`
		- Explain: 
		- `(*)` The full part as like the first 
		- `(**)` The part that we are already calculated
---
# Base cases

- `dp[i][i] = 1`
- `dp[i][i + 1] = 2`