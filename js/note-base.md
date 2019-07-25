### apply call 
```js
function add(a,b) {
  return a + b
}
```
#### call
call() 方法使用一个指定的 this 值和单独给出的一个或多个参数来调用一个函数。
```js
add.call(null,1,2)
3
```
#### apply
apply() 方法调用一个具有给定this值的函数，以及作为一个数组（或类似数组对象）提供的参数。
```js
add.apply(null,[1,2])
3
```
### 类型判断
typeof 用来判断原始类型  
```js
typeof 123
"number"

typeof '123'
"string"

typeof true
"boolean"

typeof {a:'qwe'}
"object"

function a(){}
undefined
typeof a
"function"

typeof undefined
"undefined"
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
function Person(){}
undefined

p = new Person()

p instanceof Person
true
```
### 错误处理与调试
```js
function testFinally(){
	try {
		return 2;
	} catch (error){
		return 1;
	} finally {
		return 0;
	}
}

testFinally()   //输出 0
```
可以在catch语句中使用instanceof操作符处理不同类型的错误
#### 抛出错误
throw

