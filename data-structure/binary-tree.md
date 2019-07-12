#### 二叉树转数组
```js
function treeToArr(root) {
  if (root){
    var res = [] 
    var nodes = [root]

    while(nodes.length) {
      curr = nodes.shift()
      if (curr) {
        res.push(curr.val)
        nodes.push(curr.left)
        nodes.push(curr.right)
      } else {
        res.push(null)
      }
    }
    return res
  }
  return []
}
// ---------------------------
function treeToArr2(root) {
  if (root) {
    var res = [root.val]
    var nodes = [root]
    while (nodes.length) {
      curr = nodes.shift()
      if (curr.left) {
        res.push(curr.left.val)
        nodes.push(curr.left)
      } else{
        res.push(null)
      }
      if (curr.right) {
        res.push(curr.right.val)
        nodes.push(curr.right)
      } else{
        res.push(null)
      }
    }
    return res
  }
  return []
}
```
#### 数组转二叉树
```js
function arrToTree(arr) {
  if (arr.length == 0) {
    return null
  }
  var root = {
    val: arr[0],
    left: null,
    right: null,
  }
  //nodes存放非空节点   (队列)
  var nodes = [root]
  for (let i = 1; i < arr.length; i++) {
    var curr = nodes.shift()
    //当前节点的左子树
    if (arr[i] != null) {
      var node = {
        val: arr[i],
        left: null,
        right: null,
      }
      nodes.push(node)
      curr.left = node
    } else {
      curr.left = null
    }
    i++
    if (i>=arr.length) {
      break
    }
    //当前节点的右子树
    if (arr[i] != null) {
      var node = {
        val: arr[i],
        left: null,
        right: null,
      }
      nodes.push(node)
      curr.right = node
    } else {
      curr.right = null
    }
  }

  return root

}
var arr = [1,2,null,3,4,null,5,null,null,6,7,null,8,9]
```