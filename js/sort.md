#### 冒泡排序
```js
function bubbleSort(array) {
  for (var j = 0; j < array.length-1; j++) {
    var done = true
    for (var i = 0; i < array.length - 1 -j; i++) {
      if (array[i] > array[i + 1]) {
        [array[i], array[i + 1]] = [array[i + 1], array[i]]
        console.log(array)
        done = false
      }
    }

    if(done) {
      break
    }

  }
}
```
#### 归并排序
```js
function merge(left, right) {
  var res = []
  while(left.length > 0 && right.length > 0) {
    if (left[0] < right[0]) {
      res.push(left.shift())
    } else {
      res.push(right.shift())
    }
  }
  return res.concat(left,right)
}

function mergeSort(array) {  
  if (array.length <= 1) {
    return array
  }

  var mid = Math.floor(array.length / 2)
  var left = array.slice(0,mid)
  var right = array.slice(mid)
  // console.log(left)
  // console.log(right)

  return merge(mergeSort(left), mergeSort(right))
}

console.log(mergeSort([1,2,7,3,8,9]))
```
#### 快速排序
```js
function quickSort(array) {
  if (array.length < 2) {
    return array
  }
  var basic = array[0]
  var left = []
  var right = []
  for (let i = 1; i < array.length; i++) {
    if (array[i] < basic) {
      left.push(array[i])
    } else {
      right.push(array[i])
    }
  }
  return quickSort(left).concat(basic, quickSort(right))
}
console.log(quickSort([5, 1, 2, 3, 4, 6, 7, 8, 9]))
```
#### 选择排序
```js
function selectSort(arr) {
  for (var i = 0; i < arr.length; i++) {
    for (var j = i; j < arr.length; j++) {
      if (arr[i] > arr[j]) {
        [arr[i], arr[j]] = [arr[j], arr[i]]
      }
    }
  }
  return arr
}
```
#### 插入排序
```js
function insertSort(arr) {
  for (var i = 1; i < arr.length; i++) {
    var key = arr[i]
    //
    console.log('key',key)
    console.log('sortPart',arr.slice(0,i))
    //
    for (var j = 0; j < i; j++) {
      if (key < arr[j]) {
          arr.splice(j,0,key)
          console.log('insert',arr)
          arr.splice(i+1,1)
          console.log('delete',arr)
          break
      }
    }
  }
  return arr
}
```