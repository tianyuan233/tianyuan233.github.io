### 链接
 - [MDN HTML元素参考](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element)
 - [元素分类](https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/Content_categories)
 - [ARIA](https://developer.mozilla.org/zh-CN/docs/Web/Accessibility/ARIA)

### html
代表 HTML 或 XHTML 文档的根。其他所有元素必须是这个元素的子节点。
### head
头部标签，放一些与页面相关的“元信息”
 - https://github.com/joshbuchea/HEAD
#### title
* 页面标题
* 仅支持纯文本，不支持嵌套其它标签
* 如果不出现在head内，将自动移到head内
* 出现多个的话，仅第一个生效

#### base 基准
- `<base href="页面中所有相对路径的基准地址" target="页面中所有链接的打开位置">`
    + href属性表示页面中所有**相对路径**的基础路径
        * 一定要以/即目录结尾
            - `<base href="https://www.baidu.com/abc/">`
    + target属性表示页面中**所有链接**的打开位置
        * 当然，可以在页内的a标签中用它自己的target属性覆盖用base标签设置的全局打开位置
- 有些框架等可能会利用这个特性

#### 等等等等等等....
--------------
### body
* html文档中显示的内容

### h1-h6
* 一级到六级标题

### p
* paragraph
* 语意是一个段落，当想要表达一段话时都可以使用这个标签
* 默认情况下也会有上下边距

### a
* anchor, 锚
  * 语义是一个链接，链接地址写在  href（Hyperlink REFerence）属性里
  * 可以链接到的类型非常多，而且一般来说是可扩展的
* 绝对路径，fullpath
  * `<a href="https://jd.com/">京东</a>`
* 页内特定位置跳转地址
  * `<a href="#pos1"></a>`
* 其它页特定位置跳转地址
  * `<a href="http://jd.com/#footer"></a>`
    * 这个在书目的章节跳转在使用的比较多
* 相对路径
  * `<a href="./a.html">baidu</a>`
* 电子邮件
  * `<a href="mailto:aaa@bbb.com"></a>`
  * `<a href="mailto:aaa@bbb.com?title=1&subject=2&content=3"></a>`
  * 需要在电脑安装邮件客户端

* 空的href属性 href="" 
    * 链接到当前页面
    * 所以仅以#开头的值是中转到当前页面的特定位置
    * `<img src="">`
* 类似的，如果一个img标签的src属性为空，也将对应当前页面地址
    * https://www.nczonline.net/blog/2009/11/30/empty-image-src-can-destroy-your-site/
* target属性
  * 可以指定在哪个窗口打开链接
  * 几个特殊值,关键字
    * _blank，链接在空白的窗口显示，也就相当于新打开一个窗口
    * _self，其实这个是默认值，就是在当前窗口打开
    * _parent，链接在父窗体显示
    * _top，链接在顶层窗口显示
    * 自定义值
      * shopingcart，要求不能以_开头，出处：https://www.w3.org/TR/html-markup/datatypes.html#common.data.browsing-context-name-def

### img
* src(source)属性表示图片的地址
    * 可以是绝对地址，相对地址
    * `<img src="http://www.baidu.com/logo.png" alt="" title="tooltip">`
    * `<img src="../abc.jpg" alt="">`
    * `<img src="/abc.jpg" alt="">`
    * src指定的图片可以是浏览器支持的任意图片格式
        * jpg/jpeg/png/bmp/gif/webp/svg/ico
* alt 属性表示图片在加载失败时的替换文本
    * 作用是当HTML元素本身的对象无法被渲染时，就显示alt（替代）文字作为一种补救措施
* 可以使用width和height属性定义图片的宽和高
    - 只写一个的话另一个会根据图片原始比例计算出来
    - 图片一般来说有自己的宽高（natural width/height）
    - 但是图片加载往往需要时间，而图片在加载完成之前浏览器是不知道其宽高的，所以就会产生页面抖动的问题
    - 所以一般会在标签上把宽高写出来，为未加载的图片提前把位置空出来

### download
* 表示点击这个链接将下载链接对应的文件，而不是跳转到目标页面，下载的文件名以download属性的值来命名
    * `<a href="xxx/jianai.pdf" download="简爱.pdf">点我下截《简爱》完整版</a>`
    * 只能触发下载自己网站上的资源
    * 问题，如果同时有target=“_blank”，又有download属性，它如何行为呢？
        * 请自行测试
    * 为什么要有这个属性呢？传统浏览器中，要触发下载，需要服务端的支持，给出特定的http头才会触发浏览器下载而不是打开对应的内容
        * 这个属性的出现可以让点击下载完全由前端来完成

### span
* 是一个没有明确语义(通用语义)的标签
* 一般来说想要给特定的内容加样式时可以用一个span标签将内容包起来

### div
* 同样没有语义
* 一个通用型的流内容容器，它在语义上不代表任何特定类型的内容，它可以被用来对其它元素进行分组，一般用于样式化相关的需求（使用 class 或 id 特性)

