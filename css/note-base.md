### CSS
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
- MDN文档
    - https://developer.mozilla.org/zh-CN/docs/Web/CSS/Pseudo-classes
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
-------------------------------------------------------------
### 值和单位
* 数字
    - line-height: 2;   /* 200% */
    - animation-iteration-count: 2;
    - zoom: 2.5;         /* 放大2.5倍 */
    - column-count: 2;
* 百分比
    - width/height: 60%;
    - top/left/right/bottom: 50%;
    - line-height: 150%;
    - vertical-align: 40%;
    - color: rgb(40%, 50%, 70%)
* 百分比与纯数字不可互换
* 颜色(R G B)
    * color: red;
    * red/blue/green/tan/brown/teal/grey/maroon/silver/yellow/aqua/lime/
    * hex color
        * #HHHHHH #(0-255)(0-255)(0-255) -> 16700000
    * hexa #ff00ff80
    * #abc -> #aabbcc
    * rgb(r,g,b) sin(3.14) log(2,32) = 5
    * rgb(0-255, 10, 0-255)
    * rgb(r%,g%,0-100%)
    * rgba(r,g,b,0 -> 1)
    * 色彩空间
    * CMYK(Cany Manganta Yellow blacK)
    * 色域
    * hsl（色相，饱和度，明度）
    * hsla（色相，饱和度，明度，0-1）
    * hexa rgba
    * web safe 颜色，216种
    - 是在早期大家的电脑都只支持256种颜色时，选出的大部分浏览器与操作系统都支持的216种颜色
        * 6的3次方，即r，g，b分别有6阶可选
    - https://websafecolors.info/learn
    - gif 图片也只有 256
* 长度
    * 绝对长度单位 
        * in(ch) 英寸
        * cm 厘米 centimeters
        * mm 毫米 millimeters
        * -moz-mm
        * pt point 72分之一inch
        * pc pica 6分之一inch
        * 存在的问题
            * 大部分时候不准，取绝于你的分辨率以及系统设置
                - 于是用的也很少
            * 但在打印的时候可以比较准
        * Surface Studio
    * 相对长度单位
        * px，CSS像素
            * 很多人以为这是个绝对长度单位，其实并不是。但在设计中，大多数时候被认为是绝对长度（p89页）
            * 指定图片的大小一般肯定是用这个，要不然图片会被变形拉伸，因为图片的尺寸大多数时候是以px来丈量的
            * 另一个坑，在ie7之前的浏览器，放大时以px指定的文字不会放大，不过已经不在考虑范围了
        * em
            * 【当前元素】font-size的大小
        * rem
                - root element's em
                - 灵活的布局
                - html 元素（根元素）的字号
                - html {font-size: 2em;}
                - p {width: 20rem;       }
        * ex
            * x字符的高度
            * 有些浏览器会把它计算成 0.5em
        * vw/vh
            - viewport width
            - 1vw 视口宽度的100之一
            - viewport height
            - 1vh 视口高度的100之一
            * 包含滚动条
        * vmax/vmin
            - vmax = max(vw, vh)视口宽或者高较大的那一个的100之一
            - vmin = min(vw, vh)视口宽或者高较小的那一个的100之一
        * width: calc(2 * 30em - 40%)
        * line-height: calc(2 * 3)

-------------------------------------------------------------
### 字体
* 字体族
    * serif 衬线字体
    * sans-serif 非衬线字体
        * 什么是衬线？
    * monospace 字体，等宽字体
* 使用通用字体族
    * body {font-family: sans-serif;}
    * 以上代码中，浏览器将自动选择一款没有衬线的字体
* 使用指定的字体
    * `h1 { font-family: "MicroSoft YaHei";}`
    * 如果用户的电脑上安装了这款字体，那么该页面上的h1将会用这个字体
    * 但是，有时候用户的浏览器并不一定安装了这个字体这时可以指定退化（fallback）方案
        * h1 {font-family: "Helvetica", "微软雅黑", sans-serif;}
        * 一般来说，最好提供一个字体族名称做为最后的退化方案
    * 字体名称里面有特殊字符时
        * 使用引号（quotation marks）引起来
            * 单双均可，只要配对就好
                * 但注意在html标签的style标签里面的时候要跟外层的引号匹配，还是配对问题
        * 如果不加的话，浏览器会忽略那个字体声明
            * p {font-family: "Microsoft YaHei", "lksdjf, i*7#" , serif;}
            * 上面这条规则相当于p {font-family: "Microsoft YaHei", serif;}
        * 另外，通用字体族必须不能加引号，它们算是关键字而不是字体值（字符串）
            * 加了引号就成指定的字体名称而不是字体族了
        * font-family: 'microsoft yahei';
