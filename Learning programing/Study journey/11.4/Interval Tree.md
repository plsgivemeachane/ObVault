---
tags:
  - normal
  - IT
  - data_structure
aliases:
  - IT
---
# Nah I already know this before but hell yeah will read the doc
---


## Interval Tree prototypes
- Low memory usage
- Easy install (for BIT)
- Log(n) time complexity (What we actually want)
- Solveable problems: #sequence #number 
---

## Example

### 1. IVITRI

Problems:
![](https://i.imgur.com/3kPpCtV.png)

- The problems describe that find 3 number that index of them are forward (Eg: 1, 2, 3) but the value are inverse (Eg: 3, 2, 1)
- Technique usage: #IT #data_structure #zip 

Solution
- The idea is each VITHE will contain 3 number. 1 number from left that greater than the current number. The number from the right that smaller than the current number. So we count how many pair of them for the current index
- like there are 5 numbers that less than the current value and 6 number that larger than current value
- Then the total pair of that current index is `5 * 6 = 30` pair
- Plus that all to the sum
Code:

```cpp

```

Notes:
- ![](https://i.imgur.com/Qx8kl9o.png)
- Remeber to index at 1! or it just dont wanna to work
