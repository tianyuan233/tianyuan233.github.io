### 链表
#### 数组转链表
```js
function arrToList(arr) {
  if (!arr.length) {
    return null
  }
  var head = {
    value: arr[0],
    next: null
  }

  var pnode = head

  for (var i = 1; i < arr.length; i++) {
    var node = {
      value: arr[i],
      next:null 
    }
    pnode.next = node
    pnode = pnode.next
  }

  return head
}
console.log(arrToList([1, 2, 3, 4]))
```
#### 链表转数组
```js
function listToArray(list) {
  var arr = []
  while(list) {
    arr.push(list.value)
    list = list.next
  }
  return arr
}
```
#### 链表删除元素
```js
function delNodeFromList(head, value) {
  var dummy = {
    value: null,
    next: head
  }
  while (dummy.next) {
    if (dummy.next.value === value) {
      dummy.next = dummy.next.next
    } else {
      dummy = dummy.next
    }
  }

  return head
}
console.log(delNodeFromList({ value: 1, next: { value: 2, next: { value: 5, next: null } } },2))
```