* 字重
    * font-weight
        * normal
        * bold
        * bolder  <h1> bar <span>foo</span></h1>
        * lighter
        * 100 - 900
        * inherit
    * 一般来说，一些字体都会预定义一些不同字重的字体
        * 如
            font-family: 'Zurich';
            font-weight: bold;
            * Zurich Extra Black
            * Zurich Black
            * Zurich Bold
            * Zurich
            * Zurich Light
        * 于是可以这么用
            * p {font-family: 'Zurich Black'}
            * div {font-family: 'Zurich Light'}
            * strong {font-family: 'Zurich Bold'}
        * 但是
            1. 上面的写法很繁琐
            2. 很多字体**不一定**预定义了这么多种不同的内置字重，或者用户不一定安装了所有这些字体
                * 这意味着可能会使用退化字体
            3. 很多可能就只有一种
                * 这种情况下浏览器可能会实时计算出比如粗体的样子
        * 怎么办呢？
            * 只指定主字体，然后指定font-weight，由浏览器来选择具体字重的字体文件，或者计算出来
        * Bolder
            * 让字体变的更粗
        * Lighter
            * 让字体变的更细
* 字号 font-size，
    * （所谓的）绝对大小关键字
        * xx-small
        * x-small
        * small
        * font-size: medium;
        * large
        * x-large
        * xx-large
    * 根据规范，一个绝对大小与相邻的绝对大小的缩放因子是1.5以及0.66
        * 比如如果medium是10px
        * 那large就是15px
        * small就是6.66px
        * 但
            * 不同浏览器设置的缩放因子可能并不一样
                * 而且，这个值是开发者没办法更改的
            * medium的大小也是不确定的
            * 所以这几个关键字基本上没什么用武之地
    * 百分比单位
        - 相对于父元素的大小，也即继承过来的值
        - 跟em的效果几乎是一样的
            + 120%跟1.2em几乎一样
        - 使用这种单位可能会产生意想不到的效果
          
    * font-size的继承
        - 总是继承的是**计算后**的值，而不是**书写时**的值
        * div>p>span
        * div {font-size: 10px;}
        * p {font-size: 120%;}
        * span {font-size: 120%;} -> 14.4px
    * 长度单位
        - 绝对单位如cm，pt等可能不是你想要的
            + 不同的系统可能显示效果不一致
        - 所以大多数页面中选择px等单位
            + 能够“最大程度的”保证设计的高度还原
            + 但存在的一些问题是，老版本的浏览器在放大页面或字体的时候，无法放大以px指定大小的字体
            + 现代浏览器无此问题
    + font-style与font-variants
        * font-family: "Consolas";
        * font-style
            - normal
                + 文字**是正*的，即垂直的
            - italic
            - oblique
            - 上面两个都是斜体，但是有啥区别呢？
                + italic是另一个专门设计好的斜体字体
                    * 比如正常字体是 Roboto
                    * 则italic字体可能会是 Roboto Italic，Roboto Cursive
                + 而oblique则是在正体的文字基础上变幻出来的一个斜体字
                    * 而oblique则一般会map到Roboto Slanted，Roboto Incline， Roboto Oblique
* font-variant
    - normal，默认
    - small-caps
        + 把小写字母显示成小号的大写字母
        + 有些字体专门为小写字母设计了这种样式，而不是单纯的把大写字母显示的小一点。
            * 当字体没有提供这种样式的时候，浏览器当然就是把大写字母缩小了
- 子属性
    - font-size/family/style/weight/variant
    - font: ;
    - font-style:;
    - font-weight:;
    - border SHORT HAND
    - border-style/width/color;
    - border-left/right/top/botoom
    - border-left/right/top/bottom-style/widht/color;
    - margin   margin-left/right/top/bottom;
    - transition transition-duration/timing-funciton/property....
    - border-radius
* font 属性 short hand
    - font: [font-style || font-variant || font-weight] font-size[ / line-height] font-family
    - font: small-caps bold 20px / 1.2em 宋体, serif;
    - css权威指南 p121页
