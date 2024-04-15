---
tags:
  - hash
  - normal
  - data_structure
  - string_manipulation
---
## What is a hash function?
- In real world example, a hash function is a function that taken an input of a string and convert it into a number (or bits, hex) that valid these 3 restriction
	- 1. It must be deterministic
		- _same input always has the same output_
	- 2. *Fixed* length output
		- _for every input_
	- 3. Irreverible output
		- _cannot reverse to original text_
	- (At that mean (a + b) % 10 is also a valid hash)
- But in competitive programing it a little different
- The usage of hashing in competitive programing doesn't need Fixed length output or Irreversible output because it main idea to compare 2 string as fast as possible (commonly O(1))
- The only restriction of hashing in competitive programing that it has less (or very less) `collision`
- A `collision` mean if 2 string are different but their hash are the same.
- Right now the most popular hashing aglorithm is **polynomial rolling hash** (_Hàm băm đa thức_)
	- 1. It very efficiency (Fast to calculate)
	- 2. It has **Rolling Update** (_You can calculate hash of smaller part of a string without need to recalculate the whole thing_)
	- 3. **Incremental Calculation** (_Tính toán tịnh tiến_)
		- _**efficiently** compute a hash value for a sliding window of data_
- Then we see how the function works:
	- 1. Compute the powers of P (the prime) from 1 to size of the windows
	- 2. It then computes the hash value of the first window using another for loop that iterates over the characters in the first window.
	- 3. - Finally, the function uses another for loop to compute the hash values of the rest of the substrings. It first removes the contribution of the first character in the current window, shifts the window by **one** character, and adds the new character to the **hash**. It then stores the hash value of the current window in the hash_values list.
	- 3. returns the **hash_values** list, which contains the hash values of all substrings of length window_size in s.
- Nah come into interesting part (Code:D)
```cpp
long long compute_hash(string const &s)
{
    const int p = 31; // Some good prime usually larger than the alphabet (26)
    const int m = 1e9 + 9; // Modulo
    long long hash_value = 0; // the result
    long long p_pow = 1; // current p with power
    for (char c : s)
    {
        hash_value = (hash_value + (c - 'a' + 1) * p_pow) % m;
        p_pow = (p_pow * p) % m;
    }
    return hash_value;
}
```