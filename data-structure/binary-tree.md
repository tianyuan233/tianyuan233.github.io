### 转换
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
### 遍历
#### 前序遍历 PreOrder
```js
var preorderTraversal = function (root) {
  var res = []
  function order(root) {
    if (root) {
      res.push(root.val)
      order(root.left)
      order(root.right)
    }
  }
  order(root)
  return res
};
```
#### 中序遍历 InOrder
```js
var inorderTraversal = function (root) {
  var res = []
  function order(root) {
    if (root) {
      order(root.left)
      res.push(root.val)
      order(root.right)
    }
  }
  order(root)
  return res
};
```
#### 后序遍历 PostOrder
```js
var postorderTraversal = function (root) {
  var res = []
  function order(root) {
    if (root) {
      order(root.left)
      order(root.right)
      res.push(root.val)
    }
  }
  order(root)
  return res
};
```
### 二叉树搜索
```js
var searchBST = function (root, val) {
  if (!root) {
    return null
  }
  if (root.val == val) {
    return root
  }
  if (val < root.val) {
    return searchBST(root.left,val)
  } else {
    return searchBST(root.right,val)
  }

}
```
### 二叉树合并
```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} t1
 * @param {TreeNode} t2
 * @return {TreeNode}
 */
var mergeTrees = function (t1, t2) {

  if (!t1 && !t2) {
    return null;
  }

  if (!t1||!t2){
    return t1 || t2
  }


  let root = new TreeNode(t1.val + t2.val)

  root.left = mergeTrees(t1.left, t2.left)
  root.right = mergeTrees(t1.right,t2.right)

  return root
};
```
### 二叉树精简
```js
var pruneTree = function (root) {
  if(!root) {
    return null
  }
  
  root.left = pruneTree(root.left)
  root.right = pruneTree(root.right)
  
  return (root.val === 1 || root.left || root.right) ? root : null
};
```

### 二叉搜索树
二叉查找树（英语：Binary Search Tree），也称为二叉搜索树、有序二叉树（ordered binary tree）或排序二叉树（sorted binary tree），是指一棵空树或者具有下列性质的二叉树：

 - 若任意节点的左子树不空，则左子树上所有节点的值均小于它的根节点的值；
 - 若任意节点的右子树不空，则右子树上所有节点的值均大于它的根节点的值；
 - 任意节点的左、右子树也分别为二叉查找树；
 - 没有键值相等的节点。

 *BST中序遍历的结果是一个升序排序的数组*