-------------------------------------------------------------
### 文本属性
- 文字缩进 text-indent
  + text-indent: 2em
  + text-indent: 5%；百分比相对于父元素宽度
  * 一般很少用百分比
  + 应用
    * 用text-indent: -99999px来把标签里的文字隐藏，然后用背景图片“替换”标签内容
    * -2em这种可以实现首行悬挂
      * 相应的margin-left 也要增加2em
    * 2em则可以实现首行缩进
  + 本属性只适用于块级元素，不适用于内联元素
- 文字水平对齐 text-align
  + left
  + right
  + center
  + justify
    * 两端对齐
    * 不同行文字之间的空白可能就不一样了
    * 在有长单词的行中显得比较明显
        - css 并不支持在打断长单词时自动加上连字符-
- 文字在垂直方向的对齐 vertical-align
+ line-height
  * 应用：单行文字垂直居中
      - 坑点，无法让lh总是等于元素的高度
      - 其它
          + 多行文字垂直居中
              * http://www.zhangxinxu.com/wordpress/2009/08/%E5%A4%A7%E5%B0%8F%E4%B8%8D%E5%9B%BA%E5%AE%9A%E7%9A%84%E5%9B%BE%E7%89%87%E3%80%81%E5%A4%9A%E8%A1%8C%E6%96%87%E5%AD%97%E7%9A%84%E6%B0%B4%E5%B9%B3%E5%9E%82%E7%9B%B4%E5%B1%85%E4%B8%AD/
          + flex等实现方式
+ vertical-align
  * 这个属性适用于【内联元素】
      - img
      - input
      - 替换元素等
      - 而不是给块级元素用的
  * 取值
      - 关键字
          + baseline
              * 默认值
              * 让元素的基线与其父元素行框的基线对齐
              * 如果一个元素没有基线，如img，input，则让其底部与外面的文字对齐。即使行框没有文字也是一样。是p138-139页
                  - 应用：图片跟文字底部对不齐
          + sub
              * 元素的baseline（或底部）会比父该行文字的basline低
              * 但低多少，标准并没有说。。。
          + super
              * 同上，元素的baseline比该行内容的baseline要高
              * 标准同样没有规定高多少。。
          + bottom
              * 目标元素的底部跟这一行的底部对齐
          + top
              * 目标元素的顶部跟这一行的顶部对齐
          + text-top
          + text-bottom
              * 元素的顶/底部与文字的顶/底部对齐
          + middle
              * 并不是垂直居中
              * 而是把【元素的中间】与baseline上面0.5ex（即四分之一em）对齐。。。
          + 百分比
              * 相对于自己的 line-height
              * 把其 baseline 向上或向下移动计算出来的值
          + 固定长度值
              * 按指定的数值上移或下移元素
              * 上下移动元素并不会让其与其它行的内容重叠，而是会增加行框的高度
      - 在作用于表格元素时
          + 只有 baseline，top，middle，bottom 有效，其它无效
              * 将在表格布局一章说到
+ word-spacing
  * 控制单词间的间隔
      - 注意中文文字之间不是word space，而是letter space
      * 其值是添加到本身空格间的值，而不是设置了多少，单词间就间隔多少
  * 取值
      - normal
          + 相当于写成0
      - 长度单位
          + 写成多少，单词间的间隔就是空格的宽度加这个值
          + 可以为负值
+ letter-spacing
  * 改变字母间的间隔
      - 对于汉语，则是改变文字之间的间隔
  * 取值
      - normal
          + 相当于设置为0
      - 长度值
          + 增加或减少字母间的距离
+ word-spacing，letter-spacing 与 text-align：justify
  * letter-spacing:normal与text-align:justify一起用时，字母间的距离可能会被改变
  * 但如果给了letter-spacing一个指定的值的话，则justify就不会影响它了
  * http://jsbin.com/pasekej/1/edit?html,css,output
+ text-transform
  * uppercase
      - 所有字母变成大写
  * lowercase
      - 所有字母变成小写
  * capitalize
      - 每个单词的首字母大写
          + heading-one可能被转换成下面两种
              * Heading-One
              * Heading-one
  * 本属性的效果先于font-variant执行
  * none
      - 默认，as authored
  * inherit
  * 应用
      * 有些网站的优惠券是全大写的，或者Windows的激活码什么的

-------------------------------------------------------------

