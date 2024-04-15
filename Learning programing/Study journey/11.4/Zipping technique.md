---
tags:
  - data_structure
  - normal
  - number
  - sequence
  - zip
---
# What it does
- It reduce the cost of calculate big number but you only matter the comparation prototype and you dont care about what that exact number is

# Implentment
_example_
```cpp
void solve() {
    for(int i = 0;i < n;i++) {
        zip.push_back(a[i]);
    }
    sort(zip.begin(), zip.end());
    for(int i = 0;i < n;i++) {
        int ranks = lower_bound(zip.begin(), zip.end(), a[i]) - zip.begin() + 1;
        zipped[i] = ranks;
    }
    //* Printing the numbers that are zipped
    for(int i = 0;i < n;i++) {
        cout << zipped[i] << " ";
    }
}
```