### abbr
* 用于展示缩写
* 通过title属性显示完整的描述
 
### br
* 换行 自闭合标签

### hr
* 分割线 自闭合标签

### u
* underline 下划线

### i
* italic 斜体的
* 在以前，这个标签就是表示斜体文字的
* 但html5中对其语义进行了明确
    * 用来表示由于某些原因需要与普通文本区分的文本
* 默认情况下为斜体
* 因为跟icon这个单词的首字母一样，很多人/框架/库也用这个标签来表示图标
    - http://fontawesome.io/
        * `<i class="fa fa-star"></i>`

### pre
* pre formatted
* 表示有预定义格式的文本
    * 里面的内容的回车跟空格都会被保留
* 本来有个width属性，表示每行最多的字符
    - 本来支持度也不好，然后在html5中被弃用了，因为可以用css来更精确的控制
* 常与code标签 `配合` 使用，用来在网页里显示高亮过的代码
  * `<pre><code class="">code goes here</code></pre>`

### ol,ul
* Ordered List
* Unordered List
* 其直接子结点必须只能是li标签
    * li内可以是任意其它标签

### dl
* Description List
* 一个列表项是**一个dt**和**一个或多个dd**一起算一组
    + 此标签与ol/ul有些区别，在于 **一个dt可以对应多个dd**

---------

## 表单标签
### form
* 属性
    + action
        * 表单提交的地址
    + target
        * 行为类似a标签的target
    + method
        * 表单提交方式
            - get
                * 将表单字段拼成querystring
                    - http://abc.com/?a=1&b=2&c=3
            - post
    + enctype，编码方式

### input
+ type属性的各项值
    * text
        - 文本
    * password
        - 密码
    * checkbox
        - 复选框
        - 以相同name分组
        - checked属性表示默认选中
    * radio
        - 单选框
        - 剩余同上
    * file
        - accept
            + 可以接受的文件类型
            + `<input type="file" name="" id="" accept="image/*,text/*">`
            + `<input type="file" name="" id="" accept=".jpg,.png,.gif,.jpeg,.webp,.exe" value="c:/user/xieran/desktop/a.pdf">`
        - 安全问题
        - multiple
            + 是否支持多选文件
    * hidden
        - 隐藏的输入域
        - value设置其值
        - name设置名字
    * 为以下三个值时，都表现为按钮的样式，按钮上的文字需要用value属性来设置
        * button
        * submit
            - 单击时会触发表单的提交
        * reset
            - 单击时会重置表单为初始状态
* **以下为html5新增属性值**
    * number
        - 输入数字
        * e,.,-
        * -3.14e-8   
    * email
        - multiple
        - 使用半角逗号分隔每个地址
    * date
        - 格式: 2019-05-06
    * datetime-local
        - 格式: 2019-05-09T02:02
    * time
        - 格式: 02:04
    * url
        * protocal://user:password@domain:port/a/b/c/d.html?a=b&c=d#sldjfoiwjeofij
        * 百度.中国
    * week
    * month
    * tel
    * range
        - min，4
        - max，10
        - step，2
    * color
        - value将返回十六进制颜色#abcdef
    * 不能识别的值，当做text来处理
* 其它属性
    - value
        + 为按钮形态时设置上面的文字
        + 为输入框时设置里面的默认内容
            * datetime-local
            * https://zh.wikipedia.org/wiki/ISO_8601
    - disabled
        + 无值的属性
        + 禁用这个输入域
    - required
        + 设置这个输入域为必填项
        + 不填的话无法用**正常手段**触发表单提交
    - maxlength
        + 为文本输入框时设置输入的最大长度
    - minlength
        + 同上，但为设置最小长度
        + 不过兼容性不太好，不少浏览器没有实现
            * 有点矛盾，不填的时候是空的，当然会非法
    - placeholder
        + 占位符
        + 提示性文字，一旦输入内容就消失
    - autofocus
        + 自动获得焦点，即页面加载完后光标自动在这个元素内
    - tabindex
        + 按tab键在不同输入域之间跳转时的顺序
        + 会往顺序更大的元素跳
        + 为-1的话会跳过那个元素
    - name
        + 很重要，表单提交时，form的名称
        + 同时，在radio和checkbox阵列里，name相同的元素被分在一组里

