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