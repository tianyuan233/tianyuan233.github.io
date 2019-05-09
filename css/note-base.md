## CSS
> Cascading Style Sheet 层叠样式表

### 如何引入css
- `<style>p {color:red;}</style>`
- `<link rel="stylesheet" href="style.css" media="print">`
- `<div style="color:red;font-size:45px;"></div>`
- `el.style.color = 'red'`
- 在css文件中引入其他css文件`@import url(./path/style.css)`

### 选择器
```css
selector {
    prop:value;
    prop1:value1;
  }
```
* 声明中的属性必须是css所支持的属性，否则将会被浏览器忽略
* 声明的值也必须是**对应属性所支持的**，否则整条声明同样是无效的
* 选择器分组 用`,`隔开
 - `p,div,h1 { color: red;}`
* 规则分组
  * 一个选择器里可以写多条规则
  * 一条规则以一个分号结束，否则不生效
* 标签/元素选择器 element selector
  - `element {rules}`
  - `div {}`
  - `* {color: red;}`
* 类选择器
* id选择器
* 用id还是用class选择器
    * id是一次性的，只出现一次
    * class是多处可用，可以复用的
    * 另外id选择器是不支持空格分隔的id列表的，不像class，p36页
    * id选择器优先级更高
    * 大小写敏感的，.p,.P是不一样的。但有些老浏览器不敏感
    * `#p,#P`
    * `.error {color:red;}`

#### 属性选择器
* 7种属性选择器
* 存在某属性
    * [attr] {}
* 存在多个属性，chaining
    * p[attr1][attr2]
    * [attr1][attr2]
* 属性名与值同时匹配
    * p[attr="abc"]
    * p[class="abc def"] vs p.abc 不一样 p41页
    * .class2 .class2 {
    * }
* 空格分隔的属性值列表
    * [attr~="abc"]
    * .abc == [class~="abc"]
    * 这个有什么作用呢？它可以用在任何属性上面而不是只在class属性上面
* 属性值不区分大小写
    - `<a href=".PDF"></a>`
    * [attr~="abc" i], case insenstive
    * .a.b {}
    * `[class~="a"][class~="b"] {
    }`
* 值以指定内容开头
    * [attr^="abc"] caret
    * 应用：为所有email链接加上特定的样式
    * a[href^="mailto:"]
    * a[href^="tel:"]
    * a[href$=".doc"i]
* 值以指定内容结束
    * [attr$='abc']
    * 应用：为所有不同类型的下载链接加上不同的样式，如pdf文件加上其对应的图标
* 值的任何位置包含指定内容
    * [href*='.google.'] {color: red;}
    * <a href="http://www.baidu.com/l.google.akdf/adsfal"></a>
    * 应用：选择某个域名的链接；不过强度不够，因为无法保证链接的其它部分不出现host中的内容。
* 属性值前缀选择器
    * [lang|='zh']
    * 选择attr值 为abc 或者 以“abc-”开头 的元素
    * [lang|="zh"]
    * 应用：选择语言：<html lang="en"><html lang="en-US">

#### 选择器与文档结构的对应
* 后代选择器
    * `ul em {color: grey;}`
* 子元素选择器
    * `div > h1` 做为div的子元素的h1标签
    * `div > h1 > strong[title]`
* 邻接选择器
    * 相邻兄弟选择器， A+B 紧跟在A标签后面的一个同层级B元素
      * `h1 + p.foo`    h1后面的一个p标签
    * 兄弟选择符，位置无须紧邻，只须同层级，A~B 选择A元素**后面**的所有同层级B元素。
      * `h1 ~ p.foo`

#### 伪类选择器
- a标签的伪类选择器
```css
a:link {color: blue;}
a:visited {color: purple;}
a:hover {color: red;}
a:active {color: yellow;}
```
Link, Visited, Hover, Active  
L, V, H, A  
LoVe, HAte  

- 位置伪类
  * `:first-child 匹配做为第一个子结点的元素`
  * `:last-child 匹配某元素的最后一个子元素`
  * `:nth-child(1)`
  * `:nth-last-child(1)`
  * `:nth-child(-2n+8)`
  * `:nth-child(n-9)`
  * odd/even
  * 注意：
    * `p:first-child` 选择的不是p的第一个子结点，而是做为第一个子结点的p元素
    * `p :first-child`
- 选择器取反
  * `:not(:not([value])) {}`
  * `:not(p.a#b) {}`

#### 伪元素
* `:first-letter`
* `:first-line`
    * 只能用在块级（block）元素上面，p59
* `::before`
* `::after` 
* `:root`
  * 选择文档的根元素。   
* `:empty`  
  * `p:empty` 选择没有子元素的每个 <p> 元素（包括文本节点及空格）。  
* `:target` 
  * 选择一个ID与当前URL片段匹配的元素  
* `:enabled`    
  * `input:enabled`   选择每个启用的 `<input>` 元素。 
* `:disabled`   
  * `input:disabled`  选择每个禁用的 `<input>` 元素  
* `:checked`
  * `input:checked`
  * `input:valid/invalid`
  * `input:required/optional`
* `:not(selector)`  
  * `:not(p)` 选择非 <p> 元素的每个元素。    
* `::selection`
  * 应用于文档中被用户高亮的部分（比如使用鼠标或其他选择设备选中的部分）。

#### 优先级
* 优先级的定义，四个数
  * 0,3,3,10
  * 四位的无穷进制数
* id选择器    
  * `#foo #bar #baz {}` 
  * `0,1,0,0`
* 类选择器，属性选择器，伪类选择器
  * 0，0，1，0
* 元素选择器（标签选择器），伪元素选择器
  *
  * 0，0，0，1
* 连接符如 > + ~ 等不参与优先级的计算
  * 连接符 combinators，无优先级 
  * 于是 p a 与 p > a 的优先级是一样的
* 通配符 *
  * 0，0，0，0
  * 所以以下选择器的优先级是一样的
    * div p      div的所有后代的p元素
    * div * p      div的孙子及其后代的p元素
* 内联样式/行内样式/行间样式/inline style
  * 1，0，0，0
  * `<p style="color: green;">`
* ！important
  * `p {color: red !important;}`
  * 有与important冲突的属性，important都会占上风
* 继承
  * 没有优先级，比【*】的有限级还要小
* 层叠样式
  * 用户important样式
  * 作者important样式 authored style
  * 作者普通样式
  * 用户普通样式 Custom.css
  * 默认样式，浏览器内置样式，User Agent Style
  * 优先级一样的话，按出现的顺序排列，后出现的优先级更高
    * 所以是 link visited focus hover active
    * `:link:hover /0 0 2 0/`
    * 不过在这几个伪类上分别写完全不同的属性时，顺序就不重要了
    * 重要的是写相同的属性，这时就要考虑优先级的问题了
    * LV HA  VL HA 没有太大区别，因为很明显，V和L不会同时匹配
    * 不来自CSS的样式
        * 如font标签 <font size color face></font>
            * 可以想象它的优先级为0000并且出现在作者样式的开头
            * 会被作者样式和读者样式覆盖，但不会被默认样式覆盖

  
