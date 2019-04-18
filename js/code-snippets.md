#### 数组求和
```javascrpit
let sumA = A.reduce((sum, ele) => { 
  return sum + ele 
  })
```
#### 数组降维
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
#### ASCII码转换
ASCII码转换
```
String.fromCharCode(65)   // A
String.fromCharCode(97)   // A
```