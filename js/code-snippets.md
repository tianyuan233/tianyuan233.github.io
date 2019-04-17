### 数组求和
```javascrpit
let sumA = A.reduce((sum, ele) => { 
  return sum + ele 
  })
```
### 数组降维
```javascrpit
let data = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]

let data1 = data.reduce(function(d, line) {
  d = d.concat(line)
  return d
}, [])
```