### HTML
超文本标记语言（英语：HyperText Markup Language，简称：HTML）是一种用于创建网页的标准标记语言

#### 语义化
> **语义化**是前端开发里面的一个专用术语，其优点在于有助于构架良好的html结构，有利于搜索引擎的建立索引、抓取；另外，亦有利于页面在不同的设备上显示尽可能相同；此外，亦有利于构建清晰的机构，有利于团队的开发、维护。  

一句话总结就是 合适的地方(位置)用合适的标签  
相关链接： https://github.com/zhanyouwei/blog-source/issues/6

-----
#### DOCTYPE
doctype 位于文档第一行，doctype不是html标签，而是一种标准通用标记语言的**文档类型声明**，目的是告诉标准通用标记语言解析器要使用什么样的文档类型定义（DTD）来解析文档。
在html5中的默认格式为
```html
<!DOCTYPE html>
```
----
#### HTML属性
* 每一个标签可以接受一个或多个属性
* 属性可以有值，也可以没有
* 属性名不区分大小写，属性值区分大小写的
* 属性的值一般使用双引号包起来
  * 也可以使用单引号
* 但当属性的值里没有空格，引号等特殊字符时，属性值是**完全可以**不用引号包起来的
* 如下列出一些，通用/全局属性(Global Attributes)，即可以用在所有元素上面且有实际意义
    + id属性
        * 标签在整个页面唯一的值
        * 一般来说起成一个单一的单词，不以数字开头，没有空格
    + name属性，标签的名字，现在主要用在表单类标签上面
    + title属性，鼠标在上面时显示的tooltip文本
    + style属性，用于给标签指定内联样式
    + class="foo bar" 类别
      * 空格分隔的单词列表（foo,bar）
      * 一个标签可以有多个类
    + tabindex
      * 该属性控制 tab键跳转的顺序（位置）
    + data-*
      * **自定义数据属性**。它赋予我们在所有 HTML 元素上嵌入自定义数据属性的能力，并可以通过脚本(一般指JavaScript) 与 HTML 之间进行专有数据的交换。
      * `<div data-isbn="567890">书籍详情</div>`
    + contenteditable
    + contextmenu
      * 需要js的支持
    * 参考文档：[MDN 全局属性](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes)

------
#### HTML Entity
HTML字符实体：一些会被html解析的符号，比如 "<",">"等  
一个HTML Entity都含有2种转义格式：Entity Name 和 Entity Number。表示方法通常为 以 & 开头以 ; 结尾
 - Entity Name
    - \< 表示为 "\&lt;"
    - \> 表示为 "\&gt;"
 - Entity Number

 **常见的HTML字符实体**

| Character|Entity Name	 |
|----------|-------------|
| space	　　| \&nbsp;	    |
|#	　　　　| \&num;	     |
|&	　　　　| \&amp;	     |
|版权符&copy;	| \&copy;	   |
|单引号	　　　　| \&apos;	  |
|双引号　　　　| \&quot;	  |

相关文档：
  * Google： html entity
  * https://dev.w3.org/html5/html-author/charref
-----
#### 对空白字符的忽略
默认情况下浏览器忽略文字与文字之间多于一个的空格，换行符会被全部忽略
> 注： css可以改变这种行为