### button
+ type属性
    * 不写type属性的话，默认为submit
        - 即：无type的button的type属性默认为submit
    * `<button type="reset/button/submit">Submit</button>`
    * button
        - 常规按钮，功能上与input[type="button"]一样
    * submit
        - 提交按钮，功能上与input[type="submit"]一样
    * reset
        - 重置按钮，功能上与input[type="reset"]一样
+ 与`<input type="button" name="b" value="lksjdf">`的区别
    * input的button只能在按钮上显示纯文字
    * 而button标签可以在按钮上显示其它内容比如图片（即嵌套其它标签），文字也可以设置不同颜色等

### label 标签
+ 一般与checkbox及radio一起用，以扩大这两个按钮的可点击区域，提升用户体验。当然，也可以跟其它元素一起用，不过一般没必要（比较典型的是与input:file一起用）
+ for属性
    + 为 想要被扩大点击区域的元素的id，不带井号
    - 支持度非常好，ie5都支持
    - 细节：在ie8及以下不能用于displaynone的表单元素，可能是因为 not focusable
    - 表单元素嵌套在label的时候可以不用for属性
        ```html
        <form action="">
        <!-- 有for的用法 -->
        <label for="oneid">One</label>
        <input onclick type="text" id="oneid">
        <!-- 不用for的用法 -->
        <label>
            <input type="checkbox"> 男
        </label>
        </form>
        ```

### 下拉框
- select name="sel"
    + 下拉选择框
    + 属性
        * multiple
            - 无值属性，表示多选，多选时就不是下拉的样式了
    + 另外此标签在不同的系统里面样式差别很大，而且它的样式一般来说是取自系统自带的，所以很难被css控制
        * 所以一些对ui要求比较高的网站都选择用其它元素模拟下拉框
            - 例：小米路由器
* option
    * value
        - 选择了该项目后它所属的select元素的值
    * selected
        - 默认被选中
    * disabled
        - 表示该项被禁用
    * hidden
        - 表示该项被隐藏
    - 以上三个属性均无值
* optgroup // hgroup  colgroup
    - 给option分组
    - 用label属性表示这个分组的名字
    - 无法被选中，只能选择option
    - 有一个disabled属性，如果设置了这个属性，整组标签都会被禁用
    ```html
    <select>
        <option value="1">1</option>
        <optgroup label="这是一个分组" disabled hidden>
            <option value="01">01</option>
            <option value="02">02</option>
            <option value="03">03</option>
            <option value="04">04</option>
            <option value="05">05</option>
        </optgroup>
    </select>
    ```

### textarea
+ 多行文本输入框
+ 两个特殊属性
    * rows="3"
    * cols="20"

## fieldset
### fieldset 字段组 用来把 一组 输入域 放在一起的。
+ field就是字段的意思，就是说一个表单输入域（输入框）
+ 这个标签用来给输入域分组，所以叫set
    * set本来就是组的意思
+ 如果只是分组，完全可以用div等标签
    * 那这个标签有什么用呢？
    * fieldset有个disabled属性，如果它有了这个属性，其内的所有输入域都将被禁用，类似optgroup
        - 在某些场景下是非常好用的
        
### legend
+ 只能作为 fieldset 的子元素，用来标识这组输入域的名字，基本上没有其它用处
    * 而且在有了css之后，这个标签基本也没有用武之地了
- ```js
<fieldset disabled="disabled">
    <legend>这里面的全都禁用了</legend>
    <input type="text" name="" id="">
    <input type="text" name="" id="">
    <input type="text" name="" id="">
</fieldset>
```
-------

