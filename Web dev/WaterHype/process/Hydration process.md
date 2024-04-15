# 1.Recomplie waterx file to javascript and HTML
#hard
### 1. <span style="color:red;">[DEPRICATE]</span> <span style="text-decoration-line: line-through;">Divided two of those using</span> -----
_yeah I dont know why I using -----_
```javascript
var javascriptPart = content.split("-----")[0]
var htmlPart = content.split("-----")[1]
```
---
### 2. repopulate component
_Just simple regex matching_
```javascript
var components = htmlPart.match(/=?{\S+?}/gm);
const title_head = title[0].split(":")[1].trim()
```
---
### 2.1 Implentment the module package with is a huge messy lol
[[modules support]]
---

# 3. Subtask (or TODO):
[[Subtask]]

# 4.Example
[[Simple interactive click]]