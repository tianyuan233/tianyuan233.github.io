### 防抖和节流

效果查看 http://demo.nimius.net/debounce_throttle/

#### 防抖(debounce)

作用是在短时间内多次触发同一个函数，只执行最后一次，或者只在开始时执行。

```js
function debounce(fn, interval = 300) {
  let timeout = null
  return function () {
    clearTimeout(timeout)
    timeout = setTimeout(() => {
      fn.apply(this, arguments)
    }, interval)
  }
}
```

#### 节流(throttle)

节流给事件一个 Interval 来对它的触发进行一个时间限制，在一段时间内只允许函数执行一次。

```js
function throttle(fn, interval = 300) {
  let canRun = true
  return function() {
    if (canRun === false) return
    canRun = false
    setTimeout(() => {
      fn.apply(this, arguments)
      canRun = true
    }, interval)
  }
}
```

### apply call

```js
function add(a, b) {
  return a + b
}
```

#### call

call() 方法使用一个指定的 this 值和单独给出的一个或多个参数来调用一个函数。

```js
add.call(null, 1, 2)
3
```

#### apply

apply() 方法调用一个具有给定 this 值的函数，以及作为一个数组（或类似数组对象）提供的参数。

```js
add.apply(null, [1, 2])
3
```

### 类型判断

typeof 用来判断原始类型

```js
typeof 123
;('number')

typeof '123'
;('string')

typeof true
;('boolean')

typeof { a: 'qwe' }
;('object')

function a() {}
undefined
typeof a
;('function')

typeof undefined
;('undefined')
```

Object.prototype.toString.call 用来判断内置对象类型

```js
str = new String('i am a string')
String {"i am a string"}
Object.prototype.toString.call(str)
"[object String]"
```

instanceof 用来判断自定义对象类型

```js
function Person() {}
undefined
p = new Person()
p instanceof Person
true
```

### 错误处理与调试

```js
function testFinally() {
  try {
    return 2
  } catch (error) {
    return 1
  } finally {
    return 0
  }
}

testFinally() //输出 0
```

可以在 catch 语句中使用 instanceof 操作符处理不同类型的错误

#### 抛出错误

throw
