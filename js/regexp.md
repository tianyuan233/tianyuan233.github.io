### 创建正则表达式
```js
let reg1 = /qwe/
let reg2 = new RegExp('qwe')
```
### 正则方法
#### test
返回一个布尔值表示字符串中是否含有能与表达式匹配的字符串
```js
> /qwe/.test('qqqwee')
< true
```
#### exec
```js
re = /qwe/g
re.exec('qqweeqwe')

["qwe", index: 1, input: "qqweeqwe", groups: undefined]

re.lastIndex
4

re.exec('qqweeqwe')
["qwe", index: 5, input: "qqweeqwe", groups: undefined]

re.lastIndex
8

re.exec('qqweeqwe')
null
```
### 字符串方法
#### replace
追加`g`选项表示替换所有匹配项
追加`i`选项表示替换所有匹配项

```js
'q1w3e4q5'.replace(/\d/,'#')
"q#w3e4q5"

'q1w3e4q5'.replace(/\d/g,'#')
"q#w#e#q#"
```
#### match
```js
'q1w3e4q5'.match(/\w\d/g)
(4) ["q1", "w3", "e4", "q5"]

'q1w3e4q5'.match(/\w\d/)
["q1", index: 0, input: "q1w3e4q5", groups: undefined]
```
#### search
返回搜索结果位置的index
```js
'q1w3e4q5'.search(/\s/)
-1

'q1w3e4q5'.search(/\d/)
1
```
#### split

### 单词和字符串边界
`^`起始位置
`$`结束位置
`\b`单词边界