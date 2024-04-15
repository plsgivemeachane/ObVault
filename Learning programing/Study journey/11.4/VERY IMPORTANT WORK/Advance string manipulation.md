---
tags:
  - string_manipulation
  - hard
  - sequence
---
First we need to know about: [[Hashing function]]
_**If you dont then now continue to the problems**_
## Problems 1
I will exessively pass the heck of the first because it too easy. Nah I will do it :FiSmile:
Nah It just too bad

## Problems 2
_**(dont ask me why)**_

Problems: Cho một xâu 𝑆 và một xâu mẫu 𝑃. Xác định tất cả các vị trí xẫu hiện của xâu mẫu 𝑃 trong xâu 𝑆.

- Input: Gồm một số thử nghiệm, mỗi thử nghiệm gồm 3 dòng Dòng 1: ghi độ dài của xâu mẫu 𝑃; Dòng 2: ghi xâu mẫu 𝑃; Dòng 3: ghi xâu 𝑆. 
- Output: Đối với mỗi thử nghiệm, ghi tất cả các vị trí xuất hiện của xâu P trong xâu S. (vị trí của xâu S được đánh chỉ số bắt đầu từ 0). Giữa mỗi thử nghiệm ngăn cách nhau bởi một kí tự xuống dòng
Links: [Vnoi xau con](https://oj.vnoi.info/problem/substr)

Code:
```cpp
void solve() {
    // Precalculate base P
    // Assume not to large or it would be MLE
    // Nah P is not larger than 10 "Almost"
    bases[0] = 1;
    for(int i = 1;i < 1000001;i++) {
        bases[i] = (bases[i - 1] * P) % mod;
    }

    // Precalculate hash of b
    for(int i = b.size() - 1;i >= 0;i--) {
        hash_b = (hash_b * P + b[i]) % mod;
    }

    // Precalculate all hashsed of a
    for(int i = a.size() - 1;i >= 0;i--) {
        hash_a[i] = (hash_a[i + 1] * P + a[i]) % mod;
    }

    bool WillMeFindThatShit = false;

    if(a.size() < b.size()) {
        cout << "";
        return;
    }

    for(int i = 0;i <= a.size() - b.size();i++) {
        int check = (hash_a[i] - (hash_a[i + b.size()] * bases[b.size()]) % mod + mod) % mod;
        // cout << check << " " << hash_b << endl;
        if(check == hash_b) {
            cout << i + 1 << " ";
            WillMeFindThatShit = true;
        }
    }

    if(!WillMeFindThatShit) {
        cout << "";
        return;
    }

}
```


## Problems 3

Longest Palindrome.
Link: [VNOI Palindrome](https://oj.vnoi.info/problem/paliny)
Nah it crash
EZ peasy
Code:
```cpp

```