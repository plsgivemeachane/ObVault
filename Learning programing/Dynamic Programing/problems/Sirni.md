[Sirni problems](https://oj.vnoi.info/problem/coci1617_r6_sirni)
#hard 

# 1.Understand the Problem

Given some card.
Find a way that every card has a match card that can be overlap
2 6 3 11
can be map 2 - 6; 6 - 3; 2 - 3

Every pair of card has a "value" of pair as the minimum of the divisor (Ex: 2 and 6 has 0)

The goal is picking so that the sum of those "value" is the smallest

The answer : 1;

The limit is < 10^5 _so it could be using binary search_

# 2.Identify overlaping problems
#hard 
Dynamic programing approch

## My approuch
- The dynamic array with be a 1D array that at the `dp[i]` will be the smallest "value" that card can have. Absolutely pair with other card
- So the brute force way is to use 2 loops for finding best card that fit into that card itself

## AI approuch

- Given the nature of the problem, we can observe that to find the optimal solution for a pair of cards, we need to consider the optimal solutions for pairs of cards that precede it.
- Therefore, we can define our subproblem as finding the minimum sum of values for pairs of cards up to a certain index in the given array.
- Let's denote the function `dp(i)` as the minimum sum of values for pairs of cards up to index `i` in the array.

# 3.Define the Recurrence Relation

_How the `dp[i]` related to other dps?_

As long as I know. If we know we need to find a divisor of "that" `dp[i]`. Why just make it to "know" if there is a divisor of "that"?

_If 6 has like 1 -> 6 divisor. How do we know that one of them "has" a divisor (stupid)_

It does not limit the rearrange them so we could sort?:
	Let try that out
	`[2, 3, 6, 11]`
	Then what the point?.
	

# 2. Different approuch
Graph approch