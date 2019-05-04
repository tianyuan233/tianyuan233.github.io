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