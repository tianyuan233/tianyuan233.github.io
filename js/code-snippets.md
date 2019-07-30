#### 字符串切片可使用负值
```js
'qwertyui'.slice(-1)
> "i"
'qwertyui'.slice(0,-1)
> "qwertyu"
```
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
#### 数组去重
```
[...new Set(arr)]
```
#### ASCII码转换
```
String.fromCharCode(65)   // A
String.fromCharCode(97)   // a
```