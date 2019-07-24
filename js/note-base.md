### apply bind call 
```js
function add(a,b) {
  return a + b
}

add(1,2)
3
```
#### apply
```js
add.apply(null,[1,2])
3
```
#### bind
```js
var f = add.bind(null,5)
undefined
f(2)
7
```
#### call
```js
add.call(null,1,2)
3
add.call(null,1,2,3)
3
add.call(null,1,2,4)
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