## 表格元素
* table标签
    - 这个标签以前经常用于做布局
        + 什么是布局？即页面大区块的排列和摆放
        + 为什么呢？因为table都是方方正正格子，了解后很容易控制
            * 语义很差
            * 可读性很差
            * 可维护性也很差 maintainable
            * 可访问性
        + 但现在有了 css 之后，基本上只用table来显示数据，即表格本来的作用
        + 熟悉 DIV+CSS 布局 JD Job Description
    * caption
        - 表格标题
    * thead
        - 表头
        - 做为table的直接子元素
        - 只能有一个
        - 只有一个的情况下，即使出现在tbody的后面，其内容也会显示在tbody的前面
        - 非要写多个的话，第一个以外的会当做tbody来处理
    * tbody
        - 表格主体
        - 做为table的直接子元素
        - 可以有多个
    * tfoot
        - 表尾
        - 做为table的直接子元素
        - 只能有一个
        - 只有一个的情况即使出现在tbody的前面面，它的行也出现在tbody的后面
        - 非要写多个的话，第一个以外的会当做tbody来处理
    * tr
        - table row cell
        - 表格行
        - 可以直接做为table的子元素，会被放入创建的tbody里面
        - 或者做为上面三个标签(thead/tbody/tfoot)的子元素
    * th
        - table header cell
        - 用在表头单元格
        - 文字默认为加粗
        - id用于被td元素引用以表示td所属的标题是哪一个
            + 看例子
    * td
        - table data，表格数据单元格
        - headers
            + 表格头，值为某th的id，以表示这个数据的名称
                * 方便读屏软件
            + headers的值可以是多个以空格分隔的th的id的值，用法可能是th或td单元格跨行或跨列了
        - 跨行跨列的单元格
            + colspan 跨列
            + rowspan 跨行
    * col/colgroup 标签
        - colgroup
            + 用来分组col标签
            + span属性，表示选择多列表格
            + 有span时，不可再有子的col元素
            + 大部分属性同col元素
        - col
            + 用来设置表格列的属性和样式
            + span属性，表示选择多少列表格列，默认为1
        - 可以单独使用，也可以被colgroup分组
- 工具
  - https://www.tablesgenerator.com/html_tables

------

### map
* 映射标签
* 通过 name属性 `name="somemap"`与img标签中的 `usemap="#somemap"` 绑定
* 子元素
  - area
  - 属性
    + href
    + target
    + alt
    + 以上三个属性同a标签
    + shape
        * rect(angle)，矩形
            - x1,y1,x2,y2
        * circle，圆形
            - cx,cy,r
            - 圆心x，圆心y
            - 半径r
        * poly(gon)，多边形
            - 至少6个值，表示一个多边形的若干个顶点
    + coords coordinate
        * 对应shape的几种图形的坐标
* 工具
  - https://www.image-map.net/

### iframe
* 表示嵌套的浏览上下文，有效地将另一个HTML页面嵌入到当前页面中。
- 必须有开始标签和结束标签
  + 可以在标签之间写上不支持此标签时的退化内容
* 各种属性
  - src
  - name
    + 提及a标签的target属性
      * _self, _blank
      * _top, _parent
  - sandbox
* webview
* 它的跳转记录也会存在于浏览器的前进后退的记录里面

### frameset
- frame的集合
- 已废弃

### div
 - 没有语义的标签， 通常使用class来表示该标签的“语义”
 - ```html
  <div class="footer"></div>
  <div class="header"></div>
  <div class="sidebar"></div>
  <div class="navigation"></div>
  <div class="wrapper container"></div>
  <div class="content"></div>
  <div class="main"></div>```

### 其他常见标签
* 下标 sub
* 上标 sup
* script
    - `<script>js goes here</script>`
    - `<script src=".././.././less.js">js not allowed</script>`
    - 遇到`</script>`就结束
* style
    - `<style>css goes here</style>`
    - `<link rel="stylesheet" href="a.css">`
* 多媒体标签
  - video
  - audio
* canvas
    - 画布
    - 必须有结束标签，内部写上不支持canvas的浏览器的提示性文字
        + `<canvas><p>您的浏览器不支持canvas</p></canvas>`
    * width/height 属性与css的width/height是不一样的
        * 如果不同的话图片会被拉伸
    * 默认是透明的
* progress
    * max
    * value
    * 相关文章
      * http://www.zhangxinxu.com/wordpress/2013/02/html5-progress-element-style-control/
      * https://css-tricks.com/html5-progress-element/
+ meta
  * encoding
  * viewport
  * keywords
  * author
  * description
+ link
  * 引入 css
  * 引入 页面的图标
    * favicon.ico